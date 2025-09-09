```
struct DeviceResult {
  uint64_t solution_index;
  float score;
  int lock;
};

// 互斥锁
__device__ void CompareAndSet(DeviceResult* ori, DeviceResult* value) {
  if (ori->score <= value->score) {
    return;
  }
  int* lock = &ori->lock;
  // spin lock
  bool blocked = true;
  while (blocked) {
    if (0 == atomicCAS(lock, 0, 1)) {
      if (value->score < ori->score) {
        ori->score = value->score;
        ori->solution_index = value->solution_index;
      }
      // 必须加，防止指令乱序
      __threadfence();
      atomicExch(lock, 0);
      blocked = false;
    }
  }
}
```
