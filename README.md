# Jellyfin Automatización

Despliegue automatizado de Jellyfin usando Ansible y Docker 
en dos entornos: AWS (cloud) y local.

## Requisitos previos

- Python 3
- Cuenta AWS con credenciales
- Llave .pem creada en AWS
- Ansible instalado

## Instalación

1. Clona el repositorio
```bash
git clone 
cd jellyfin_automatication
```

2. Crea y activa el entorno virtual
```bash
python3 -m venv venv
source venv/bin/activate
```

3. Instala las dependencias
```bash
pip install -r requirements.txt
```

4. Configura tus credenciales de AWS
```bash
aws configure
```
Ingresa tu AWS Access Key ID y AWS Secret Access Key.
Las credenciales se descargan una sola vez desde la consola de AWS. Guárdalas en un lugar seguro.

5. Coloca tu archivo `.pem` en la raíz del proyecto
El archivo `.pem` nunca debe subirse a GitHub. Ya está incluido en `.gitignore`.

6. Configura `vars.yml` con tus valores
```yaml
region: us-east-1
ami_id: ami-0c02fb55956c7d316
key_name: nombre-de-tu-llave  # sin el .pem
```

## Despliegue cloud (AWS)

```bash
cd playbooks
ansible-playbook creacion_instancia.yml  ->  esto en caso de quererlo hacer en el entorno CLOUD
ansible-playbook jellyfinlocal.yml  ->  esto en caso de querer hacerlo en un entorno LOCAL
```

Al finalizar, Ansible mostrará la IP pública. Abre en tu navegador: http//[ip publica]:8096
O en caso de haberlo hecho localmente simplemente entrar a: localhost:8096
