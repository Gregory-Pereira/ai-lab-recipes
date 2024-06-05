APP := llamacpp_python
PORT ?= 8001
CHAT_FORMAT ?= llama-2

include ../common/Makefile.common

IMAGE_NAME ?= $(REGISTRY_ORG)/$(COMPONENT)/$(APP):latest
IMAGE := $(REGISTRY)/$(IMAGE_NAME)
CUDA_IMAGE := $(REGISTRY)/$(REGISTRY_ORG)/$(COMPONENT)/$(APP)_cuda:latest
VULKAN_IMAGE := $(REGISTRY)/$(REGISTRY_ORG)/$(COMPONENT)/$(APP)_vulkan:latest

MODELS_PATH := /locallm/models
MODEL_NAME ?= granite-7b-lab-Q4_K_M.gguf

LLVM_GIT_REPO ?= https://github.com/llvm/llvm-project.git
LLVM_GIT_BRANCH ?= tags/llvmorg-16.0.0

.Phony: all
all: build download-model-granite run

.PHONY: build-cuda
build-cuda:
	podman build --squash-all -t $(CUDA_IMAGE) . -f cuda/Containerfile

.PHONY: build-vulkan
build-vulkan:
	$(MAKE) llvm-16
	podman build --squash-all -t $(VULKAN_IMAGE) . -f vulkan/Containerfile

.PHONY: download-model-granite # default model
download-model-granite:
	cd ../../models/ && \
	make download-model-granite

.PHONY: llvm-16
llvm-16:
	cd vulkan && \
	git clone $(LLVM_GIT_REPO) llvm 2> /dev/null || true
	(cd llvm; git checkout $(LLVM_GIT_BRANCH))
