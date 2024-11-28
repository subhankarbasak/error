
Error While installing 'maatwebsite/excel' package in Laravel 11 on 28.11.2024 using composer require maatwebsite/excel in cmd:
    ```
        > Illuminate\Foundation\ComposerScripts::postAutoloadDump
        > @php artisan package:discover --ansi

        BadMethodCallException

        Method Illuminate\Foundation\Application::share does not exist.

        at vendor\laravel\framework\src\Illuminate\Macroable\Traits\Macroable.php:115
            111▕      */
            112▕     public function __call($method, $parameters)
            113▕     {
            114▕         if (! static::hasMacro($method)) {
        ➜ 115 ▕             throw new BadMethodCallException(sprintf(
            116▕                 'Method %s::%s does not exist.', static::class, $method
            117▕             ));
            118▕         }
            119▕

        1   vendor\maatwebsite\excel\src\Maatwebsite\Excel\ExcelServiceProvider.php:154
            Illuminate\Foundation\Application::__call("share")

        2   vendor\maatwebsite\excel\src\Maatwebsite\Excel\ExcelServiceProvider.php:58
            Maatwebsite\Excel\ExcelServiceProvider::bindClasses()
    ```
Solutions:
    ```
    I am using laravel 11. After running following steps everything seems to be fine.

    Go to composer.json
    Update "maatwebsite/excel": "^3.1",
    Run composer update

    *Optionals step and for laravel 10:*
        Go to config->app.php
        Add to providers Maatwebsite\Excel\ExcelServiceProvider::class,
        Add to aliases 'Excel' =>Maatwebsite\Excel\Facades\Excel::class,
        Run composer dump-autoload
    ```