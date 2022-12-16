# Naprawnienie błędu o braku uprawnień do laravel.log

```bash
cd /storage/logs
cat laravel.log > laravel_copy.log
mv laravel.log laravel2.log
chmod 777 laravel_copy.log
mv laravel_copy.log laravel.log
chmod 775 laravel.log
```
