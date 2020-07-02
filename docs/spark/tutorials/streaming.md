---
title: Tworzenie strukturalnego przesyłania strumieniowego za pomocą platformy .NET dla Apache Spark — samouczek
description: W ramach tego samouczka nauczysz się używać platformy .NET do Apache Spark na potrzeby przesyłania strumieniowego platformy Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 5420fe081db1704d7af647e8c88826c1bcf614d9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617846"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Samouczek: strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark

W tym samouczku pokazano, jak wywoływać strukturalne przesyłanie strumieniowe platformy Spark przy użyciu platformy .NET dla Apache Spark. Przetwarzanie strumieni danych w czasie rzeczywistym jest obsługiwane Apache Spark. Przetwarzanie strumieniowe oznacza analizowanie danych na żywo w miarę ich produkcji.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Utwórz i Uruchom platformę .NET dla aplikacji Apache Spark
> * Tworzenie strumienia danych za pomocą netcat
> * Korzystanie z funkcji zdefiniowanych przez użytkownika i SparkSQL do analizowania danych przesyłanych strumieniowo

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jest to pierwsza aplikacja .NET dla Apache Spark, Zacznij od [samouczka Wprowadzenie](get-started.md) , aby zapoznać się z podstawowymi informacjami.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. W wierszu polecenia Uruchom następujące polecenia, aby utworzyć nową aplikację konsolową:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   `dotnet`Polecenie tworzy `new` aplikację typu `console` . `-o`Parametr tworzy katalog o nazwie *mySparkStreamingApp* , w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami. `cd mySparkStreamingApp`Polecenie zmienia katalog na właśnie utworzony katalog aplikacji.

1. Aby używać platformy .NET do Apache Spark w aplikacji, zainstaluj pakiet Microsoft. Spark. W konsoli programu uruchom następujące polecenie:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Ustanawianie strumienia danych i nawiązywanie z nim połączenia

Jednym z popularnych sposobów testowania przetwarzania strumienia jest użycie **netcat**. netcat (znany również jako *NC*) umożliwia odczytywanie i zapisywanie połączeń sieciowych. Nawiązywane jest połączenie sieciowe z netcat za pomocą okna terminalu.

### <a name="create-a-data-stream-with-netcat"></a>Tworzenie strumienia danych za pomocą netcat

1. [Pobierz netcat](https://sourceforge.net/projects/nc110/files/). Następnie wyodrębnij plik z pliku zip i Dołącz wyodrębniony katalog do zmiennej środowiskowej "PATH".

2. Aby rozpocząć nowe połączenie, Otwórz nową konsolę i uruchom następujące polecenie, które nawiązuje połączenie z hostem localhost na porcie 9999.

   W systemie Windows:

   ```console
   nc -vvv -l -p 9999
   ```

   W systemie Linux:

   ```console
   nc -lk 9999
   ```

   Program Spark nasłuchuje danych wejściowych wpisywanych w tym wierszu polecenia.

### <a name="create-a-sparksession"></a>Utwórz SparkSession

1. Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* w *mySparkStreamingApp*:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Dodaj następujący kod do `Main` metody, aby utworzyć nowy `SparkSession` . Sesja platformy Spark jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API Dataframe.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Wywołanie obiektu *Spark* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i Dataframe w programie.

### <a name="connect-to-a-stream-with-readstream"></a>Łączenie ze strumieniem za pomocą ReadStream ()

`ReadStream()`Metoda zwraca metodę `DataStreamReader` , która może służyć do odczytu danych przesyłanych strumieniowo w jako `DataFrame` . Dołącz informacje o hoście i porcie, aby określić, gdzie aplikacja platformy Spark ma oczekiwać, że dane przesyłane strumieniowo.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Rejestrowanie funkcji zdefiniowanej przez użytkownika

W aplikacjach platformy Spark można używać funkcji UDF, *zdefiniowanych przez użytkownika*w celu wykonywania obliczeń i analizy danych.

Dodaj następujący kod do `Main` metody, aby zarejestrować funkcję UDF o nazwie `udfArray` .

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Ten format UDF przetwarza każdy ciąg otrzymany od terminalu netcat, aby utworzyć tablicę, która zawiera oryginalny ciąg (zawarty w *str*), a następnie oryginalny ciąg połączony z długością oryginalnego ciągu.

Na przykład wprowadzenie do usługi *Hello World* w terminalu netcat tworzy tablicę, w której:

* Tablica \[ 0] = Hello World
* Tablica \[ 1] = Hello World 11

## <a name="use-sparksql"></a>Użyj SparkSQL

Użyj SparkSQL do wykonywania różnych funkcji na danych przechowywanych w ramce Dataframe. Często należy połączyć UDF i SparkSQL, aby zastosować UDF do każdego wiersza ramki danych.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Ten fragment kodu stosuje *udfArray* do każdej wartości w ramce Dataframe, która reprezentuje każdy ciąg odczytywany z terminala netcat. Zastosuj metodę SparkSQL, <xref:Microsoft.Spark.Sql.Functions.Explode%2A> Aby umieścić każdy wpis tablicy w osobnym wierszu. Na koniec użyj, <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> Aby umieścić kolumny, które zostały utworzone w nowej ramce Dataframe *arrayDF.*

## <a name="display-your-stream"></a>Wyświetlanie strumienia

Służy <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> do ustalenia charakterystyki danych wyjściowych, takich jak drukowanie wyników do konsoli i wyświetlanie tylko najnowszych danych wyjściowych.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Uruchamianie kodu

Strukturalne przesyłanie strumieniowe w usłudze Spark przetwarza dane przez serię małych **partii**.  Po uruchomieniu programu w wierszu polecenia, w którym ustanawiane jest połączenie netcat, można zacząć pisać. Za każdym razem, gdy naciśniesz klawisz Enter po wpisaniu danych w tym wierszu polecenia, platforma Spark traktuje wpis jako zadanie wsadowe i uruchomi UDF.

### <a name="use-spark-submit-to-run-your-app"></a>Korzystanie z platformy Spark — przesyłanie w celu uruchomienia aplikacji

Po uruchomieniu nowej sesji netcat Otwórz nowy terminal i uruchom `spark-submit` polecenie, podobnie jak następujące polecenie:

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Pamiętaj, aby zaktualizować powyższe polecenie z rzeczywistą ścieżką do pliku JAR Microsoft Spark. Powyższe polecenie zakłada również, że serwer netcat jest uruchomiony na porcie lokalnym hosta 9999.

## <a name="get-the-code"></a>Uzyskiwanie kodu

Ten samouczek używa przykładu [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) , ale istnieją trzy inne przykłady przetwarzania pełnego strumienia w witrynie GitHub:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): liczba wyrazów dla danych przesyłanych strumieniowo z dowolnego źródła
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): liczba wyrazów dla danych z logiką okna
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): liczba wyrazów dla danych przesyłanych strumieniowo z Kafka

## <a name="next-steps"></a>Następne kroki

Przejdź do następnego artykułu, aby dowiedzieć się, jak wdrożyć aplikację .NET dla Apache Spark w usłudze datakostki.
> [!div class="nextstepaction"]
> [Samouczek: wdrażanie aplikacji .NET dla Apache Spark w kostkach](databricks-deployment.md)
