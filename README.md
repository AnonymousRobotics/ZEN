# ZEN: Efficient Zero-Knowledge Proof for Neural Networks

# Rust version
We test the code using `rustc 1.47.0` for `zk-ml-private-model`, `zk-ml-accuracy`, `zk-ml-private-model-baseline`.
Make sure that you sue  `rustc 1.47.0` by executing `rustup override set 1.47.0`
For the newer version implementation of ZEN in `zen-arkworks` and `zen-accuracy-arkworks`, please use `rustup override set 1.51.0` before `cargo build`.

# Prepare Data
* Under directory `ZEN/zk-ml-private-model-baseline/`, run `mkdir test-data` and `cargo run --bin gen_data` to generate the mock inputs for baseline and microbenchmark purposes only. For optimization level 3, we load real quantization parameters generated from `ZEN/numpyInferenceEngine/XXNet/`. For example, cd to `ZEN/numpyInferenceEngine/LeNet_CIFAR10` and run `python3.8 LeNet_end_to_end_quant.py --model LeNet_Small`. The generated quantized parameters are located at `ZEN/numpyInferenceEngine/LeNet_CIFAR10/LeNet_CIFAR_pretrained/`. For easily reproducing the results, we have saved a copy of parameters for all combinations of model and dataset in director `ZEN/zk-ml-private-model/pretrained_model/`


# Microbenchmarks for each NN layer(under `zk-ml-microbench` directory)

## Conv and FC layers different levels of optimization
* `cargo run --bin microbench_conv_layered_optimization_by_kernel_size --release 2>/dev/null`
* `cargo run --bin microbench_fc_layered_optimization --release 2>/dev/null`

## SIMD (stranded encoding) under different batch size
* `cargo run --bin microbench_SIMD_by_batch_size --release 2>/dev/null`

## LeNet Small on CIFAR dataset different levels of optimization 
* `cargo run --bin microbench_lenet_small_cifar_naive --release 2>/dev/null` 
* `cargo run --bin microbench_lenet_small_cifar_op1 --release 2>/dev/null` 
* `cargo run --bin microbench_lenet_small_cifar_op2 --release 2>/dev/null` 
* `cargo run --bin microbench_lenet_small_cifar_op3 --release 2>/dev/null` 
* 
# Baseline(under `zk-ml-private-model-baseline` directory)
## Naive/baseline for all combinations of models and datasets(only calculate the number of constraints)
* `cargo run --bin shallownet_naive_mnist --release 2>/dev/null`
* `cargo run --bin lenet_small_naive_pedersen_cifar --release 2>/dev/null`
* `cargo run --bin lenet_medium_naive_pedersen_cifar --release 2>/dev/null`
* `cargo run --bin lenet_small_naive_pedersen_face --release 2>/dev/null`
* `cargo run --bin lenet_medium_naive_pedersen_face --release 2>/dev/null`
* `cargo run --bin lenet_large_naive_pedersen_face --release 2>/dev/null`
  




# Under `zen-arkworks` directory
## Optmization level 3 for all combinations of models and datasets


* `cargo run --example shallownet_poseidon --release > shallownet.log`
* `cargo run --example lenet_small_cifar_poseidon --release > lenet_small_cifar.log`
* `cargo run --example lenet_medium_cifar_poseidon --release > lenet_medium_cifar.log`
* `cargo run --example lenet_small_face_poseidon --release > lenet_small_face.log`
* `cargo run --example lenet_medium_face_poseidon --release > lenet_medium_face.log`
* `cargo run --example lenet_large_face_poseidon --release > lenet_large_face.log`
# Under `zen-accuracy-arkworks` directory
## Optmization level 3 for all combinations of models and datasets
* `cargo run --bin shallownet_accuracy --release 2>/dev/null`
* `cargo run --bin lenet_small_cifar_accuracy --release 2>/dev/null`
* `cargo run --bin lenet_medium_cifar_accuracy --release 2>/dev/null`
* `cargo run --bin lenet_small_face_accuracy --release 2>/dev/null`
* `cargo run --bin lenet_medium_face_accuracy --release 2>/dev/null`
* `cargo run --bin lenet_large_face_accuracy --release 2>/dev/null`





