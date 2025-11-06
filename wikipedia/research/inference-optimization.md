# Inference optimization

## OpenVino

Export <https://huggingface.co/docs/optimum/main/en/intel/openvino/export>
GPU - Need <https://dgpu-docs.intel.com/driver/client/overview.html>

And then verify `clinfo | grep "Device Name"`

More openvino models <https://huggingface.co/echarlaix>
<https://huggingface.co/models?library=openvino>

### Intel initiatives

* https://github.com/intel/intel-ai-assistant-builder

## Papers

- Taming the Titans: A Survey of Efficient LLM Inference Serving: <https://arxiv.org/pdf/2504.19720>

# Candle GGUF decoding example

<https://gist.github.com/CoffeeVampir3/b66ee4e9695e7daae4f328edb599c1d3>
