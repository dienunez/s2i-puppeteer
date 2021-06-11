#### s2i de puppeteer para utilizar en el PaaS.

VERIFICAR QUE .s2i/bin/assemble comience con #!/bin/bash en lugar de #!/bin/sh

Podemos buildear el container con el dockerfile de este repo:

```bash
docker build -t puppeteer .
```

```bash
s2i build [file:///path-a-tu-app](file:///path-a-tu aplicacion) puppeteer:latest puppeteers2i
```

```bash
docker run -i puppeteers2i:latest
```


O para usarla desde ocp:

 

```bash
oc new-app dienun/ocppuppet~https://repogit.com --name puppeteer oc expose svc/puppeteer
```

```bash
oc start-build dc/puppeteer --from-dir=. -n {NAMESPACE}
```



El archivo server.js contiene un script que instancia un headless browser y captura la pantalla de una visita a una url para una POC de chrome-puppeteer dockerizado version s2i
