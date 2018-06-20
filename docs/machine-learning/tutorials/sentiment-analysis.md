---
title: Użyj ML.NET w przypadku klasyfikacji binarnej analizy wskaźniki nastrojów klientów
description: Dowiedzieć się, jak za pomocą ML.NET w scenariuszu klasyfikacji binarnej można określić sposób użycia prognozowania wskaźniki nastrojów klientów podjęcie odpowiednich działań.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 85fb55582d891c67f172effa4952f15ac5604d50
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207667"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Samouczek: Użyj ML.NET w przypadku klasyfikacji binarnej analizy wskaźniki nastrojów klientów

> [!NOTE]
> W tym temacie odnosi się do ML.NET, który jest obecnie w wersji zapoznawczej, i materiały może być może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Ten samouczek przykładowy przedstawiono przy użyciu ML.NET utworzenie klasyfikatora programu wskaźniki nastrojów klientów za pomocą aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2017 r.

Z tego samouczka, dowiesz się, jak:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie learning odpowiednie maszyny
> * Przygotowywanie danych
> * Tworzenie potoku learning
> * Klasyfikator obciążenia
> * Uczenie modelu
> * Ocena modelu z innego zestawu danych
> * Wyniki testu danych z modelu prognozowania

## <a name="sentiment-analysis-sample-overview"></a>Omówienie przykładowej analizy wskaźniki nastrojów klientów

