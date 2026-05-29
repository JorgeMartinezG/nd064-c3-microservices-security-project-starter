# syntax=docker/dockerfile:1.0-experimental

# define base image
FROM opensuse/leap:latest

# define maintainer 
LABEL maintainer="nick.reva@snap.com"
LABEL version="V1"

# Crear grupo y usuario seguro dentro del contenedor
RUN groupadd -r udacity_group && useradd -r -g udacity_group -d /udacity -m -s /sbin/nologin udacity_user

# Crear el directorio de trabajo y darle los permisos al nuevo usuario
RUN mkdir /udacity && chown -R udacity_user:udacity_group /udacity

WORKDIR /udacity

# Instalar actualizaciones y limpiar caché para mejorar seguridad
RUN zypper refs && zypper refresh && zypper clean --all

# Cambiar al usuario seguro de forma explícita para que NADA corra como root
USER udacity_user
