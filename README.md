# RViz_model
Este proyecto tuvo muchos inconventienes en cuanto al codigo por lo cual se diran los errores primeros para tener en cuenta:

![Captura de pantalla de 2020-05-15 15-03-48](https://user-images.githubusercontent.com/59718261/82102904-a3977000-96d6-11ea-8128-f3925ed65e7d.png)

Este error paso debido a que solo se estaba publicando en el /joint_states los datos de position sin embargo tambien se debe los datos del header name="base_to_arm"(Nombre del joint a publicar), stamp.secs (Tiempo de ROS debido a este el screen nos dice que nuestro mensaje esta x segundos tarde , por lo tanto debemos estar sincronizados con el reloj de ROS , para ello podemos usar ROSCPP crear una instancia de ROS::TIME variable=ROS::TIME:NOW , despues solo llamamos la instancia variable.secs , le sumamos un poco de tiempo para la duracion en mi caso 2sec , lo publicamos en el stamp.secs y ya estara solucionado.

![-home-asus-Escritorio-Probe-catkin_ws-src-quanergy-launch-rviz launch http:--localhost:11311_028](https://user-images.githubusercontent.com/59718261/82102914-ad20d800-96d6-11ea-80c0-ceef5e108ca9.png)

El error en este caso fue haber publicado incorrectamente los mensajes con variables que no pertecen como por ejemplo int32 a position que es una lista de floats.

Primero subir el skecth al arduino.

![image](https://user-images.githubusercontent.com/59718261/82105158-6edbe680-96df-11ea-8710-5b1323061a68.png)

Para ejecutar y probar el model , primero se debe compilar la carpeta catkin_ws , para ello se usa el comando:

```bash
catkin_make
```
![asus@asus-ROG-Strix-G531GT-G531GT: ~-Escritorio-RViz_model-catkin_ws_033](https://user-images.githubusercontent.com/59718261/82104282-e1e35e00-96db-11ea-8684-1c4688dec952.png)

```bash
source devel/setup.bash
```
Despues ingresar lo siguiente al terminal.

```bash
roslaunch rviz_visual rviz.launch
```
![Peek 15-05-2020 19-02](https://user-images.githubusercontent.com/59718261/82105021-dc3b4780-96de-11ea-8026-55dc9ed63b23.gif)




