---
title: Analiza tonacji za pomocą platformy .NET dla platformy Apache Spark i samouczka ML.NET
description: W tym samouczku dowiesz się, jak używać ML.NET z .NET dla platformy Apache Spark do analizy tonacji.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391259"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Samouczek: Analiza tonacji za pomocą platformy .NET dla platformy Spark i ML.NET

Ten samouczek uczy, jak to zrobić analiza tonacji opinii online przy użyciu ML.NET i .NET dla Apache Spark. [ML.NET](http://dot.net/ml) jest bezpłatną, wieloplatformową platformą uczenia maszynowego typu open source. ML.NET z .NET for Apache Spark można użyć do skalowania szkolenia i przewidywania algorytmów uczenia maszynowego.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Tworzenie modelu analizy tonacji przy użyciu ML.NET kreatora modeli w programie Visual Studio.
> * Utwórz aplikację konsoli .NET dla platformy Apache Spark.
> * Napisz i zaimplementuj funkcję zdefiniowaną przez użytkownika.
> * Uruchom aplikację konsoli .NET for Apache Spark.

## <a name="prerequisites"></a>Wymagania wstępne

* Jeśli nie zostały opracowane .NET dla aplikacji Platformy Apache Spark przed, należy rozpocząć od [wprowadzenie samouczek,](get-started.md) aby zapoznać się z podstawami. Wypełnij wszystkie wymagania wstępne samouczka Wprowadzenie przed kontynuowaniem tego samouczka.

* W tym samouczku użyto ML.NET Programu Model Builder (preview), interfejsu wizualnego dostępnego w programie Visual Studio. Jeśli nie masz jeszcze programu Visual Studio, możesz [pobrać wersję społecznościową programu Visual Studio](https://visualstudio.microsoft.com/downloads/) za darmo.

* [Pobieranie i instalowanie](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Kreator modeli (wersja zapoznawcza).

* Pobierz zestawy danych [recenzji yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) i [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.

## <a name="review-the-data"></a>Przejrzyj dane

Zestaw danych opinii Yelp zawiera opinie online Yelp o różnych usługach. Otwórz [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) i zwróć uwagę na strukturę danych. Pierwsza kolumna zawiera tekst recenzji, a druga zawiera wyniki tonacji. Jeśli wynik tonacji wynosi 1, recenzja jest pozytywna, a wynik tonacji wynosi 0, ocena jest negatywna.

Poniższa tabela zawiera przykładowe dane:

|Tekst recenzji|Opinia|
|-|-|
|Wow... Bardzo dobre miejsce na życie.|    1|
|Skorupa nie jest dobra.|    0|

## <a name="build-your-machine-learning-model"></a>Tworzenie modelu uczenia maszynowego

1. Otwórz program Visual Studio i utwórz nową aplikację konsoli języka C# (Core.NET). Nazwij projekt *MLSparkModel*.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *MLSparkModel.* Następnie wybierz pozycję **Dodaj > uczenie maszynowe**.

1. W ML.NET Konstruktora modeli wybierz kafelek scenariusz **analizy tonacji.**

1. Na stronie **Dodawanie danych** prześlij zestaw danych *yelptrain.csv.*

1. Wybierz *pozycję Sentyment* z listy rozwijanej **Kolumny, aby przewidzieć.**

1. Na stronie **Pociąg** ustaw czas treningu na *60 sekund* i wybierz **pozycję Rozpocznij szkolenie**. Zwróć uwagę na status treningu w obszarze **Postęp**.

1. Po zakończeniu szkolenia kreatora modeli **oceń** wyniki szkolenia. Możesz wpisać frazy w polu tekstowym poniżej **Wypróbuj model** i wybierz **pozycję Przewiduj,** aby wyświetlić dane wyjściowe.

1. Wybierz **pozycję Kod,** a następnie wybierz pozycję **Dodaj projekty,** aby dodać model ml do rozwiązania.

1. Należy zauważyć, że dwa projekty są dodawane do rozwiązań: **MLSparkModelML.ConsoleApp** i **MLSparkModelML.Model**.

1. Kliknij dwukrotnie projekt *MLSpark* C# i zwróć uwagę, że dodano następujące odwołanie do projektu.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Tworzenie aplikacji konsolowej

Kreator modeli tworzy aplikację konsoli dla Ciebie.

1. Kliknij prawym przyciskiem myszy **mlsparkModelML.Console** w Eksploratorze rozwiązań i wybierz pozycję **Zarządzaj pakietami NuGet**.

1. Wyszukaj witrynę **Microsoft.Spark** i zainstaluj pakiet. **Microsoft.ML** jest automatycznie instalowany przez Program Model Builder.

### <a name="create-a-sparksession"></a>Tworzenie sparkSession

1. Otwórz plik *Program.cs* dla **aplikacji MLSparkModelML.ConsoleApp**. Ten plik został automatycznie zwykli przez Kreatora modeli. Usuń `using` instrukcje, zawartość Main() metody i `CreateSingleDataSample` regionu.

1. Dodaj następujące `using` dodatkowe instrukcje do górnej części *Program.cs:*

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Zmień `DATA_FILEPATH` ścieżkę swojego *yelptest.csv*.

1. Dodaj następujący kod `Main` do metody, `SparkSession`aby utworzyć nowy plik . Sesja iskry jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Wywołanie obiektu *iskrzącego* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i DataFrame w całym programie.

### <a name="create-a-dataframe-and-print-to-console"></a>Tworzenie elementu DataFrame i drukowanie na konsoli

Przeczytaj w yelp przeglądu danych z pliku *yelptest.csv* jako `DataFrame`. Dołącz `header` `inferSchema` i opcje. Opcja `header` odczytuje pierwszy wiersz *yelptest.csv* jako nazwy kolumn zamiast danych. Opcja `inferSchema` wywnioskować typy kolumn na podstawie danych.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Rejestrowanie funkcji zdefiniowanej przez użytkownika

W aplikacjach Spark można używać plików UDF, *funkcji zdefiniowanych przez użytkownika,* aby wykonywać obliczenia i analizy danych. W tym samouczku używasz ML.NET z UDF do oceny każdej recenzji Yelp.

Dodaj następujący kod `Main` do metody, aby `MLudf`zarejestrować UDF o nazwie .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Ten UDF przyjmuje ciąg przeglądu Yelp jako dane wejściowe i wyprowadza prawdziwe lub fałszywe dla pozytywnych lub negatywnych nastrojów, odpowiednio. Używa *predict()* metody zdefiniowanej w późniejszym kroku.

### <a name="use-spark-sql-to-call-the-udf"></a>Wywoływanie usługi UDF za pomocą programu Spark SQL

Teraz, gdy zostały przeczytane w danych i włączone ML, użyj Spark SQL do wywołania UDF, który będzie uruchamiać analizę tonacji w każdym wierszu dataframe. Dodaj następujący kod `Main` do swojej metody:

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a>Utwórz metodę predict()

Dodaj następujący kod `Main()` przed metodą. Ten kod jest podobny do tego, co jest produkowane przez Model Builder w *ConsumeModel.cs*. Przeniesienie tej metody na konsolę powoduje załadowanie modelu przy każdym uruchomieniu aplikacji.

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a>Dodawanie modelu do aplikacji konsoli

W Eksploratorze rozwiązań skopiuj plik *MLModel.zip* z projektu **MLSparkModelML.Model** i wklej go w projekcie **MLSparkModelML.ConsoleApp.** Odwołanie jest automatycznie dodawane w *pliku MLSparkModelML.ConsoleApp.csproj*.

## <a name="run-your-code"></a>Uruchom swój kod

Użyj `spark-submit` do uruchomienia kodu. Przejdź do folderu głównego aplikacji konsoli za pomocą wiersza polecenia i uruchom następujące polecenia.

Najpierw oczyść i opublikuj aplikację.

```dotnetcli
dotnet clean
dotnet publish
```

Następnie przejdź do folderu publikowania aplikacji konsoli `spark-submit` i uruchom następujące polecenie. Pamiętaj, aby zaktualizować polecenie za pomocą rzeczywistej ścieżki pliku jar programu Microsoft Spark.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Uzyskiwanie kodu

Ten samouczek jest podobny do kodu z [analizy tonacji z](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) big data przykład.

## <a name="next-steps"></a>Następne kroki

Przejdź do następnego artykułu, aby dowiedzieć się, jak wykonać ustrukturyzowane przesyłanie strumieniowe za pomocą platformy .NET dla platformy Apache Spark.
> [!div class="nextstepaction"]
> [Samouczek: Zorganizowane przesyłanie strumieniowe z .NET dla platformy Apache Spark](streaming.md)
