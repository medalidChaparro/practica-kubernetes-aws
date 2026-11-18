# Práctica 11 - Kubernetes Multi-Nodo en AWS

## Descripción
Implementación de un clúster Kubernetes con dos nodos EC2 en AWS,
configuración de red mediante Flannel, comunicación entre Pods
y Services, y almacenamiento persistente mediante PV y PVC.

## Arquitectura
- Master: 172.31.41.59
- Worker: 172.31.32.73
- Kubernetes: v1.37.2
- Container Runtime: containerd
- Red CNI: Flannel VXLAN
- Aplicación: Nginx
- Exposición: NodePort 30335

## Comunicación
- Deployment Nginx con 2 réplicas.
- Service tipo NodePort.
- ClusterIP: 10.97.112.214.
- Acceso externo mediante el puerto 30335.

## Persistencia
- PersistentVolume: pv-local-worker.
- PersistentVolumeClaim: pvc-local-worker.
- Capacidad: 1Gi.
- Tipo: Local PersistentVolume.
- Nodo: Worker.
- Ruta: /mnt/k8s-pv.
- Política: Retain.

## Prueba de persistencia
Se creó un archivo dentro del volumen, se eliminó el Pod,
se recreó y se verificó que el archivo conservaba su contenido.

## Estructura
- comunicacion/
- persistencia/
