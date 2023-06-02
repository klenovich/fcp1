make
python3 -m pip install torch numpy transformers accelerate
python3 convert-hf-to-ggml.py bigscience/bloomz-7b1 ./models 
./quantize ./models/ggml-model-bloomz-7b1-f16.bin ./models/ggml-model-bloomz-7b1-f16-q4_0.bin 2
./main -m ./models/ggml-model-bloomz-7b1-f16-q4_0.bin -t 8 -n 128