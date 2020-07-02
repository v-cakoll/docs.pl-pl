---
title: Analiza tonacji za pomocą platformy .NET dla Apache Spark i samouczka ML.NET
description: W ramach tego samouczka nauczysz się używać ML.NET z platformą .NET do Apache Spark na potrzeby analizy tonacji.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 69deb30419b98536fa309547d94f59bb266e413c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617586"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Samouczek: Analiza tonacji z platformą .NET dla Apache Spark i ML.NET

W tym samouczku przedstawiono, jak przeprowadzić analizę tonacjiych przeglądów online przy użyciu ML.NET i platformy .NET dla Apache Spark. [Ml.NET](http://dot.net/ml) to bezpłatna, międzyplatformowa platforma uczenia maszynowego typu open source. Możesz użyć ML.NET z platformą .NET dla Apache Spark do skalowania szkoleń i przewidywania algorytmów uczenia maszynowego.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Utwórz model analizy tonacji przy użyciu konstruktora modelu ML.NET w programie Visual Studio.
> * Utwórz aplikację konsolową platformy .NET dla Apache Spark.
> * Pisanie i implementowanie funkcji zdefiniowanej przez użytkownika.
> * Uruchom aplikację konsolową platformy .NET dla Apache Spark.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Wymagania wstępne

* Jeśli jeszcze nie opracowano aplikacji .NET for Apache Spark, Zacznij od [samouczka Wprowadzenie](get-started.md) , aby zapoznać się z podstawowymi informacjami. Przed kontynuowaniem pracy z tym samouczkiem wykonaj wszystkie wymagania wstępne dotyczące samouczka Wprowadzenie.

* Ten samouczek używa programu ML.NET model Builder (wersja zapoznawcza) — interfejsu wizualizacji dostępnego w programie Visual Studio. Jeśli nie masz jeszcze programu Visual Studio, możesz bezpłatnie [pobrać wersję społeczności programu Visual Studio](https://visualstudio.microsoft.com/downloads/) .

* [Pobierz i zainstaluj](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET model Builder (wersja zapoznawcza).

* Pobierz zestawy danych [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) i [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.

## <a name="review-the-data"></a>Przejrzyj dane

Zestaw danych Yelp Reviews zawiera przeglądy online Yelp dotyczące różnych usług. Otwórz [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) i zwróć uwagę na strukturę danych. Pierwsza kolumna zawiera tekst przeglądu, a druga kolumna zawiera wyniki tonacji. Jeśli wynik tonacji wynosi 1, przegląd jest dodatni i jeśli wynik tonacji jest równy 0, przegląd jest ujemny.

Poniższa tabela zawiera przykładowe dane:

|ReviewText|Opinia|
|-|-|
|Wow... Uwielbiane to miejsce.|    1|
|Crust nie jest dobry.|    0|

## <a name="build-your-machine-learning-model"></a>Kompilowanie modelu uczenia maszynowego

1. Otwórz program Visual Studio i Utwórz nową aplikację konsolową w języku C# (.NET Core). Nazwij projekt *MLSparkModel*.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *MLSparkModel* . Następnie wybierz pozycję **dodaj > Machine Learning**.

1. Z konstruktora modelu ML.NET wybierz kafelek scenariusz **Analiza tonacji** .

1. Na stronie **Dodawanie danych** Przekaż zestaw danych *yelptrain.csv* .

1. Wybierz pozycję *tonacji* z listy rozwijanej **kolumny do prognozowania** .

1. Na stronie **uczenie** Ustaw czas uczenia na *60 sekund* i wybierz pozycję **Rozpocznij szkolenie**. Zwróć uwagę na stan szkolenia w **toku**.

1. Po zakończeniu szkolenia konstruktora modeli **Oceń** wyniki szkolenia. Możesz wpisać frazy w polu tekstowym poniżej **Wypróbuj model** i wybrać pozycję **przewidywanie** , aby wyświetlić dane wyjściowe.

1. Wybierz pozycję **kod** , a następnie wybierz pozycję **Dodaj projekty** , aby dodać model ml do rozwiązania.

1. Zwróć uwagę, że dwa projekty są dodawane do rozwiązań: **MLSparkModelML. ConsoleApp** i **MLSparkModelML. model**.

1. Kliknij dwukrotnie projekt *MLSpark* C# i zwróć uwagę, że dodano następujące odwołanie do projektu.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>tworzenie aplikacji konsoli

Konstruktor modelu tworzy aplikację konsolową.

1. Kliknij prawym przyciskiem myszy pozycję **MLSparkModelML. Console** w Eksplorator rozwiązań i wybierz pozycję **Zarządzaj pakietami NuGet**.

1. Wyszukaj ciąg **Microsoft. Spark** i zainstaluj pakiet. Program **Microsoft.ml** jest automatycznie instalowany przez konstruktora modelu.

### <a name="create-a-sparksession"></a>Utwórz SparkSession

1. Otwórz plik *program.cs* dla **MLSparkModelML. ConsoleApp**. Ten plik został automatycznie wygenerowany przez konstruktora modelu. Usuń `using` instrukcje, zawartość metody Main () i `CreateSingleDataSample` region.

1. Dodaj następujące dodatkowe `using` instrukcje na początku *program.cs*:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Zmień `DATA_FILEPATH` ścieżkę na *yelptest.csv*.

1. Dodaj następujący kod do `Main` metody, aby utworzyć nowy `SparkSession` . Sesja platformy Spark jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API Dataframe.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Wywołanie obiektu *Spark* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i Dataframe w programie.

### <a name="create-a-dataframe-and-print-to-console"></a>Tworzenie ramki danych i drukowanie do konsoli

Przeczytaj dane Yelp z pliku *yelptest.csv* jako `DataFrame` . `header`Opcje include i `inferSchema` . `header`Opcja odczytuje pierwszy wiersz *yelptest.csv* jako nazwy kolumn, a nie dane. `inferSchema`Opcja dla typów kolumn na podstawie danych.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Rejestrowanie funkcji zdefiniowanej przez użytkownika

W aplikacjach platformy Spark można używać funkcji UDF, *zdefiniowanych przez użytkownika*w celu wykonywania obliczeń i analizy danych. W tym samouczku użyjesz ML.NET z UDF, aby oszacować każdy Yelp przegląd.

Dodaj następujący kod do `Main` metody, aby zarejestrować funkcję UDF o nazwie `MLudf` .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Ten format UDF Pobiera ciąg Yelp jako dane wejściowe i generuje odpowiednio wartość true lub false dla wartości dodatnich lub ujemnych mową. Używa metody *predykcyjnej ()* zdefiniowanej w późniejszym kroku.

### <a name="use-spark-sql-to-call-the-udf"></a>Używanie platformy Spark SQL do wywoływania UDF

Teraz, po odczytaniu danych i dołączanej ML, Użyj języka Spark SQL, aby wywołać funkcję UDF, która będzie uruchamiać analizę tonacji na każdym wierszu ramki danych. Dodaj następujący kod do `Main` metody:

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

### <a name="create-predict-method"></a>Create predykcyjny () — Metoda

Dodaj następujący kod przed `Main()` metodą. Ten kod jest podobny do działania utworzonego przez konstruktora modelu w *ConsumeModel.cs*. Przeniesienie tej metody do konsoli ładuje model ładujący za każdym razem, gdy uruchamiasz aplikację.

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

## <a name="add-the-model-to-your-console-app"></a>Dodawanie modelu do aplikacji konsolowej

W Eksplorator rozwiązań Skopiuj plik *MLModel.zip* z projektu **MLSparkModelML. model** i wklej go w projekcie **MLSparkModelML. ConsoleApp** . Odwołanie jest automatycznie dodawane do *MLSparkModelML. ConsoleApp. csproj*.

## <a name="run-your-code"></a>Uruchamianie kodu

Użyj `spark-submit` do uruchomienia kodu. Przejdź do folderu głównego aplikacji konsolowej przy użyciu wiersza polecenia i uruchom następujące polecenia.

Najpierw Oczyść i Opublikuj aplikację.

```dotnetcli
dotnet clean
dotnet publish
```

Następnie przejdź do folderu publikowania aplikacji konsoli i uruchom następujące `spark-submit` polecenie. Pamiętaj, aby zaktualizować polecenie za pomocą rzeczywistej ścieżki pliku JAR Microsoft Spark.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Uzyskiwanie kodu

Ten samouczek jest podobny do kodu z [Analiza tonacji z przykładem danych Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) .

## <a name="next-steps"></a>Następne kroki

Przejdź do następnego artykułu, aby dowiedzieć się, jak wykonywać strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark.
> [!div class="nextstepaction"]
> [Samouczek: strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark](streaming.md)
