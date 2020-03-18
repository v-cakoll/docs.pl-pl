---
title: 'Samouczek: Analizowanie opinii za pomocą modelu TensorFlow'
description: W tym samouczku pokazano, jak używać wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach do witryny. Klasyfikator tonacji binarnych jest aplikacją konsoli Języka C# opracowaną przy użyciu programu Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241120"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Samouczek: Analizowanie opinii o filmach przy użyciu wstępnie przeszkolonego modelu TensorFlow w ML.NET

W tym samouczku pokazano, jak używać wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach do witryny. Klasyfikator tonacji binarnych jest aplikacją konsoli Języka C# opracowaną przy użyciu programu Visual Studio.

Model TensorFlow używany w tym samouczku został przeszkolony przy użyciu recenzji filmów z bazy danych IMDB. Po zakończeniu tworzenia aplikacji, będzie można dostarczyć tekst przeglądu filmu i aplikacja powie, czy przegląd ma pozytywne lub negatywne uczucia.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Załaduj wstępnie przeszkolony model TensorFlow
> * Przekształcaj tekst komentarza strony internetowej w funkcje odpowiednie dla modelu
> * Użyj modelu, aby dokonać przewidywania

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

## <a name="setup"></a>Konfiguracja

### <a name="create-the-application"></a>Tworzenie aplikacji

1. Utwórz **aplikację .NET Core Console** o nazwie "TextClassificationTF".

2. Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.

3. Zainstaluj **pakiet Microsoft.ML NuGet:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj.** Wyszukaj **Microsoft.ML**wybierz odpowiedni pakiet, a następnie wybierz przycisk **Zainstaluj.** Kontynuuj instalację, zgadzając się na warunki licencyjne dla wybranego pakietu. Powtórz te kroki dla **microsoft.ML.TensorFlow** i **SciSharp.TensorFlow.Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Dodawanie modelu TensorFlow do projektu

> [!NOTE]
> Model tego samouczka pochodzi z repotentu [github dotnet/machinelearning-testdata.](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) Model jest w formacie TensorFlow SavedModel.

1. Pobierz [sentiment_model plik zip](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)i rozpakuj.

    Plik zip zawiera:

    * `saved_model.pb`: sam model TensorFlow. Model przyjmuje tablicę całkowitą o stałej długości (rozmiar 600) funkcji reprezentujących tekst w ciągu przeglądu IMDB i generuje dwa prawdopodobieństwa, które sumują się do 1: prawdopodobieństwo, że przegląd wejściowy ma pozytywne nastawienie i prawdopodobieństwo, że przegląd wejściowy ma negatywnych nastrojów.
    * `imdb_word_index.csv`: mapowanie z poszczególnych wyrazów do wartości całkowitej. Mapowanie służy do generowania funkcji wejściowych dla modelu TensorFlow.

2. Skopiuj zawartość `sentiment_model` najbardziej wewnętrznego katalogu `sentiment_model` do katalogu projektu *TextClassificationTF.* Ten katalog zawiera model i dodatkowe pliki pomocy technicznej potrzebne w tym samouczku, jak pokazano na poniższym obrazku:

   ![sentiment_model zawartość katalogu](./media/text-classification-tf/sentiment-model-files.png)

3. W Eksploratorze rozwiązań kliknij `sentiment_model` prawym przyciskiem myszy każdy z plików w katalogu i podkatalogu i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

### <a name="add-using-statements-and-global-variables"></a>Dodawanie za pomocą instrukcji i zmiennych globalnych

1. Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Utwórz dwie zmienne globalne `Main` tuż nad metodą przechowywania zapisanej ścieżki pliku modelu oraz długość wektora operacji.

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`jest ścieżką pliku uczonego modelu.
    * `FeatureLength`jest długością tablicy operacji liczby całkowitej, której oczekuje model.

### <a name="model-the-data"></a>Modelowanie danych

Recenzje filmów są tekstem w formie dowolnych. Aplikacja konwertuje tekst do formatu wejściowego oczekiwanego przez model w wielu dyskretnych etapach.

Pierwszym z nich jest podzielenie tekstu na oddzielne wyrazy i użycie dostarczonego pliku mapowania do mapowania każdego wyrazu na kodowanie całkowitej. Wynikiem tej transformacji jest tablica całkowita o zmiennej długości o długości odpowiadającej liczbie wyrazów w zdaniu.

|Właściwość| Wartość|Typ|
|-------------|-----------------------|------|
|ReviewText (Tekst recenzji)|ten film jest naprawdę dobry|ciąg|
|Funkcje variablelengthFeatures|14,22,9,66,78,... |int[]|

Tablica operacji o zmiennej długości jest następnie zmieniana na stałą długość 600. Jest to długość, że model TensorFlow oczekuje.

|Właściwość| Wartość|Typ|
|-------------|-----------------------|------|
|ReviewText (Tekst recenzji)|ten film jest naprawdę dobry|ciąg|
|Funkcje variablelengthFeatures|14,22,9,66,78,... |int[]|
|Funkcje|14,22,9,66,78,... |int[600]|

1. Utwórz klasę dla danych wejściowych, po metodzie: `Main`

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    Klasa danych wejściowych, `MovieReview` `string` ma komentarze`ReviewText`dla użytkowników ( ).

1. Utwórz klasę dla operacji o `Main` zmiennej długości, po metodzie:

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    Właściwość `VariableLengthFeatures` ma [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) atrybut, aby wyznaczyć go jako wektor.  Wszystkie elementy wektorowe muszą być tego samego typu. W zestawach danych z dużą liczbą kolumn ładowanie wielu kolumn jako pojedynczego wektora zmniejsza liczbę przebiegów danych po zastosowaniu przekształceń danych.

    Ta klasa jest `ResizeFeatures` używana w akcji. Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania, które kolumny w DataView mogą służyć jako _dane wejściowe_ do akcji mapowania niestandardowego.

1. Utwórz klasę dla operacji o `Main` stałej długości, po metodzie:

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    Ta klasa jest `ResizeFeatures` używana w akcji. Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania, które kolumny w DataView mogą służyć jako _dane wyjściowe_ akcji mapowania niestandardowego.

    Należy zauważyć, że `Features` nazwa właściwości jest określana przez model TensorFlow. Nie można zmienić tej nazwy właściwości.

1. Utwórz klasę dla przewidywania `Main` po metodzie:

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction`jest klasa przewidywania używane po treningu modelu. `MovieReviewSentimentPrediction`ma pojedynczą `float` `Prediction`tablicę `VectorType` ( ) i atrybut.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Tworzenie funkcji MLContext, wyszukiwania i akcji w celu zmiany rozmiaru obiektów

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET. Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

1. Zamień `Console.WriteLine("Hello World!")` wiersz `Main` w metodzie na następujący kod, aby zadeklarować i zainicjować zmienną mlContext:

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Utwórz słownik do kodowania wyrazów jako liczb [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) całkowitych za pomocą metody ładowania danych mapowania z pliku, jak widać w poniższej tabeli:

    |Word     |Indeks    |
    |---------|---------|
    |Dzieci     |  362    |
    |chcesz     |  181    |
    |Nieodpowiednim    |  355    |
    |effects  |  302    |
    |Uczucie  |  547    |

    Dodaj poniższy kod, aby utworzyć mapę odzewu:

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. Dodaj `Action` rozmiar tablicy całkowitej wyrazu o zmiennej długości do tablicy całkowitej o stałym rozmiarze, z kolejnymi wierszami kodu:

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Załaduj wstępnie przeszkolony model TensorFlow

