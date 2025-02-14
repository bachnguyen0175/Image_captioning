<h1>Image Captioning using Seq2seq model with attention</h1>
<div align="center" dir="auto">
<a href="https://pytorch.org/get-started/locally/" rel="nofollow"><img src="https://camo.githubusercontent.com/0add0c0b6ec6267b61016063796469feb03cc17c93d9f04201e25d0f12651de0/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5059544f5243482d312e31302b2d7265643f7374796c653d666f722d7468652d6261646765266c6f676f3d7079746f726368" alt="PyTorch - Version" data-canonical-src="https://img.shields.io/badge/PYTORCH-1.10+-red?style=for-the-badge&amp;logo=pytorch" style="max-width: 100%;"></a>
<a href="https://www.python.org/downloads/" rel="nofollow"><img src="https://camo.githubusercontent.com/c2623d41ae89703a8d56dab2e458028b95b87d8ce1897ff29930ef267e9e77e0/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f505954484f4e2d332e372b2d7265643f7374796c653d666f722d7468652d6261646765266c6f676f3d707974686f6e266c6f676f436f6c6f723d7768697465" alt="Python - Version" data-canonical-src="https://img.shields.io/badge/PYTHON-3.7+-red?style=for-the-badge&amp;logo=python&amp;logoColor=white" style="max-width: 100%;"></a>
<br></p>
</div>

<details open="">
  <summary>Table of Contents</summary>
  <ol dir="auto">
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#project-structure">Project Structure</a>
    </li>
    <li>
      <a href="#data-preparation">Data Preparation</a>
    </li>
    <li><a href="#custom-dataset">How to run repository</a></li>
    <li><a href="#colab">Try with google colab</a></li>
    <li><a href="#conclusion">Conclusion</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>

<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#about-the-project">About The Project<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>
<p dir="auto">In this project we will build model for Image captioning. The target of project is from the image, we can describe the image with short script. The model we use in this project is Seq2seq with Attention</p>
<h4>The project test on python version 3.10.12</h4>
<h4>Result we want to show</h4>
<img width="100%" src="https://github.com/LuongTuanAnh163002/Image_captioning/blob/main/image/captioning.jpg" style="max-width: 100%;">

<h4>Seq2seq model with RNN</h4>
<img width="100%" src="https://github.com/LuongTuanAnh163002/Image_captioning/blob/main/image/seq2seq.jpg" style="max-width: 100%;">

<h4>Attention</h4>
<img width="100%" src="https://github.com/LuongTuanAnh163002/Image_captioning/blob/main/image/attention.png" style="max-width: 100%;">

<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#project-structure">Project Structure<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>
<div class="highlight highlight-source-shell notranslate position-relative overflow-auto" dir="auto">
  <pre>Image_captioning
  │   train.py                      <span class="pl-c"><span class="pl-c">#</span> Train script</span>
  │   detect.py                     <span class="pl-c"><span class="pl-c">#</span> Detect script inference</span>
  
  ├───models
  │       model.py               <span class="pl-c"><span class="pl-c">#</span>Define Seq2seq model structure</span>
  │
  ├───data
  │       Flicks.yaml              <span class="pl-c"><span class="pl-c">#</span>Config data Flicks.yaml</span>
  │
  └───utils
      │   datasets.py               <span class="pl-c"><span class="pl-c">#</span>Processing datasets</span>
      │   general.py               <span class="pl-c"><span class="pl-c">#</span> Various helper functions</span>
  </pre>

</div>

<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#data-preparation">Data Preparation<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>
<p>You can dowload dataset here or through script in next part</p>
<a href="https://drive.google.com/file/d/1P-32Vfy3-s8gaAxbLqTbjLAWlKDGzbTy/view?usp=sharing"><code>flickr8k.zip</code></a>
<pre>Flickr8k
└───datasets
    ├───Images
      ├───file_name.jpg
      ├───..............       
    ├───captions.txt
</pre>

