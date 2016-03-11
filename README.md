# obj-tracking

Для обнаружения движущихся объектов применяется следующий алгоритм.

В памяти хранится последние 11 кадров записаных с камеры.
Каждый кадр обрабатывается и сравнивается с предыдущим. Сравнение происходит следующим образом:

1. Кадры переводятся в ч\б диапазон.
![gray](data/frames/893-1-gray.jpg)
1. Для простого устранения шумов, применяется размытие.
![blure](data/frames/893-2-blure.jpg)
1. Из текущего (размытого) кадра вычитается предыдущий.
![delta](data/frames/893-3-delta.jpg)
1. Повышается контраст разницы кадров.
![thresh](data/frames/893-4-thresh.jpg)
1. Над контрастом разницы кадров, применяется смазывание границ, что бы близкостоящие области слились в одну.
![dil](data/frames/893-5-dil.jpg)
1. На результирующем кадре производиться поиск контуров.
![countours](data/frames/893-6-countours.jpg)

Каждый найденый контур сравнивается с гистограммой изображения цели:
![target](data/target.png)
![hist](data/hist.png)

Сравнение осуществляется выражением:
![formula 1](http://docs.opencv.org/2.4/_images/math/a97f7b5144b192bd40b04c165665c9eb1f5cceef.png)
где
![formula 2](http://docs.opencv.org/2.4/_images/math/438152c292378fc2e75dfa048289aaefe29756d2.png)


##Результат

[![youtube video](http://img.youtube.com/vi/6gwxjfIyjEE/0.jpg)](http://www.youtube.com/watch?v=6gwxjfIyjEE)
