# Transformer-13

clear all
close all
clc
GENERAR Y REPRESENTAR ESPECTROS
#Numero de muestras
N=20;
#Rango
n=0:N-1;
#Valor de K
k=n;
senalA2X4=2*cos(2*pi*0.1*n+(pi/4))
transA2X4=fft(senalA2X4);
#Reprensentamos la señal
figure('name','Transformadas X4.','NumberTitle','off');
subplot(311);
stem(n,senalA2X4, "markerfacecolor", [1 0 1]);
title ("Señal X4=2*cos(2*pi*0.1*n+(pi/4))");
#Representamos el modulo de la transformada en k
subplot(312);
stem(k,abs(transA2X4), "markerfacecolor", [1 0 1]);
title ("Modulo Transformada en k");
#Representamos el modulo de la transformada en k/N
subplot(313);
stem(k/N,abs(transA2X4), "markerfacecolor", [1 0 1]);
title ("Modulo Transformada en k/N");

CARGAR UNA IMAGEN
im = imread('globo.jpg');
MOSTRAR UNA IMAGEN
figure(1)
imshow(im);
HACER EL CAST A DOUBLE
imd=double(im);
GUARDARLA
imwrite(unit8(imd), 'prueba.jpg');
CARGAR IMAGEN
im = imread('manzanas.jpg')
VER TAMAÑO
size(im)
canal1=im(:;:;1);CANAL ROJO
OTRAVEZ HASTA GUARDARLA

INVERTIR UNA IMAGEN
im_inv=255-imd;
figure(2)
HACER CAST Y GUARDARLA

CREAR HISTOGRAMA
subplot(121);
imshow(im);ç
subplot(122);
h=imhist(im)
HISTOGRAMA CANAL ROJOO
imhist(im(:;:;1)
CAMBIAR DE COLOR A BLANCO Y NEGRO
imBN = rgb2gray(imd);
imshow(unit8(imBN));
HISTOGRAMA A COLOR
h = hlshistogramRed(im)

BINARIZACION
pkg load image
im=imread('objetos.jpg'); %con objetos, huevos y huella se puede hacer al ser bimonial
subplot(141);
imshow(im);
subplot(142);
h=imhist(im); %no pasamos a double porque imhist trabaja con uint8
imhist(im);
T=135;
out=(im>=T)*255;
subplot(143);
imshow(uint8(out));
subplot(144);
imhist(uint8(out)); %no pasamos a double porque imhist trabaja con uint8

APLICAR FILTROS
pkg load image
im=imread('farola.jpg');
imshow(im);
esp=fftshift(fft2(im));
ShowFft(esp,1);
[n m]=size(im);
#Filtro paso baja ideal
#h=filtro(n,m,10,0,1);
#Filtro paso baja Butterworth
#h=filtro(n,m,10,0,0);
#Filtro paso alta ideal
h=filtro(n,m,10,1,1);
#Filtro paso alta Butterworth
#h=filtro(n,m,10,1,0);
espOut=esp.*h;
out=abs(ifft2(espOut));
imshow(uint8(out));

