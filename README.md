# Curso de Deploy con Now.sh
Este es el proyecto del curso de deploy con [now.sh](https://now.sh) de Platzi.

El proyecto esta dividido en 2 partes.

## [API](https://github.com/sergiodxa/now-course/tree/master/api)
Es un API GraphQL dentro de un contenedor de Docker. Esta hecha en Node.js y se conecta a una base de datos PostgreSQL externa mediante las variables de entorno que configuramos.

## [BFF](https://github.com/sergiodxa/now-course/tree/master/bff)
El servidor de cara al usuario hecho en Next.js. Consume el API GraphQL mediante queries, mutaciones y suscripciones gracias al cliente de Apollo.

## Now Rules
Para transformar nuestra aplicacion microservicio en monolitica pero usan la base de microservicios, podemos definir reglas en Now, creando el archivo rules.json y agregando el siguiente eschema

```bash
    {
        "rules": [
            {
                "pathname": "/graphql",
                "dest": "[aplicacion].now.sh"
            },
            {
                "pathname": "/[ruta]",
                "dest": "[aplicacion].now.sh"
            },
            {
                "dest": "[aplicacion].now.sh"
            }
        ]
    }
```

y corriendo el siguente comando 

```bash
$ now alias platzi-now.now.sh -r rules.json
```

