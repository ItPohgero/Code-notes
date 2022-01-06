# Cara Membatasi akses HTTP dan Redirect ke HTTPS di Laravel dengan Middleware

1.  Buat Middleware dengan nama HttpsProtocol
    * Nama bebas
    Dengan cara menulis perintah **php artisan make:middleware** HttpsProtocol
    Maka file middleware baru akan terbuat pada app/http/middleware
 
2.  Akse file Middleware pada app/http/middleware
    Masukkan code berikut :

    ```
    if (!$request->secure() && env('APP_ENV') === 'production') {
        return redirect()->secure($request->getRequestUri());
    }
    ```

3.  Setting midleware pada kernel.php
    Letakkan code berikut pada middlewareGroups[web]
    ```
    \App\Http\Middleware\HttpsProtocol::class
    ```
    Tiga langkah simple, dan website kamu akan lebih aman dan keren!
    itpohgero.com