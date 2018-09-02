---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 57ade448f5773bee3474cb46bec8ad33e3afbee3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391068"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Samouczek: Używanie strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Ten przykładowy samouczek przedstawia tworzenie klasyfikatora tonacji za pomocą aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2017 przy użyciu strukturze ML.NET.

W tym samouczku dowiesz się, jak:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie uczenia odpowiedniej maszyny
> * Przygotowywanie danych
> * Tworzenie potoku uczenia
> * Ładowanie klasyfikatora
> * Uczenie modelu
> * Ocena modelu za pomocą innego zestawu danych
> * Przewidywanie wyników danych testów przy użyciu modelu

## <a name="sentiment-analysis-sample-overview"></a>Omówienie przykładowych analizy tonacji

Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje wskaźniki nastrojów klientów, jak dodatnie lub ujemne. Oblicza model z drugiego zestawu danych do analizy jakości dostawców. Zestawy danych wskaźniki nastrojów klientów są od projektu WikiDetox.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

* [Wikipedia detox wiersza danych tabulacji pliku (wikiPedia-detox-250-linia data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Wikipedia detox wiersza testu tabulacji pliku (wikipedia-detox-250-linia test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

## <a name="machine-learning-workflow"></a>Maszyny uczenie się przepływu pracy

W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.

Fazy przepływu pracy są następujące:

1. **Omówienie problemu**
2. **Pozyskiwanie danych**
3. **Wstępne przetwarzanie danych i inżynieria funkcji**
4. **Uczenia i przewidywania modelu**
5. **Ocena modelu**
6. **Operacjonalizacja modelu**

### <a name="understand-the-problem"></a>Omówienie problemu

Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu. Przerywanie problem w dół do przewidywania i ocena wyników.

Ten problem, w tym samouczku jest zrozumienie, przychodzące tonacji komentarz witryny sieci Web podejmowanie odpowiednich działań.

Ten problem można podzielić do tonacji tekstu i wartości tonacji danych mają do nauczenia modelu, z, a wartości tonacji przewidywane, można obliczyć, a następnie za pomocą pod względem.

Następnie należy **określić** tonacji, która ułatwia wybieranie zadań uczenia maszynowego.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie uczenia odpowiedniej maszyny

W rozwiązaniu tego problemu znasz następujące fakty:

Szkolenie danych: komentarze witryny sieci Web może być dodatnia lub ujemna (**tonacji**).
Przewidywanie **tonacji** nowego komentarza witryny sieci Web, dodatnie lub ujemne, takie jak w następujących przykładach:

* Punktowanych — Dodawanie żadnego znaczenia do Wikipedia.
* Jest on najlepsze, a artykuł powinien oznacza, że.

Zadania uczenia maszyny klasyfikacji najlepiej nadaje się dla tego scenariusza.

### <a name="about-the-classification-task"></a>O zadaniu klasyfikacji

Klasyfikacja jest zadanie uczenia maszynowego, które są używane dane do **określić** kategorii, typ lub klasa elementu lub wiersza danych. Na przykład można użyć klasyfikacji:

* Zidentyfikuj tonacji jako dodatnia lub ujemna.
* Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.
* Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.
* Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.

Klasyfikacja zadań są często jednym z następujących typów:

* Plik binarny: A i B.
* Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsoli

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W *nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

3. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [WikiPedia detox-250-linia data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) i [wikipedia-detox-250-linia test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder. Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowania ścieżek

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Musisz utworzyć trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki:

* `_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.
* `_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.
* `_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku.

    *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` Klasa wejściowy zestaw danych i ma `float` (`Sentiment`) zawierający wartości tonacji dodatnie lub ujemne, a ciąg komentarza (`SentimentText`). Oba pola mają `Column` atrybuty dołączonych do nich. Ten atrybut wykonywania działań Opisuje kolejność każdego pola w pliku danych, i które `Label` pola. `SentimentPrediction` Klasa służy do prognozowania po wyszkoliła modelu. Ma ona pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu. `Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu. `PredictedLabel` Używany podczas prognoz i oceny. W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.

W *Program.cs* pliku, zmień `Main` podpis metody, zastępując `void` z `async Task`, jak w poniższym przykładzie:

```csharp
static async Task Main(string[] args) 
{

}
```

Możesz dodać `async` do `Main` z <xref:System.Threading.Tasks.Task> typ zwracany, ponieważ model są zapisywane później do pliku zip, a program musi czekać, aż do zakończenia tego zadania zewnętrznego.

> [!NOTE]
> *Asynchroniczna funkcja main* metoda umożliwia użycie `await` w swojej `Main` metody. Aby uzyskać więcej informacji, zobacz [asynchroniczna funkcja main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) w Podręczniku programowania C#.

Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

`Train` Metoda wykonuje następujące zadania:

* Ładuje lub pozyskuje dane.
* Wstępnie przetwarza i featurizes danych.
* Szkolenie modeli modelu.
* Prognozuje tonacji na podstawie danych testowych.

Tworzenie `Train` metody tuż za `Main` metody, używając następującego kodu:

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a>Pozyskiwanie danych

Inicjuje nowe wystąpienie klasy <xref:Microsoft.ML.LearningPipeline> zawierające ładowania danych, przetwarzanie danych/cechowania i modelu. Dodaj następujący kod jako pierwsza linia `Train` metody:

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<xref:Microsoft.ML.Data.TextLoader> Obiektu jest pierwszą częścią potoku i ładuje plik danych szkoleniowych.

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>Wstępne przetwarzanie danych i inżynieria funkcji

Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego. Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości. Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników. UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET umożliwiają tworzą zbiór niestandardowych przekształceń, które są stosowane do danych przed szkolenie i testowanie. Przekształcenia głównym celem jest dla cechowania danych. Potok przekształcania zaletą jest to, że po definicji potoku transformacji, Zapisz potoku, aby zastosować dane testowe.

Zastosuj <xref:Microsoft.ML.Transforms.TextFeaturizer> można przekonwertować `SentimentText` kolumny na [liczbowych wektor](../resources/glossary.md#numerical-feature-vector) o nazwie `Features` używane przez algorytm uczenia maszynowego. Jest to krok przetwarzania wstępnego cechowania. Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu. Dodaj `TextFeaturizer` do potoku jako następnego wiersza kodu:

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Obiekt jest uczeń drzewa decyzyjne, zostanie użyty w tym potoku. Podobnie jak w kroku cechowania wypróbowania różnych uczestników kursów, które są dostępne w strukturze ML.NET i zmienianie ich parametrów prowadzi do różne wyniki. W przypadku dostosowywania, można ustawić [hiperparametrów](../resources/glossary.md#hyperparameter) takich jak <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, i <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>. Te hiperparametrów są ustawiane przed wszystko wpływa na modelu i są specyficzne dla modelu. Służą one do dostrojenia drzewa decyzyjnego dla wydajności, więc większe wartości może negatywnie wpłynąć na wydajność.

Dodaj następujący kod do `Train` metody:

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>Uczenie modelu

Uczenie modelu, <xref:Microsoft.ML.PredictionModel%602>zgodnie z zestawu danych, który został załadowany i przekształcone. `pipeline.Train<SentimentData, SentimentPrediction>()` szkolenie modeli potoku (służy do ładowania danych, pociągów featurized i uczeń). Eksperyment nie jest wykonywane, dopóki nie dzieje.

Dodaj następujący kod do `Train` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Zapisz i wróć model jest uczony na potrzeby oceny

W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET. Aby zapisać swój model do pliku zip, przed zwróceniem, Dodaj następujący kod do następnego wiersza w `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

Zwraca model na końcu `Train` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności. W `Evaluate` metody, model utworzony w `Train` jest przekazywany do obliczenia. Tworzenie `Evaluate` metody tuż za `Train`, jak w poniższym kodzie:

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Evaluate` Metoda wykonuje następujące zadania:

* Ładuje zestawy danych testowych.
* Tworzy ewaluatora binarnego.
* Oblicza model oraz tworzenie metryk.
* Przedstawia metryki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<xref:Microsoft.ML.Data.TextLoader> Klasy ładuje nowego zestawu danych testowych za pomocą tego samego schematu. Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości. Dodaj następujący kod do `Evaluate` metody:

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Obiektu oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych. Aby wyświetlić te metryki, należy dodać ewaluatora w następnym wierszu `Evaluate` metoda następującym kodem:

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<xref:Microsoft.ML.Models.BinaryClassificationMetrics> Zawiera ogólne metryki obliczone przez ewaluatory klasyfikacji binarnej. Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki. Dodaj następujący kod:

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryki dotyczące weryfikacji modelu

Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>Przewidywanie wyników danych testów przy użyciu modelu

Tworzenie `Predict` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Predict` Metoda wykonuje następujące zadania:

* Tworzy dane testowe.
* Prognozuje tonacji na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `Predict` metody:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

Teraz, gdy model, możesz go używać, aby przewidzieć dodatnie lub ujemne tonacji przy użyciu danych komentarz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metody. Aby uzyskać prognozę, użyj `Predict` na nowych danych. Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Model operacjonalizacji: prognoz

Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich. Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych. Utwórz nagłówek dla wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

Przed wyświetleniem wyników, Połącz opinii i prognozowania ze sobą, aby zobaczyć, oryginalnym komentarzem z jego przewidywane wskaźniki nastrojów klientów. Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, obok więc Dodaj ten kod:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

Teraz, gdy zostały połączone `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

Ponieważ wywnioskować, że jest nową funkcją w C# 7.1 i wersją języka domyślnego projektu języka C# 7.0 nazwami elementów krotki, musisz zmienić wersję języka C# 7.1 lub nowszej.
Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku. Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja). Wybierz **OK** przycisku.

## <a name="results"></a>wyniki

Wyniki powinny być podobne do następujących. Ponieważ przetwarza potoku, wyświetla komunikaty. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te zostały usunięte z następujących wyników dla przejrzystości.

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

Gratulacje! Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie uczenia odpowiedniej maszyny
> * Przygotowywanie danych
> * Tworzenie potoku uczenia
> * Ładowanie klasyfikatora
> * Uczenie modelu
> * Ocena modelu za pomocą innego zestawu danych
> * Przewidywanie wyników danych testów przy użyciu modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Taksówek taryfy predykcyjne](taxi-fare.md)
