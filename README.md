# Домашнее задание «Введение в Terraform» - Подус Сергей

### Задание 1

1. Перейдите в каталог [**src**](https://github.com/netology-code/ter-homeworks/tree/main/01/src). Скачайте все необходимые зависимости, использованные в проекте. 
2. Изучите файл **.gitignore**. В каком terraform-файле, согласно этому .gitignore, допустимо сохранить личную, секретную информацию?
3. Выполните код проекта. Найдите  в state-файле секретное содержимое созданного ресурса **random_password**, пришлите в качестве ответа конкретный ключ и его значение.
4. Раскомментируйте блок кода, примерно расположенный на строчках 29–42 файла **main.tf**.
Выполните команду ```terraform validate```. Объясните, в чём заключаются намеренно допущенные ошибки. Исправьте их.
5. Выполните код. В качестве ответа приложите: исправленный фрагмент кода и вывод команды ```docker ps```.
6. Замените имя docker-контейнера в блоке кода на ```hello_world```. Не перепутайте имя контейнера и имя образа. Мы всё ещё продолжаем использовать name = "nginx:latest". Выполните команду ```terraform apply -auto-approve```.
Объясните своими словами, в чём может быть опасность применения ключа  ```-auto-approve```. Догадайтесь или нагуглите зачем может пригодиться данный ключ? В качестве ответа дополнительно приложите вывод команды ```docker ps```.
8. Уничтожьте созданные ресурсы с помощью **terraform**. Убедитесь, что все ресурсы удалены. Приложите содержимое файла **terraform.tfstate**. 
9. Объясните, почему при этом не был удалён docker-образ **nginx:latest**. Ответ **обязательно** подкрепите строчкой из документации [**terraform провайдера docker**](https://docs.comcloud.xyz/providers/kreuzwerker/docker/latest/docs).  (ищите в классификаторе resource docker_image )

## Ответ:

2. В соответствии с файлом .gitignore хранить личную информацию допустимо в файле **personal.auto.tfvars** 

3. Содержимое **state-файла**: "result": "7EuR6Tb9xfoqMP6u" 

4. В коде были специально допущены ошибки, наверное для того, что бы проверить нашу "внимательность" 

Ошибки: "1nginx" и resource "docker_image" нет строки названия образа "nginx", name  = "example_${random_password.random_string_FAKE.resulT}" - убираем Fake и буква "T" должна 

быть маленькой

6. Ключ -auto-approve в команде terraform apply удаляет подтверждение действия перед применением изменений. Это означает, что Terraform автоматически применит все изменения, 

указанные в файле конфигурации, без запроса подтверждения от пользователя, а это в свою очередь может навлечь проблемы.

8. 
```
{
  "version": 4,
  "terraform_version": "1.5.5",
  "serial": 12,
  "lineage": "d478f2ab-6ef1-cc47-ded7-27c783387475",
  "outputs": {},
  "resources": [],
  "check_results": null
}
```

9. По умолчанию Terraform не удаляет docker-образы. Terraform управляет ресурсами уровня инфраструктуры, такими как виртуальные машины, контейнеры и сети, но не управляет контентом 

внутри контейнеров. Поэтому удаление контейнера не приведет к автоматическому удалению связанного с ним образа.

```
force_remove (Boolean) If true, then the image is removed forcibly when the resource is destroyed.

keep_locally (Boolean) If true, then the Docker image won't be deleted on destroy operation. If this is false, it will delete the image from the docker local storage on destroy operation.
```

## Скриншоты к работе

![Скриншот 1](https://github.com/Wanderwille/scrinshot/blob/main/terraform.png)

![Скриншот 2](https://github.com/Wanderwille/scrinshot/blob/main/terraform2.png)

![Скриншот 3](https://github.com/Wanderwille/scrinshot/blob/main/terraform3.png)

![Скриншот 4](https://github.com/Wanderwille/scrinshot/blob/main/terraform4.png)

![Скриншот 5](https://github.com/Wanderwille/scrinshot/blob/main/terraform5.png)

![Скриншот 6](https://github.com/Wanderwille/scrinshot/blob/main/terraform6.png)