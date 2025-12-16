# **MNIST FPGA**


En este repositorio se realizara la implementacion de un red neuronal utilizando el dataset MNIST, el cual posee datos de numeros escritos  con la mano.

El flujo de trabajo es el siguiente

* Creacion de una red neuronal Teacher, en la que se aplicara las tecnicas de Prunning, Quantification

* Del modelo Teacher se creara un modelo Student utilizando un Knownledge Distilation (KD)

* Implementacion del modelo Student a la FPGA utilizando la libreria HLS4ML


Se utiizaran dos tipos de arquitecturas de red neuroanl para el dataset de MNIST. En el archivo *mnist_teach_stu.ipynb* utiliza un red neuronal de MLP(Multilayer Perceptron) y en el archivo *mnist_teach_stu_cnn.ipynb* utilizaremos una CNN(Convulational Neural Network).



## Como utilizar el repositorio


Clona el repositorio 

```sh

git clone https://github.com/pinpacho/mnist_fpga_hls4ml.git
```

Crea un entorno virtual con anaconda, se recomienda usar la version de *python =3.11.9*

```sh

conda create -n mf_env python=3.11.9
conda activate mf_env  
```
Instala las dependecias

```sh
pip install -r requirements.txt
```

## References

[1]  Molina, R. S., Morales, I. R., Crespo, M. L., Costa, V. G., Carrato, S., & Ramponi, G. (2024). An End-to-End Workflow to Efficiently Compress and Deploy DNN Classifiers On SoC/FPGA. IEEE Embedded Systems Letters, 16(3), 255-258.

[2] Fast Machine Learning Lab. (s.f.). Part 6: Convolutional Neural Networks in hls4ml. En hls4ml-tutorial. https://fastmachinelearning.org/hls4ml-tutorial/part6_cnns.html