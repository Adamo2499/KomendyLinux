# Naprawnienie błędu o braku uprawnień do laravel.log

I sposób: wyczyszczenie cacha projektu:

```bash
php artisan cache:clear
chmod -R 777 storage/
composer dump-autoload
```

II sposób: utworzenie kopii laravel.log

```bash
cd ./storage/logs
cat laravel.log > laravel_copy.log
mv laravel.log laravel2.log
chmod 777 laravel_copy.log
mv laravel_copy.log laravel.log
chmod 775 laravel.log
```
