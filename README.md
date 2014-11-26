AndroidManifest-com-multiplas-tag-application
=============================================

Utilizando duas classes do tipo Application em um AndroidManifest

Bom, depois de tanto quebrar a cabeça com essa questão que parece simples (e é), resolvi postar a solução para o problema.
Recentemente precisei utilizar as bibliotecas Parse e Volley em uma aplicação que desenvolvi, daí veio o problema, ambas precisam ser declaradas na TAG Aplication do AndroidManifest, na propriedade android:name="pacote.NomeApplication".
Pois bem, o AndroidManifest só aceita uma única TAG Application, mas para contornar essa situação, basta estender (extends) uma classe da outra, exemplo:

arquivo: ParseApplication.java

    Public class ParseApplication extends Application {
    ...
    }


Agora é só estender VolleyApplication de ParseApplication:

arquivo: VolleyApplication.java

    Public class VolleyApplication extends ParseApplication {
    ...
    }

resultado no AndroidManifest:

    <application
    android:name="pacote.VolleyApplication"
    android:allowBackup="true"
    android:icon="@drawable/ic_launcher"
    android:label="@string/app_name"
    android:theme="@style/AppTheme" >
    <activity
    .
    .
    .
    </activity
    </application>

É isso, pessoal.
