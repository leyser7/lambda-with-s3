# lambda-with-s3
Este archivo CloudFormation se utiliza para desplegar automáticamente una función Lambda y un grupo de logs de CloudWatch con nombres personalizados basados en los parámetros proporcionados. Esto puede ser útil para desplegar rápidamente funciones Lambda para diferentes proyectos o usuarios sin tener que crear y configurar manualmente cada recurso.

Este archivo CloudFormation realiza las siguientes acciones:

Define dos parámetros: projectName y userName. Estos parámetros se pueden proporcionar al crear o actualizar el stack de CloudFormation y se utilizan para personalizar los nombres de los recursos creados.

Crea una función Lambda llamada MyLambdaFunction. La función Lambda se configura con el manejador app.lambda_handler y se ejecuta en el entorno de tiempo de ejecución python3.10. El código de la función simplemente imprime 'Hello World'. El nombre de la función se establece en el valor de projectName seguido de userName. Por ejemplo, si projectName es myProject y userName es myUser, el nombre de la función sería myProject-myUser.

Crea un rol IAM llamado LambdaExecutionRole que la función Lambda asume para obtener los permisos necesarios. Este rol no se muestra en el fragmento de código proporcionado, pero se hace referencia a él en la función Lambda.

Crea un grupo de logs de CloudWatch llamado MyLogGroup. El nombre del grupo de logs se establece en /aws/lambda/ seguido del valor de userName. Por ejemplo, si userName es myUser, el nombre del grupo de logs sería /aws/lambda/myUser. Los logs en este grupo se retienen durante 7 días.