1. Dodaj kod, aby załadować model TensorFlow:

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    Po załadowaniu modelu można wyodrębnić jego schemat danych wejściowych i wyjściowych. Schemy są wyświetlane tylko dla zainteresowania i uczenia się. Nie potrzebujesz tego kodu do działania aplikacji końcowej:

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    Schemat wejściowy jest tablicą o stałej długości wyrazów zakodowanych całkowitą. Schemat danych wyjściowych jest zmienną tablicą prawdopodobieństwa wskazującą, czy sentyment recenzji jest ujemny, czy dodatni. Wartości te sumują się do 1, ponieważ prawdopodobieństwo pozytywnego jest uzupełnieniem prawdopodobieństwa, że sentyment jest ujemny.

## <a name="create-the-mlnet-pipeline"></a>Tworzenie potoku ML.NET

1. Utwórz potok i podziel tekst wejściowy na słowa za pomocą transformacji [TokenizeIntoWords,](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) aby podzielić tekst na słowa jako następny wiersz kodu:

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   Transformacja [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) używa spacji do analizowania tekstu/ciągu w słowa. Tworzy nową kolumnę i dzieli każdy ciąg wejściowy na wektor podciągów na podstawie separatora zdefiniowanego przez użytkownika.

1. Mapowanie wyrazów na ich kodowanie liczby całkowitej za pomocą tabeli odzewów, które zadeklarowano powyżej:

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. Zmień rozmiar kodowania liczb całkowitych o zmiennej długości na kodowanie o stałej długości wymagane przez model:

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. Sklasyfikować dane wejściowe z załadowanym modelem TensorFlow:

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    Wyjście modelu TensorFlow `Prediction/Softmax`nosi nazwę . Należy zauważyć, `Prediction/Softmax` że nazwa jest określana przez model TensorFlow. Nie można zmienić tej nazwy.

1. Utwórz nową kolumnę dla przewidywania danych wyjściowych:

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    Należy skopiować `Prediction/Softmax` kolumnę do jednej z nazwą, która może być używana `Prediction`jako właściwość w klasie C#: . Znak `/` nie jest dozwolone w nazwie właściwości Języka C#.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Tworzenie modelu ML.NET z potoku

1. Dodaj kod, aby utworzyć model z potoku:

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    Model ML.NET jest tworzony z łańcucha estymatorów w `Fit` potoku przez wywołanie metody. W takim przypadku nie są dopasowane żadnych danych do utworzenia modelu, jak model TensorFlow został już wcześniej przeszkolony. Dostarczamy obiekt pustego widoku danych, `Fit` aby spełnić wymagania metody.

## <a name="use-the-model-to-make-a-prediction"></a>Użyj modelu, aby dokonać przewidywania

1. Dodaj `PredictSentiment` metodę poniżej `Main` metody:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Dodaj następujący kod, `PredictionEngine` aby utworzyć jako `PredictSentiment()` pierwszy wiersz w metodzie:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

1. Dodaj komentarz, aby przetestować przewidywanie `Predict()` uczonego modelu `MovieReview`w metodzie, tworząc wystąpienie:

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. Przekaż dane komentarza testowego do dodawania `Prediction Engine` kolejnych `PredictSentiment()` wierszy kodu w metodzie:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie dla pojedynczego wiersza danych:

    |Właściwość| Wartość|Typ|
    |-------------|-----------------------|------|
    |Prediction (Prognoza)|[0.5459937, 0.454006255]|pływak[]|

1. Wyświetl przewidywanie tonacji przy użyciu następującego kodu:

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. Dodaj wywołanie `PredictSentiment` na końcu `Main` metody:

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Wyniki

Tworzenie i uruchamianie aplikacji.

Wyniki powinny być podobne do poniższych. Podczas przetwarzania są wyświetlane komunikaty. Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania. Te komunikaty zostały usunięte z następujących wyników dla jasności.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego do klasyfikowania i przewidywania tonacji `TensorFlow` wiadomości przez ponowne użycie wstępnie uczonego modelu w ML.NET.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Załaduj wstępnie przeszkolony model TensorFlow
> * Przekształcaj tekst komentarza strony internetowej w funkcje odpowiednie dla modelu
> * Użyj modelu, aby dokonać przewidywania
