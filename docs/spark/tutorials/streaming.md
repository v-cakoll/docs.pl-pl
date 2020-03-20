---
title: Ustrukturyzowane przesyłanie strumieniowe za pomocą samouczka .NET for Apache Spark
description: W tym samouczku dowiesz się, jak używać platformy .NET for Apache Spark for Spark Structured Streaming.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186512"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Samouczek: Zorganizowane przesyłanie strumieniowe z .NET dla platformy Apache Spark

W tym samouczku dowiesz się, jak wywołać usługi Spark Structured Streaming przy użyciu platformy .NET dla platformy Apache Spark. Spark Structured Streaming to obsługa apache Spark do przetwarzania strumieni danych w czasie rzeczywistym. Przetwarzanie strumienia oznacza analizowanie danych na żywo podczas ich tworzenia.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Tworzenie i uruchamianie aplikacji .NET dla aplikacji Apache Spark
> * Tworzenie strumienia danych za pomocą netcata
> * Używanie funkcji zdefiniowanych przez użytkownika i sparksql do analizowania danych przesyłania strumieniowego

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jest to twoja pierwsza aplikacja .NET dla platformy Apache Spark, zacznij od [samouczka Wprowadzenie,](get-started.md) aby zapoznać się z podstawami.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. W wierszu polecenia uruchom następujące polecenia, aby utworzyć nową aplikację konsoli:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   Polecenie `dotnet` tworzy `new` aplikację typu `console` dla Ciebie. Parametr `-o` tworzy katalog o nazwie *mySparkStreamingApp,* w którym aplikacja jest przechowywana i wypełnia go wymaganymi plikami. Polecenie `cd mySparkStreamingApp` zmienia katalog na katalog aplikacji, który został właśnie utworzony.

1. Aby użyć platformy .NET for Apache Spark w aplikacji, należy zainstalować pakiet Microsoft.Spark. W konsoli uruchom następujące polecenie:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Ustanawianie strumienia danych i łączenie się z nią

Jednym z popularnych sposobów testowania przetwarzania strumienia jest za pośrednictwem **netcat**. netcat (znany również jako *nc)* pozwala na odczyt i zapis do połączeń sieciowych. Nawiązujesz połączenie sieciowe z netcatem przez okno terminala.

### <a name="create-a-data-stream-with-netcat"></a>Tworzenie strumienia danych za pomocą netcat

1. [Pobierz netcat](https://sourceforge.net/projects/nc110/files/). Następnie wyodrębnij plik z pobierania zip i dołącz katalog wyodrębniony do zmiennej środowiskowej "PATH".

2. Aby rozpocząć nowe połączenie, otwórz nową konsolę i uruchom następujące polecenie, które łączy się z localhostem na porcie 9999.

   W systemie Windows:

   ```console
   nc -vvv -l -p 9999
   ```

   W systemie Linux:

   ```console
   nc -lk 9999
   ```

   Program Spark nasłuchuje wpisanych danych wejściowych w tym wierszu polecenia.

### <a name="create-a-sparksession"></a>Tworzenie sparkSession

1. Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs* w *mySparkStreamingApp:*

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Dodaj następujący kod `Main` do metody, `SparkSession`aby utworzyć nowy plik . Sesja iskry jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Wywołanie obiektu *iskrzącego* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i DataFrame w całym programie.

### <a name="connect-to-a-stream-with-readstream"></a>Łączenie się ze strumieniem za pomocą readstream()

Metoda `ReadStream()` `DataStreamReader` zwraca, który może służyć do odczytu `DataFrame`przesyłania strumieniowego danych w jako . Dołącz informacje o hoście i porcie, aby poinformować aplikację Spark, gdzie należy się spodziewać jej danych przesyłania strumieniowego.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Rejestrowanie funkcji zdefiniowanej przez użytkownika

W aplikacjach Spark można używać plików UDF, *funkcji zdefiniowanych przez użytkownika,* do wykonywania obliczeń i analiz danych.

Dodaj następujący kod `Main` do metody, aby `udfArray`zarejestrować UDF o nazwie .

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Ten UDF przetwarza każdy ciąg odbierany z terminala netcat do produkcji tablicy, która zawiera oryginalny ciąg (zawarte w *str*), a następnie oryginalny ciąg połączony z długością oryginalnego ciągu.

Na przykład wejście *Hello world* w terminalu netcat tworzy tablicę, w której:

* tablica\[0] = Hello world
* tablica\[1] = Hello world 11

## <a name="use-sparksql"></a>Użyj SparkSQL

Użyj SparkSQL do wykonywania różnych funkcji na danych przechowywanych w dataframe. Często łączyć pliki UDF i SparkSQL, aby zastosować UDF do każdego wiersza elementu DataFrame.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Ten fragment kodu stosuje *udfArray* do każdej wartości w dataframe, która reprezentuje każdy ciąg odczytu z terminala netcat. Zastosuj SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A> metody, aby umieścić każdy wpis tablicy w swoim własnym wierszu. Na koniec <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> użyj umieścić kolumny, które zostały wyprodukowane w nowej *dataframe arrayDF.*

## <a name="display-your-stream"></a>Wyświetlanie strumienia

Służy <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> do ustanawiania cech danych wyjściowych, takich jak drukowanie wyników na konsoli i wyświetlanie tylko najnowszych danych wyjściowych.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Uruchom swój kod

Przetwarzanie w ustrukturyzowanym programie Spark przetwarza dane za pośrednictwem serii małych **partii.**  Po uruchomieniu programu wiersz polecenia, w którym nawiązano połączenie netcat, umożliwia rozpoczęcie pisania. Za każdym razem, gdy po naciśnięciu klawisza Enter po wpisaniu danych w tym wierszu polecenia spark uznaje wpis za partię i uruchamia UDF.

### <a name="use-spark-submit-to-run-your-app"></a>Uruchamianie aplikacji za pomocą spark-submit

Po uruchomieniu nowej sesji netcat otwórz nowy `spark-submit` terminal i uruchom polecenie, podobne do następującego polecenia:

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Pamiętaj, aby zaktualizować powyższe polecenie za pomocą rzeczywistej ścieżki do pliku jar platformy Microsoft Spark. Powyższe polecenie zakłada również, że serwer netcat jest uruchomiony na porcie localhost 9999.

## <a name="get-the-code"></a>Uzyskiwanie kodu

W tym samouczku użyto [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) przykładu, ale istnieją trzy inne przykłady przetwarzania pełnego strumienia w usłudze GitHub:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): liczba słów na danych przesyłanych strumieniowo z dowolnego źródła
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): liczba słów na danych z logiką okna
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): liczba słów na dane przesyłane strumieniowo z Platformy Kafka

## <a name="next-steps"></a>Następne kroki

Przejdź do następnego artykułu, aby dowiedzieć się, jak wdrożyć aplikację platformy .NET for Apache Spark w witrynie Databricks.
> [!div class="nextstepaction"]
> [Samouczek: Wdrażanie aplikacji .NET dla platformy Spark apache w databricks](databricks-deployment.md)