Próbka jest aplikacji konsoli, która używa ML.NET do nauczenia modelu, który klasyfikowanych i prognozuje wskaźniki nastrojów klientów jako dodatnią lub ujemną. Oblicza model z drugiego zestawu danych do analizy jakości. Zestawy danych wskaźniki nastrojów klientów pochodzą z projektu WikiDetox.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15,6 lub nowszym](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany.

* [Wikipedia detox wiersz danych karta rozdzielonych plików (wikiPedia-detox-250-wiersza data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Karta testu linii detox Wikipedia rozdzielonych plików (wikipedia-detox-250-wiersza test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

## <a name="machine-learning-workflow"></a>Machine learning w przepływie pracy

W tym samouczku wykonuje przepływ pracy, który umożliwia procesu przenieść w sposób uporządkowany uczenia maszynowego.

Fazy przepływu pracy są następujące:

1. **Zrozumieć**
2. **Pozyskiwanie danych**
3. **Przetwarzanie wstępne danych i inżynieria**
4. **Szkolenie i prognozowania modelu**
5. **Ocena modelu**
6. **Operationalization modelu**

### <a name="understand-the-problem"></a>Omówienie problemu

Należy najpierw zrozumieć, dlatego mogą być dzielone do części, które obsługują tworzenie i uczenie modelu. Przerywanie problem w dół do prognozowania i ocena wyników.

Ten problem, w tym samouczku jest zrozumienie, przychodzących witryny sieci Web komentarz wskaźniki nastrojów klientów podjęcie odpowiednich działań.

Problem można podzielić tekstu wskaźniki nastrojów klientów i wskaźniki nastrojów klientów wartość żądane dane do uczenia modelu o i wartość przewidywane wskaźniki nastrojów klientów, które można ocenić i następnie użyć pod względem.

Następnie należy **określić** wskaźniki nastrojów klientów, która ułatwia wybór zadania uczenia maszynowego.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie learning odpowiednie maszyny

Z tym problemem znasz następujące fakty:

Uczenie danych: komentarze witryny sieci Web może być liczbą dodatnią lub ujemną (**wskaźniki nastrojów klientów**).
Przewidywanie **wskaźniki nastrojów klientów** nowego komentarza witryny sieci Web, dodatnie lub ujemne, takich jak w poniższych przykładach:

* Unikaj umieszczania Dodawanie żadnego znaczenia do Wikipedia.
* Jest najlepsza i artykułu należy oznacza, że.

Zadanie klasyfikacji maszyny learning jest najbardziej odpowiednie dla tego scenariusza.

### <a name="about-the-classification-task"></a>Zadania klasyfikacji

Klasyfikacja jest zadanie uczenia maszynowego, które używa danych do **określić** kategorii, typu lub klasy elementu lub wiersza danych. Na przykład można użyć klasyfikacji:

* Zidentyfikuj wskaźniki nastrojów klientów jako dodatnią lub ujemną.
* Klasyfikowanie poczty e-mail jako wiadomości-śmieci, wiadomości-śmieci lub dobra.
* Ustal, czy pacjenta laboratorium próbki jest cancerous.
* Klasyfikowanie klientów przez ich większego ukierunkowania odpowiedzieć kampanii sprzedaży.

Zadania klasyfikacji są często jednym z następujących typów:

* Dane binarne: A i B.
* Multiklasa: wiele kategorii, które można przewidzieć przy użyciu pojedynczego modelu.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsoli

1. Otwórz program Visual Studio 2017 r. Wybierz **pliku** > **nowy** > **projektu** na pasku menu. W *nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **.NET Core** węzła. Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu. W **nazwa** polu tekstowym, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane" i naciśnij Enter.

3. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz polecenie "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz z listy tego pakietu i wybierz **zainstalować** przycisku. Wybierz **OK** znajdującego się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdującego się na **akceptacji licencji** okna dialogowego jeśli użytkownik Akceptuję warunki licencji dla pakietów na liście.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [WikiPedia detox-250-wiersza data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) i [wikipedia-detox-250-wiersza test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) danych ustawia i zapisywanie ich *danych* folder utworzony wcześniej. Modelu uczenia maszynowego przygotowuje pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładny jest modelem.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*.tsv pliki i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość **Kopiuj do katalogu wyjściowego** do **zawsze**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i zdefiniować ścieżki

Dodaj następujące dodatkowe `using` instrukcje na początku *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Musisz utworzyć trzy zmienne globalne, aby mógł pomieścić ścieżka ostatnio pobranych plików:

* `_dataPath` zawiera ścieżkę do zestawu danych używany do uczenia modelu.
* `_testDataPath` zawiera ścieżkę do zestawu danych używane do oceny modelu.
* `_modelPath` zawiera ścieżkę, w której jest zapisywany trenowanego modelu.

Dodaj następujący kod do prawej wiersz powyżej `Main` metodę, aby określić ostatnio pobranych plików:

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

Musisz utworzyć niektórych klas dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *SentimentData.cs*. Następnie wybierz opcję **Dodaj** przycisku.

    *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące `using` instrukcji na początku *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `SentimentData` i `SentimentPrediction`, do *SentimentData.cs* pliku:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` Klasa zestawu danych wejściowych i ma `float` (`Sentiment`) mający wartość wskaźniki nastrojów klientów dodatnie lub ujemne, a ciąg komentarza (`SentimentText`). Oba pola mają `Column` atrybuty dołączone do nich. Ten atrybut Opisuje kolejność każdego pola w pliku danych, który jest `Label` pola. `SentimentPrediction` Klasa służy do prognozowania po zakończenia uczenia modelu. Składa się z jednego typu boolean (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu. `Label` Jest używany do tworzenia i nauczenia modelu, a także używane z drugiego zestawu danych do oceny modelu. `PredictedLabel` Jest używany podczas prognozowania i oceny. Do oceny są używane dane wejściowe dane szkoleniowe, przewidywane wartości i modelu.

W *Program.cs* Zmień `Main` podpis metody zastępując `void` z `async Task`, jak w poniższym przykładzie:

```csharp
static async Task Main(string[] args) 
{

}
```

Możesz dodać `async` do `Main` z <xref:System.Threading.Tasks.Task> typ zwracany, ponieważ są zapisywane modelu w pliku zip później, a program musi czekać, aż do zakończenia tego zadania zewnętrznego.

> [!NOTE]
> *Async głównego* metoda pozwala na użycie `await` w Twojej `Main` metody. Aby uzyskać więcej informacji, zobacz [async głównego](../../../docs/csharp/programming-guide/main-and-command-args/index.md) w Podręczniku programowania C#.

Zastąp `Console.WriteLine("Hello World!")` wiersza w następującym kodem `Main` metody:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

`Train` Metoda wykonuje następujące zadania:

* Ładuje lub wysyła strumień danych.
* Przetwarza wstępnie i featurizes danych.
* Przygotowuje modelu.
* Prognozuje wskaźniki nastrojów klientów oparte na danych testowych.

Utwórz `Train` metody tuż po `Main` metodę, przy użyciu następującego kodu:

```csharp
public static PredictionModel<SentimentData, SentimentPrediction> Train()
{

}
```

## <a name="ingest-the-data"></a>Pozyskiwanie danych

Inicjuje nowe wystąpienie klasy <xref:Microsoft.ML.LearningPipeline> zawierające ładowanie danych, przetwarzanie danych/featurization i modelu. Dodaj następujący kod jako pierwszy wiersz `Train` metody:

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<xref:Microsoft.ML.Data.TextLoader> Obiektu jest pierwszą częścią potoku i ładuje dane szkoleniowe pliku.

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>Przetwarzanie wstępne danych i inżynieria

Przetwarzanie wstępne i czyszczenia danych są ważne zadania, które występuje, zanim będzie można skutecznie użyć zestawu danych do uczenia maszynowego. Dane pierwotne jest często zakłócenia i zawodnych i może brakować wartości. Przy użyciu danych bez tych zadań modelowania może wygenerować błędne wyniki. ML. Potoki przekształcenia w sieci umożliwiają utworzenie niestandardowego zestawu transformacje, które są stosowane do danych przed szkolenia lub testowania. Główny cel przekształcenia dotyczy featurization danych. Potok przekształcenia korzyści jest to, że po definicji potoku przekształcania, zapisać potoku, aby zastosować go do testowania danych.

Zastosuj <xref:Microsoft.ML.Transforms.TextFeaturizer> można przekonwertować `SentimentText` kolumny do [liczbowych wektor](../resources/glossary.md#numerical-feature-vector) o nazwie `Features` używane przez algorytm uczenia maszynowego. Jest to krok przetwarzania wstępnego featurization. Przy użyciu dodatkowych składników dostępnych w ML.NET umożliwiają lepsze wyniki z modelu. Dodaj `TextFeaturizer` do potoku jako następnym wierszu kodu:

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>Wybierz algorytm uczenia

<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Obiekt jest uczeń drzewa decyzyjne, będzie używany w tym potoku. Podobnie jak w kroku featurization wypróbować różne uczących dostępne w ML.NET i zmiany ich parametry prowadzi do różne wyniki. Dostrajanie, można ustawić [hyperparameters](../resources/glossary.md#hyperparameter) jak <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, i <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>. Te hyperparameters są ustawiane przed niczego wpływa na modelu i są specyficzne dla modelu. Są używane do dostrajania drzewo decyzyjne dotyczące wydajności, więc większe wartości może niekorzystnie wpłynąć na wydajność.

Dodaj następujący kod do `Train` metody:

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>Uczenie modelu

Nauczenia modelu, <xref:Microsoft.ML.PredictionModel%602>zgodnie zestawu danych, który został załadowany i przekształcenia. `pipeline.Train<SentimentData, SentimentPrediction>()` przygotowuje potoku (ładuje dane, pociągu featurizer i uczeń). Eksperyment nie została wykonana, dopóki nie dzieje.

Dodaj następujący kod do `Train` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Zapisz i wróć uczenia modelu do użycia na potrzeby oceny

W tym momencie masz modelu, który można zintegrować wszelkie istniejące lub nowe aplikacje .NET. Aby zapisać modelu w pliku zip, przed zwróceniem, Dodaj następujący kod do następnego wiersza w `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

Zwraca model na końcu `Train` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Teraz, utworzeniu i nauczyć model, należy go obliczyć z innego zestawu danych dla jakości i sprawdzania poprawności. W `Evaluate` metoda, modelu, który został utworzony w `Train` jest przekazywany do obliczenia. Utwórz `Evaluate` metody tuż po `Train`, jak w poniższym kodzie:

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Evaluate` Metoda wykonuje następujące zadania:

* Załadowanie zestawu danych testowych.
* Tworzy ewaluatora binarnego.
* Oblicza model oraz tworzenie metryk.
* Przedstawia metryki.

Dodaj wywołanie do nowej metody z `Main` metoda, bezpośrednio pod `Train` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<xref:Microsoft.ML.Data.TextLoader> Klasy ładuje nowego zestawu danych testowych z tego samego schematu. Należy ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości. Dodaj następujący kod do `Evaluate` metody:

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Obiektu oblicza metryki jakości `PredictionModel` przy użyciu określonego zestawu danych. Aby wyświetlić te metryki, Dodaj ewaluatora w następnym wierszu `Evaluate` metodę z następującym kodem:

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<xref:Microsoft.ML.Models.BinaryClassificationMetrics> Zawiera ogólną metryki obliczone przez oceniających klasyfikacji binarnej. Aby wyświetlić tych zasobów w celu określenia jakości modelu, należy uzyskać pierwszy metryki. Dodaj następujący kod:

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryki Weryfikacja modelu

Do wyświetlania metryk, udostępnić wyniki, a następnie działają na nich należy użyć poniższego kodu:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>Wyniki testu danych z modelu prognozowania

Utwórz `Predict` metody tuż po `Evaluate` metodę, przy użyciu następującego kodu:

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Predict` Metoda wykonuje następujące zadania:

* Tworzy danych testowych.
* Prognozuje wskaźniki nastrojów klientów oparte na danych testowych.
* Łączy testowania danych i prognoz dla raportowania.
* Wyświetla wyniki przewidywane.

Dodaj wywołanie do nowej metody z `Main` metoda, bezpośrednio pod `Evaluate` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

Dodaj niektóre komentarze do testowania prognoz uczonego modelu w `Predict` metody:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

Teraz, gdy masz modelu należy go używać, aby przewidzieć dodatnie lub ujemne wskaźniki nastrojów klientów użycia danych komentarz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metody. Aby uzyskać prognozowania, należy użyć `Predict` na nowych danych. Należy pamiętać, że danych wejściowych jest ciągiem i model zawiera featurization. Potoku sieci jest w synchronizacji podczas uczenia i prognozowania. Nie trzeba napisać kod przetwarzania wstępnego featurization specjalnie z myślą o prognoz i tego samego interfejsu API zajmuje się zarówno partii i jednorazowego prognoz.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Model operationalization: prognozowania

Wyświetl `SentimentText` oraz odpowiednie wskaźniki nastrojów klientów prognozowania celu mają wyniki i odpowiednio działają na nich. Jest to operationalization używanie zwrócone dane jako części zasady operacyjne. Utwórz nagłówek dla wyników z następującym <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

Przed wyświetleniem wyniki przewidywane, łączyć wskaźniki nastrojów klientów i prognozowanie ze sobą, aby wyświetlić oryginalne komentarz z jego przewidywane wskaźniki nastrojów klientów. Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, a więc Dodaj ten kod obok:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

Teraz, po połączeniu `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

Ponieważ wywnioskować nazwy elementu krotki to 7.0 C# jest nową funkcją w C# 7.1 i wersję językową domyślny projekt, musisz zmienić wersję języka C# 7.1 lub nowszej.
W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** i wybierz **zaawansowane** przycisku. Na liście rozwijanej wybierz **C# 7.1** (lub nowszej wersji). Wybierz **OK** przycisku.

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następującego. Jak przetwarza potoku, wyświetla komunikaty. Mogą pojawić się ostrzeżenia lub komunikaty przetwarzania. Te zostały usunięte z następującymi wynikami dla uzyskania przejrzystości.

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

Gratulacje! Teraz został pomyślnie skompilowany modelu uczenia maszynowego, klasyfikowania i prognozowanie wiadomości wskaźniki nastrojów klientów. Kod źródłowy można znaleźć w tym samouczku w [dotnet/przykłady](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie learning odpowiednie maszyny
> * Przygotowywanie danych
> * Tworzenie potoku learning
> * Klasyfikator obciążenia
> * Uczenie modelu
> * Ocena modelu z innego zestawu danych
> * Wyniki testu danych z modelu prognozowania

Przejdź do następnego samouczkiem, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Prognoza taryfy taksówki](taxi-fare.md)
