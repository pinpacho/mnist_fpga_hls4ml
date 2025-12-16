# MNIST FPGA 

Este repositorio presenta el desarrollo y la compresión de modelos de redes neuronales artificiales para su posterior implementación en plataformas FPGA, utilizando el conjunto de datos **MNIST**, el cual contiene imágenes de dígitos manuscritos (0–9).

El trabajo se enmarca en un flujo de **compresión de modelos de aprendizaje profundo**, combinando técnicas de *pruning*, *quantization* y *knowledge distillation*, con el objetivo de obtener modelos eficientes en términos de memoria y cómputo, adecuados para hardware reconfigurable.

---

## Flujo de trabajo

El flujo de trabajo implementado en este repositorio es el siguiente:

* **Entrenamiento de un modelo Teacher**
  Se entrena un modelo base de mayor capacidad en precisión completa, que actúa como referencia de desempeño.

* **Compresión del modelo Teacher**
  Al modelo Teacher se le aplican técnicas de:

  * *Pruning* (eliminación de pesos poco relevantes)
  * *Quantization* y *Quantization-Aware Training (QAT)*

* **Entrenamiento del modelo Student**
  A partir del modelo Teacher optimizado, se entrena un modelo Student más compacto mediante la técnica de *Knowledge Distillation (KD)*, transfiriendo el conocimiento del modelo maestro.

* **Preparación para implementación en FPGA**
  El modelo Student está diseñado para ser compatible con herramientas de síntesis de alto nivel, específicamente la librería **hls4ml**, para su futura implementación en FPGA.

---

## Arquitecturas implementadas

Se utilizan dos tipos de arquitecturas de redes neuronales para el conjunto de datos MNIST:

* **MLP (Multilayer Perceptron)**
  Implementada en el archivo:

  * `mnist_teach_stu.ipynb`

* **CNN (Convolutional Neural Network)**
  Implementada en el archivo:

  * `mnist_teach_stu_cnn.ipynb`

En ambos casos se sigue el esquema **Teacher–Student**, comparando el desempeño antes y después de la compresión.

---

## Requisitos y uso del repositorio

### Clonar el repositorio

```sh
git clone https://github.com/pinpacho/mnist_fpga_hls4ml.git
cd mnist_fpga_hls4ml
```

### Crear entorno virtual

Se recomienda utilizar **Anaconda** con Python versión **3.11.9**:

```sh
conda create -n mf_env python=3.11.9
conda activate mf_env
```

### Instalar dependencias

```sh
pip install -r requirements.txt
```

Una vez configurado el entorno, se pueden ejecutar los notebooks para entrenar los modelos Teacher y Student, aplicar las técnicas de compresión y evaluar los resultados.

---


## Referencias

* **Molina, R., Morales Argueta, I., Crespo, M., Costa, V., Carrato, S., & Ramponi, G.** (2023).
  *An end-to-end workflow to efficiently compress and deploy DNN classifiers on SoC/FPGA*.
  IEEE Embedded Systems Letters.
  [https://doi.org/10.1109/LES.2023.3343030](https://doi.org/10.1109/LES.2023.3343030)

* **Hu, C., Li, X., Liu, D., Wu, H., Chen, X., Wang, J., & Liu, X.** (2023).
  *Teacher–student architecture for knowledge distillation: A survey*.
  arXiv.
  [https://arxiv.org/abs/2308.04268](https://arxiv.org/abs/2308.04268)

* **TensorFlow Authors.** (2024).
  *Trim insignificant weights — Pruning guide*.
  TensorFlow.
  [https://www.tensorflow.org/model_optimization/guide/pruning](https://www.tensorflow.org/model_optimization/guide/pruning)

* **TensorFlow Authors.** (2024).
  *Quantization aware training*.
  TensorFlow Model Optimization Guide.
  [https://www.tensorflow.org/model_optimization/guide/quantization/training](https://www.tensorflow.org/model_optimization/guide/quantization/training)

* **ICTP Machine Learning Lab.** (2024).
  *Part 1: GN discrimination with hls4ml* (Lab 5, Jupyter notebook).
  [https://gitlab.com/ictp-mlab/smr-4078/-/blob/main/Labs/Lab5_HLS4ML/part_1/Part-1-GN-discrimination.ipynb](https://gitlab.com/ictp-mlab/smr-4078/-/blob/main/Labs/Lab5_HLS4ML/part_1/Part-1-GN-discrimination.ipynb)

* **Gou, J., Yu, B., Maybank, S. J., & Tao, D.** (2021).
  *Knowledge distillation: A survey*.
  International Journal of Computer Vision, 129(6), 1789–1819.
  [https://doi.org/10.1007/s11263-021-01453-z](https://doi.org/10.1007/s11263-021-01453-z)

* **Aarrestad, T., Loncar, V., Ghielmetti, N., Pierini, M., Summers, S., Ngadiuba, J., Petersson, C., Linander, H., Iiyama, Y., Di Guglielmo, G., Duarte, J., Harris, P., Rankin, D., Jindariani, S., Pedro, K., Tran, N., Liu, M., Kreinar, E., Wu, Z., & Hoang, D.** (2021).
  *Fast convolutional neural networks on FPGAs with hls4ml*.
  Machine Learning: Science and Technology, 2(4), 045015.
  [https://doi.org/10.1088/2632-2153/ac0ea1](https://doi.org/10.1088/2632-2153/ac0ea1)

