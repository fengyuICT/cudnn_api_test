# cudnn_api_test
cudnn api document maybe obscure, the target of this project is provide some test cast to figure out how to invoke this API correctly.

API list
## cudnnSetTensorNdDescriptor
Problem descripe:
cudnn provide a document to descripe this function, see the hyperlinks below:
https://docs.nvidia.com/deeplearning/sdk/cudnn-developer-guide/index.html#cudnnSetTensorNdDescriptor
but I can't figure out what sequence of data should feed to the parameters, e.g. input data storage in NHWC, so is we set dimA in [N, H, W, C] or [N, C, H, W]?
test: see cudnnSetTensorNdDescriptor.cu
method main body is copy from https://gist.github.com/odashi/1c20ba90388cf02330e1b95963d78039, we change code for our purpose.
Conclusion: cuDNN requires the strides and dims to be ordered as NCHW no matter what input layout is.
