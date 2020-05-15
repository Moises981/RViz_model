# RViz_model

Este proyecto tuvo muchos inconventienes en cuanto al codigo por lo cual se diran los errores primeros para tener en cuenta:

![Captura de pantalla de 2020-05-15 15-03-48](https://user-images.githubusercontent.com/59718261/82102904-a3977000-96d6-11ea-8128-f3925ed65e7d.png)

Este error paso debido a que solo se estaba publicando en el /joint_states los datos de position sin embargo tambien se debe los datos del header name="base_to_arm"(Nombre del joint a publicar), stamp.secs (Tiempo de ROS debido a este el screen nos dice que nuestro mensaje esta x segundos tarde , por lo tanto debemos estar sincronizados con el reloj de ROS , para ello podemos usar ROSCPP crear una instancia de ROS::TIME variable=ROS::TIME:NOW , despues solo llamamos la instancia variable.secs , le sumamos un poco de tiempo para la duracion en mi caso 2sec , lo publicamos en el stamp.secs y ya estara solucionado.

![-home-asus-Escritorio-Probe-catkin_ws-src-quanergy-launch-rviz launch http:--localhost:11311_028](https://user-images.githubusercontent.com/59718261/82102914-ad20d800-96d6-11ea-80c0-ceef5e108ca9.png)

El error en este caso fue haber publicado incorrectamente los mensajes con variables que no pertecen como por ejemplo int32 a position que es una lista de floats.

Para ejecutar y probar el model , primero se debe compilar el catkin_ws , para ello se usa el comando:

