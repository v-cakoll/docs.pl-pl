---
title: Wprowadzenie do platformy .NET dla Apache Spark
description: Dowiedz się, jak uruchomić aplikację .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 679ee7660e96504768a781e1e384acab80362736
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743203"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Samouczek: Rozpoczynanie pracy z platformą .NET dla Apache Spark

W tym samouczku przedstawiono sposób uruchamiania aplikacji platformy .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:

> [!div class="checklist"]
>
> * Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark
> * Napisz swoją pierwszą aplikację .NET dla Apache Spark
> * Kompiluj i uruchamiaj prostą aplikację platformy .NET dla Apache Spark

## <a name="prepare-your-environment"></a>Przygotowywanie środowiska

Przed rozpoczęciem pisania aplikacji należy skonfigurować niektóre zależności wymagane wstępnie. Jeśli można uruchomić `dotnet`, `java`, `mvn``spark-shell` ze środowiska wiersza polecenia, środowisko jest już przygotowane i można przejść do następnej sekcji. Jeśli nie można uruchomić żadnego lub wszystkich poleceń, wykonaj następujące czynności.

### <a name="1-install-net"></a>1. Zainstaluj platformę .NET

Aby rozpocząć tworzenie aplikacji platformy .NET, należy pobrać i zainstalować zestaw .NET SDK (Software Development Kit).

Pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0). Zainstalowanie zestawu SDK dodaje `dotnet` łańcucha narzędzi do ścieżki.

Po zainstalowaniu zestaw .NET Core SDK Otwórz nowy wiersz polecenia i uruchom `dotnet`.

Jeśli polecenie jest uruchamiane i drukuje informacje o sposobach korzystania z programu dotnet, można przejść do następnego kroku. Jeśli wystąpi błąd `'dotnet' is not recognized as an internal or external command`, przed uruchomieniem polecenia upewnij się, że otwarto **Nowy** wiersz polecenia.

### <a name="2-install-java"></a>2. Zainstaluj środowisko Java

Zainstaluj [środowisko Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

Wybierz odpowiednią wersję systemu operacyjnego. Na przykład wybierz **JDK-8u201-Windows-x64. exe** dla komputera z systemem Windows x64. Następnie użyj `java` polecenia, aby sprawdzić poprawność instalacji.

![Pobieranie w języku Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a>3. Zainstaluj 7-zip

Apache Spark jest pobierany jako skompresowany plik TGZ. Użyj programu wyodrębniania, takiego jak 7-zip, aby wyodrębnić plik.

* Odwiedź stronę [7 — pobieranie plików zip](https://www.7-zip.org/).
* W pierwszej tabeli na stronie Wybierz pobieranie 32-bitowe x86 lub 64-bit x64, w zależności od używanego systemu operacyjnego.
* Po zakończeniu pobierania uruchom Instalatora.

![Pobieranie 7Zip](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a>4. Zainstaluj Apache Spark

[Pobierz i zainstaluj Apache Spark](https://spark.apache.org/downloads.html). Należy wybrać jedną z wersji 2,3. * lub 2.4.0, 2.4.1, 2.4.3 lub 2.4.4 (.NET dla Apache Spark nie jest zgodna z innymi wersjami Apache Spark).

W poniższych krokach przyjęto założenie, że [pobrano i zainstalowano Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Jeśli chcesz użyć innej wersji, Zastąp wartość **2.4.1** odpowiednim numerem wersji. Następnie wyodrębnij plik **. tar** i pliki Apache Spark.

Aby wyodrębnić zagnieżdżony plik **tar** :

* Znajdź pobrany plik **Spark-2.4.1-bin-Hadoop 2.7. tgz** .
* Kliknij prawym przyciskiem myszy plik i wybierz **7-zip-> Wyodrębnij tutaj**.
* **Spark-2.4.1-bin-Hadoop 2.7. tar** jest tworzony obok pobranego pliku **. tgz** .

Aby wyodrębnić pliki Apache Spark:

* Kliknij prawym przyciskiem myszy **Spark-2.4.1-bin-Hadoop 2.7. tar** i wybierz **7-zip-> Wyodrębnianie plików...**
* Wprowadź **C:\Bin** w polu **Wyodrębnij do** .
* Usuń zaznaczenie pola wyboru pod polem **Wyodrębnij do** .
* Wybierz **OK**.
* Pliki Apache Spark są wyodrębniane do C:\bin\spark-2.4.1-bin-hadoop2.7\

![Zainstaluj platformę Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania Apache Spark:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Po zainstalowaniu wszystkiego i ustawieniu zmiennych środowiskowych Otwórz **Nowy** wiersz polecenia i uruchom następujące polecenie:

`%SPARK_HOME%\bin\spark-submit --version`

Jeśli polecenie jest uruchamiane i drukuje informacje o wersji, można przejść do następnego kroku.

Jeśli wystąpi błąd `'spark-submit' is not recognized as an internal or external command`, upewnij się, że otwarto **Nowy** wiersz polecenia.

### <a name="5-install-net-for-apache-spark"></a>5. Zainstaluj program .NET dla Apache Spark

Pobierz wydanie [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) z platformy .net dla Apache Spark GitHub. Na przykład jeśli korzystasz z komputera z systemem Windows i planujesz korzystać z platformy .NET Core, [Pobierz wydanie systemu Windows x64 netcoreapp 2.1](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).

Aby wyodrębnić pakiet Microsoft. Spark. Worker:

* Znajdź pobrany plik **Microsoft. Spark. Worker. netcoreapp 2.1. win-x64-0.6.0. zip** .
* Kliknij prawym przyciskiem myszy i wybierz **7-zip-> Wyodrębnianie plików.** ...
* Wprowadź **C:\Bin** w polu **Wyodrębnij do** .
* Usuń zaznaczenie pola wyboru pod polem **Wyodrębnij do** .
* Wybierz **OK**.

![Zainstaluj platformę .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a>6. Zainstaluj WinUtils

Platforma .NET dla Apache Spark wymaga zainstalowania WinUtils razem z Apache Spark. [Pobierz winutils. exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Następnie skopiuj WinUtils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Jeśli używasz innej wersji usługi Hadoop, która ma adnotację na końcu nazwy folderu instalacji platformy Spark, [Wybierz wersję WinUtils](https://github.com/steveloughran/winutils) zgodną z wersją usługi Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Ustaw DOTNET_WORKER_DIR i sprawdź zależności

Uruchom następujące polecenie, aby ustawić zmienną środowiskową `DOTNET_WORKER_DIR`, która jest używana przez aplikacje platformy .NET do lokalizowania programu .NET dla Apache Spark:

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

Na koniec sprawdź, czy można uruchomić `dotnet`, `java`, `mvn``spark-shell` z poziomu wiersza polecenia przed przejściem do następnej sekcji.

## <a name="write-a-net-for-apache-spark-app"></a>Napisz aplikację platformy .NET dla Apache Spark

### <a name="1-create-a-console-app"></a>1. Tworzenie aplikacji konsolowej

W wierszu polecenia Uruchom następujące polecenia, aby utworzyć nową aplikację konsolową:

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

`dotnet` polecenie tworzy `new` aplikacji typu `console`. Parametr `-o` tworzy katalog o nazwie *mySparkApp* , w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami. `cd mySparkApp` polecenie zmienia katalog na właśnie utworzony katalog aplikacji.

### <a name="2-install-nuget-package"></a>2. Zainstaluj pakiet NuGet

Aby używać platformy .NET do Apache Spark w aplikacji, zainstaluj pakiet Microsoft. Spark. W wierszu polecenia Uruchom następujące polecenie:

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a>3. kod aplikacji

Otwórz *program.cs* w Visual Studio Code lub dowolnym edytorze tekstów i Zastąp cały kod następującym kodem:

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-add-data-file"></a>4. Dodaj plik danych

Aplikacja przetwarza plik zawierający wiersze tekstu. Utwórz plik *Input. txt* w katalogu *mySparkApp* , zawierający następujący tekst:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Uruchamianie aplikacji platformy .NET dla Apache Spark

1. Uruchom następujące polecenie, aby skompilować aplikację:

   ```dotnetcli
   dotnet build
   ```

2. Uruchom następujące polecenie, aby przesłać aplikację do uruchamiania na Apache Spark:

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. Gdy aplikacja zostanie uruchomiona, dane zliczania plików *wejściowych. txt* są zapisywane w konsoli programu.

Gratulacje! Pomyślnie utworzono i uruchomiono aplikację .NET dla Apache Spark.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark
> * Napisz swoją pierwszą aplikację .NET dla Apache Spark
> * Kompiluj i uruchamiaj prostą aplikację platformy .NET dla Apache Spark

Aby wyświetlić film wideo z objaśnieniem powyższych kroków, Zaewidencjonuj [serie wideo dla programu .net for Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Zapoznaj się ze stroną zasobów, aby dowiedzieć się więcej.
> [!div class="nextstepaction"]
> [Platforma .NET dla Apache Spark zasobów](../resources/index.md)
