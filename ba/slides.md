# Künstliche neuronale Netze <br> & <br> Conv-Nets

---

## Intro

1. Künstliche neuronale Netze
    1. Geschichte
    1. Neuron
    1. Mehrschichtige neuronale Netze/Deep Learning
    1. Lernen
2. Convolutional Neural Networks
    1. Geschichte
    1. Kernel
    1. Convolution
    1. Aufbau eines CNN
3. Meine BA
    1. SqueezeNet - Warum ist das cool?
    1. Autos!
    1. Warum sind die anderen Lösungen doof?
    1. Mein Ansatz

---

## KNN

<ul>
    <li class="fragment">Modellieren __nicht__ das Gehirn</li>
    <li class="fragment">Approximieren Funktionen</li>
    <li class="fragment">Nur inspiriert von natürlichen NN</li>
    <li class="fragment">Bestehen aus *Schichten von Neuronen*</li>
</ul>

Note:
- Wenig Zeit, viel Inhalt, deshalb erspare ich euch die Geschichtsstunde...

---

<img src="fig/ann-schema/ann-schema.png">

Note:
- Eingangsvektor y
- Ausgangsvektor x
- Können mehr Schichten haben, bei DEEP LEARNING haben sie viele Schichten
- Gewichte sind "Konfiguration" von ANNs
- Sind in echt meist größer
- Topologie variiert stark je nach Aufgabe

---

## KNN - Approximation von Funktionen

<span class="fragment">Gesucht: $y = f^*(x)$</span>

<span class="fragment">
Gefunden: $y \approx f(x,\theta) $ <span class="fragment">$:= f^3(f^2(f^1(x,\theta_1),\theta_2),\theta_3)$</span>
</span>

<span class="fragment">$f^k = k$-te Schicht</span>

<span class="fragment">Lernen: $\theta$ finden</span>

Note:
- Wir suchen eine Funktion


---

## KNN - Neuron

<ul>
    <li>Auch "Einheit" oder "Unit"</li>
    <li>Hat vage etwas mit natürlichen Neuronen zu tun</li>
    <li>Linearer Klassifizierer</li>
</ul>

---

## KNN - Neuron

<small class="pull-right">[Russel & Norvig, 2012]</small>
<img src="fig/neuron-mathematical.png">

<span class="fragment">$ a\_j = g(\sum w\_{i,j} a\_i) $</span>

Note:
- "Mathematische" Ansicht eines Neuron

---

## KNN - Lernen

- Finden einer Konfiguration $\theta$
- $\theta$ wird zufällig mit niedrigen Werten initialisiert
- Entscheiden was ein KNN kann
- $g$ muss differenzierbar sein
- Gradient Descent
- Backpropagation Algorithmus

---

## KNN - Lernen

<span class="fragment" data-fragment-index="1">Supervised Learning</span>
<span class="fragment" style="position: absolute;margin-left:5px;font-size:50%;vertical-align:top;" data-fragment-index="4"> 🔴 YOU ARE HERE</span>

<span class="fragment" data-fragment-index="2">Unsupervised Learning</span>

<span class="fragment" data-fragment-index="3">Reinforcement Learning</span>

---

## KNN - Deep Learning

- KNN mit vielen Schichten <!-- .element: class="fragment" -->
- Overfitting! <!-- .element: class="fragment" -->

---

## Convolutional Neural Networks

- Merkmale in Bilder erkennen seit 1990*
- Katzen
- Grober Aufbau: Layerarten und Aufbau eines CNN
- Feiner Aufbau: Kernel und wie sie funktionieren

Note:
Warum? -> Würde man ein FC dafuer nehmen waere die Anzahl an Parametern imens, unmöglich zu lernen

---

<video data-autoplay loop data-src="video/lecun_90.mp4"></video>
<br>
<small>[LeCun et al., 1993; http://youtu.be/FwFduRA_L6Q, 2017]</small>

Note:
- Video von LeCun der zeigt wie ein CNN Zahlen erkennt
- Demo von Arbeit von drei Jahren zuvor

---

<iframe data-src="http://cs231n.stanford.edu" frameborder="0" width="1000" height="360"></iframe>
<br>
<small>[http://cs231n.stanford.edu, 2017]</small>

Note:
- Jetzt kann man sowas im Browser machen
- Andrej Karpathy

___

<img src="video/cnn-in-browser.gif">
<br>
<small>[http://cs231n.stanford.edu, 2017]</small>

---

## CNN

- "Gitterartige" Inhalte
- Verwendet Convolution

Note:
Gitterartig, also nicht zwangsläufig Bilder

Convolution ist der Trick: Dadurch spart man eine Menge Parameter ein

---

## CNN

- Bestehen ebenfalls aus *Schichten*
- Arten von Schichten sind:
    - Input
    - Convolution
    - Activation
    - Pooling
    - Fully-Connected
    - Output

Note:
__Input:__ Eingabeschicht, beinhaltet Eingabe

__Convolution:__ Arbeiter des CNN, hier werden __Merkmale__ erkannt

__Activation:__ Beinhaletet Aktivierungen aus Conv-Layer

__Pooling:__ Verkleinert Eingabe/Datenmenge

__Fully-Connected:__ Neuronales Netz, jedes Neuron mit jedem Pixel in Eingabe verbunden

__Output:__ Ausgabe des CNN, analog zu KNN. Manchmal __Fully-Connected__

---

## CNN

<img src="fig/convnet-overview.jpeg" alt="">
<br>
<small>[http://cs231n.github.io/convolutional-networks/, 2017]</small>

---

## Convolution

- Kernel

---

## Pooling

<img src="fig/pool.jpeg">
<br>
<small>[http://cs231n.github.io/convolutional-networks/, 2017]</small>

Note:
- Pooling um Bilder zu verkleinern
- Aber auch um System robuster zu machen
- Auf dem Bild: __stride=2__
- Also eine Halbierung der Maße

---

## Max-Pooling

<img src="fig/maxpool.jpeg">
<br>
<small>[http://cs231n.github.io/convolutional-networks/, 2017]</small>

Note:
- Früher Avg-Pooling
- Heute weiß man das max pooling besser ist

---

## AlexNet

<small>Krizhevsky et al., 2012</small>

- Erstes CNN das die ILSVRC gewinnt (2012)
- X Gewichte (auch Parameter genannt)
- X Conv-Layer, insgesamt X Kernel
- CNN haben Genauigkeit bei Merkmalserkennung extrem weit nach oben gedrückt
- Gilt als Auslöser des heutigen Deep Learning Booms

---

## SqueezeNet

<small>Iandola et al., 2016</small>

- "Kleines AlexNet"
- X Parameter
- X Conv-Layer, insgesamt X Kernel
- Gleiche Genauigkeit wie AlexNet
- Fire-Modul

Note:
Kleines AlexNet weil sie sich damit verglichen 

Eine Menge revolutionäre Architekturen ausgelassen: ResNet, LeNet, etc.

---

## Fire-Module

<img src="fig/fire-module.png">

Note:
__Module:__ Pakete von Schichten, sozusagen Kompositlayer

__Hyperparameter:__ "Konfiguration" eines Moduls, in diesem Fall z.B. Anzahl von 1x1 und 3x3 Filtern