<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#custom-dataset">How to run repository<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>
  <h3>1.For training</h3>
  <p>+Step1: Install virtual environment, package</p>
  <pre>
  conda create --name image_caption python=3.10.12
  git clone https://github.com/bachnguyen0175/Image_captioning.git
  cd Image_captioning
  conda activate image_caption
  pip install -r requirements.txt
  </pre>
  <p>+Step2: Dowload dataset</p>
  <pre>
  #for ubuntu/linux
  pip install gdown
  gdown "1P-32Vfy3-s8gaAxbLqTbjLAWlKDGzbTy&confirm=t"
  d="./flickr8k/"
  mkdir -p $d
  unzip -q flickr8k.zip -d $d
  rm flickr8k.zip
  \
  #for window
  pip install gdown
  gdown "1P-32Vfy3-s8gaAxbLqTbjLAWlKDGzbTy&confirm=t"
  tar -xf flickr8k.zip
  del flickr8k.zip
  </pre>
  <p>+Step3: Go to "data" folder then modify path of dataset to your path dataset</p>
  <p>+Step4: Run the command below to training for pretrain</p>
  <pre>python train.py --data data/Flicks.yaml --epochs 25 --batch_size 256 --device 0</pre>
  <p>After you run and done training, all results save in runs/train/exp/..., folder runs automatic create after training done</p>

  <h3>2.For detect with your model</h3>
  <pre>python detect.py --source file_name.jpg --weight runs/train/exp</pre>

  <h3>3.For detect with my model</h3>
  <p>+Step1: Dowload my model with script below or you can dowload here</p>
  <a href="https://drive.google.com/file/d/15awWEiar47LKqHn9D4A5B_keWuxZlGTM/view?usp=sharing"><code>weight.zip</code></a>
  <pre>
  #for ubuntu/linux
  curl -L -o weight_image_captioning.zip https://github.com/bachnguyen0175/Image_captioning/releases/download/v1.0.0/weight_image_captioning.zip
  d="./weight_img_caption/"
  mkdir -p $d
  unzip -q weight_image_captioning.zip -d $d
  rm weight_image_captioning.zip
  \
  #for window
  pip install gdown
  gdown 15awWEiar47LKqHn9D4A5B_keWuxZlGTM
  tar -xf weight_image_captioning.zip
  del weight_image_captioning.zip
  </pre>
  <p>+Step2: Dowload image example</p>
  <pre>curl -L -o test_predict.jpg 'https://drive.google.com/uc?id=1PWU1tw53Rv3J-T9i0OQBGFKLbMF4rg9J&confirm=t'</pre>
  <p>+Step3: Detect</p>
  <pre>python detect.py --source test_predict.jpg --weight weight_img_caption/exp</pre>
  
<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#colab">Try with google colab<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>
<h3>1.For training and detect in Flickr8k dataset</h3>
<a href="https://colab.research.google.com/drive/15hfvnPsYac8ydxG_mmHjZAxW2Z2DOM7o?usp=sharing" rel="nofollow"><img src="https://camo.githubusercontent.com/f5e0d0538a9c2972b5d413e0ace04cecd8efd828d133133933dfffec282a4e1b/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667" alt="Open In Colab" data-canonical-src="https://colab.research.google.com/assets/colab-badge.svg" style="max-width: 100%;"></a>

<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#conclusion">Conclusion<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>

<p>We build complete image captioning project but we have some disadvantage:</p>
<p>Disadvantage</p>
<ul dir="auto">
<li>We meet some problem when training with CPU, so that if you running project without no GPU, you meet some error, we will fix this bug in near future</li>
<li>Cannot train with multiple GPUs for acceleration</li>
<li>Only jpg files images are supported during training, in the future we will improve to support more file types images.</li>
<li>Haven't exported model to onnx or tensorRT yet. In the near future we will update the conversion code for onnx and tensorRT.</li>
<li>Model only experiment in English language, in the future we will experiment in other language, especials Vienamese language</li>
<li>Not metric to evaluate, we are building some code to evaluate model base BLEU score metric and will update in near future</li>
</ul>
<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#license">License<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>
<p dir="auto">See <code>LICENSE</code> for more information.</p>

<h2 tabindex="-1" id="user-content-about-the-project" dir="auto"><a class="heading-link" href="#acknowledgements">Acknowledgements<svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></h2>

<ul dir="auto">
<p>Our work will not be complete without the wonderful work of the following authors:</p>
<li><a href="https://github.com/WongKinYiu/yolov7.git">Yolov7</a></li>
<li><a href="https://viblo.asia/p/attention-trong-seq2seq-model-m68Z0J4z5kG">seq2seq-with-attention</a></li>
