### 设置TensorRT
```
OrtTensorRTProviderOptionsV2* options;
std::ignore = Ort::GetApi().CreateTensorRTProviderOptions(&options);
std::unique_ptr<OrtTensorRTProviderOptionsV2, decltype(Ort::GetApi().ReleaseTensorRTProviderOptions)> rel_options(
    options, Ort::GetApi().ReleaseTensorRTProviderOptions);
session_options_.AppendExecutionProvider_TensorRT_V2(*options);
```

### 设置CUDA
```
OrtCUDAProviderOptionsV2* options;
std::ignore = Ort::GetApi().CreateCUDAProviderOptions(&options);
std::unique_ptr<OrtCUDAProviderOptionsV2, decltype(Ort::GetApi().ReleaseCUDAProviderOptions)> rel_options(
    options, Ort::GetApi().ReleaseCUDAProviderOptions);
session_options_.AppendExecutionProvider_CUDA_V2(*options);
```
