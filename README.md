# Домашнее задание к занятию "14.4 Сервис-аккаунты"

## Задача 1: Работа с сервис-аккаунтами через утилиту kubectl в установленном minikube

Выполните приведённые команды в консоли. Получите вывод команд. Сохраните
задачу 1 как справочный материал.

### Как создать сервис-аккаунт?

```
kubectl create serviceaccount netology
```
***Ответ:***
![Alt text](https://i.ibb.co/xCQVjp0/Screenshot-1.jpg)

### Как просмотреть список сервис-акаунтов?

```
kubectl get serviceaccounts
kubectl get serviceaccount
```
***Ответ:***
![Alt text](https://i.ibb.co/M6qNYjK/Screenshot-2.jpg)

### Как получить информацию в формате YAML и/или JSON?

```
kubectl get serviceaccount netology -o yaml
kubectl get serviceaccount default -o json
```
***Ответ:***
![Alt text](https://i.ibb.co/Sv3zLmD/Screenshot-3.jpg)
![Alt text](https://i.ibb.co/6BByBqp/Screenshot-4.jpg)

### Как выгрузить сервис-акаунты и сохранить его в файл?

```
kubectl get serviceaccounts -o json > serviceaccounts.json
kubectl get serviceaccount netology -o yaml > netology.yml
```
***Ответ:***
![Alt text](https://i.ibb.co/RBR7pcp/Screenshot-5.jpg)

### Как удалить сервис-акаунт?

```
kubectl delete serviceaccount netology
```
***Ответ:***
![Alt text](https://i.ibb.co/wM8S3PJ/Screenshot-6.jpg)

### Как загрузить сервис-акаунт из файла?

```
kubectl apply -f netology.yml
```
***Ответ:***
![Alt text](https://i.ibb.co/w0XjM2W/Screenshot-7.jpg)

## Задача 2 (*): Работа с сервис-акаунтами внутри модуля

Выбрать любимый образ контейнера, подключить сервис-акаунты и проверить
доступность API Kubernetes

```
kubectl run -i --tty fedora --image=fedora --restart=Never -- sh
```
***Ответ:***
![Alt text](https://i.ibb.co/mJb7DWg/Screenshot-8.jpg)

Просмотреть переменные среды

```
env | grep KUBE
```
![Alt text](https://i.ibb.co/wJrsjxt/Screenshot-9.jpg)

Получить значения переменных
```
K8S=https://$KUBERNETES_SERVICE_HOST:$KUBERNETES_SERVICE_PORT
SADIR=/var/run/secrets/kubernetes.io/serviceaccount
TOKEN=$(cat $SADIR/token)
CACERT=$SADIR/ca.crt
NAMESPACE=$(cat $SADIR/namespace)
```
***Ответы:***
![Alt text](https://i.ibb.co/svSDrcr/Screenshot-11.jpg)

Подключаемся к API

```
curl -H "Authorization: Bearer $TOKEN" --cacert $CACERT $K8S/api/v1/
```
***Ответ:***

Результат команды:  *[API output](https://github.com/romrsch/netology-14.4/blob/main/api_output.md)*.



