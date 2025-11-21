[![Agile611](https://www.agile611.com/wp-content/uploads/2020/09/cropped-logo-header.png)](http://www.agile611.com/)

# Agile611 WordPress Ansible (Vagrant)

Plantilla para desplegar un entorno WordPress usando Vagrant y Ansible. Incluye una máquina de control (Ansible), servidor web, base de datos y balanceador de carga, todos definidos en el `Vagrantfile`.

**Objetivo:** facilitar el aprovisionamiento y pruebas locales de una arquitectura WordPress multinodo usando cajas `bento/ubuntu-24.04`.

**Contenido principal**
- **`Vagrantfile`**: definición de las máquinas (ansible, database, loadbalancer, webserver).
- **`ansible.sh`** (si existe): script de aprovisionamiento inicial usado por la máquina `ansible`.
- **Playbooks/roles**: añade tus playbooks de Ansible en una carpeta `ansible/` o similar.

**Requisitos**
- `Vagrant` (>= 2.2.x)
- `VirtualBox` (u otro proveedor soportado por Vagrant)
- Opcional: `ansible` en la máquina host si prefieres ejecutar playbooks desde fuera de la VM

Guía rápida

- Levantar todas las máquinas:

```bash
vagrant up --provider=virtualbox
```

- Levantar una máquina concreta (por ejemplo `webserver`):

```bash
vagrant up webserver
```

- Acceder por SSH a la máquina de control (Ansible):

```bash
vagrant ssh ansible
```

- Desde la máquina `ansible` (o desde tu host si tienes Ansible instalado), ejecuta tus playbooks:

```bash
# desde la VM de control
ansible-playbook -i inventory/hosts site.yml

# o desde host (si está configurado)
ansible-playbook -i inventory/hosts site.yml --private-key=path/to/key
```

Notas y recomendaciones
- Revisa y ajusta las IPs privadas en `Vagrantfile` si entran en conflicto con tu red local.
- Si usas `rsync` para sincronizar carpetas, recuerda que puede requerir `rsync` instalado en la máquina host.
- Mantén `composer.lock` en el repositorio si tu proyecto PHP depende de versiones concretas; `vendor/` normalmente se ignora (está en `.gitignore`).

Estructura sugerida

- `Vagrantfile`
- `ansible/`
  - `inventory/`
  - `playbooks/`
  - `roles/`
- `ansible.sh` (opcional)

Contribuciones
- Abre issues o PRs para sugerir mejoras. Describe cambios y pasos para reproducirlos.

**Licencia**

This tutorial is released into the public domain by [Agile611](http://www.agile611.com/) under Creative Commons Attribution-NonCommercial 4.0 International.

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC_BY--NC_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)


This README file was originally written by [Guillem Hernández Sola](https://www.linkedin.com/in/guillemhs/) and is likewise released into the public domain.

Please contact Agile611 for further details.

* [Agile611](http://www.agile611.com/)
* Laureà Miró 309
* 08950 Esplugues de Llobregat (Barcelona)
