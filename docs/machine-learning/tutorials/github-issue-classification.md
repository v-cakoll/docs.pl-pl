---
title: 'Samouczek: Kategoryzacja problemów z pomocą techniczną — Klasyfikacja wieloklasowa'
description: Dowiedz się, jak używać ML.NET w scenariuszu klasyfikacji wieloklasowej do klasyfikowania problemów z usługi GitHub w celu przypisywania ich do danego obszaru.
ms.date: 07/31/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 1eb56465bb56906df25c3a094126f2496bef684e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929226"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a>Samouczek: Klasyfikowanie problemów z pomocą techniczną przy użyciu klasyfikacji wieloklasowej z .NET ML

Ten przykładowy samouczek ilustruje użycie ML.NET do utworzenia klasyfikatora problemu w usłudze GitHub w celu uczenia modelu, który klasyfikuje i przewidywalnuje etykietę obszaru dla problemu usługi GitHub za pośrednictwem aplikacji konsolowej .NET Core C# w programie Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Oceń model
> * Przewidywanie przy użyciu przeszkolonego modelu
> * Wdrażanie i przewidywanie z załadowanym modelem

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .

## <a name="prerequisites"></a>Wymagania wstępne

* [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

* [Plik rozdzielony tabulatorami problemów usługi GitHub (issues_train. tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Plik rozdzielony kart testów problemów GitHub (issues_test. tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** . W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **.NET Core** . Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "GitHubIssueClassification", a następnie wybierz przycisk **OK** .

2. Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**. Wpisz "Data" i naciśnij klawisz ENTER.

3. Utwórz katalog o nazwie *models* w projekcie, aby zapisać model:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**. Wpisz "models" i naciśnij klawisz ENTER.

4. Zainstaluj **pakiet NuGet Microsoft.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz pakiet **v 1.0.0** na liście, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz zestawy danych [issues_train. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) i Zapisz je w utworzonym wcześniej folderze *danych* . Pierwszy zestaw danych pociąga za niego model uczenia maszynowego, a drugi może służyć do oszacowania, jak dokładny jest model.

2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy z \*plików. tsv i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Utwórz trzy pola globalne do przechowywania ścieżek do ostatnio pobranych plików, a następnie zmienne globalne dla `MLContext`,`DataView`i `PredictionEngine`:

* `_trainDataPath`ma ścieżkę do zestawu danych używanego do uczenia modelu.
* `_testDataPath`ma ścieżkę do zestawu danych używanego do szacowania modelu.
* `_modelPath`ma ścieżkę, w której jest zapisywany model szkolony.
* `_mlContext`jest to element, który zawiera kontekst przetwarzania. <xref:Microsoft.ML.MLContext>
* `_trainingDataView`<xref:Microsoft.ML.IDataView> jest używany do przetwarzania zestawu danych szkoleniowych.
* `_predEngine`<xref:Microsoft.ML.PredictionEngine%602> jest używany dla pojedynczych prognoz.

Dodaj następujący kod do wiersza bezpośrednio powyżej `Main` metody, aby określić te ścieżki i inne zmienne:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Utwórz klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *GitHubIssueData.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *GitHubIssueData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `GitHubIssue` i `IssuePrediction`, do pliku *GitHubIssueData.cs* :

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`label` Jest to kolumna, która ma zostać przewidywalna. Identyfikowane `Features` są dane wejściowe, które umożliwiają modelowi przewidywalność etykiety.

Użyj [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) , aby określić indeksy kolumn źródłowych w zestawie danych.

`GitHubIssue`jest klasą wejściowego zestawu danych i zawiera <xref:System.String> następujące pola:

* Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)
* Druga kolumna `Area` (Prognoza dla szkolenia)
* Trzecia kolumna `Title` (tytuł problemu GitHub) jest pierwszym `feature` używanym do przewidywania`Area`
* czwarta kolumna `Description` jest sekundą `feature` używaną do przewidywania`Area`

`IssuePrediction`jest klasą używaną do przewidywania po przeszkoleniu modelu. Ma pojedynczy `string` (`Area`) `PredictedLabel` i`ColumnName` atrybut.  `PredictedLabel` Jest używany podczas przewidywania i oceny. W celu dokonania oceny dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model są używane.

Wszystkie operacje ML.NET są uruchamiane w klasie [MLContext](xref:Microsoft.ML.MLContext) . Inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w. `Entity Framework`

### <a name="initialize-variables-in-main"></a>Inicjuj zmienne w głównym

Zainicjuj zmienną `MLContext` `seed: 0`globalną z nowym wystąpieniem z losowym inicjatorem () dla powtarzalnych/deterministycznych wyników w wielu szkoleniach. `_mlContext`  Zamień wiersz na następujący kod `Main` w metodzie: `Console.WriteLine("Hello World!")`

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Ładowanie danych

ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznej, wydajnej metody opisywania danych tabelarycznych lub tekstowych. `IDataView`może ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dzienników).

Aby zainicjować i załadować `_trainingDataView` zmienną globalną w celu użycia jej dla potoku, należy dodać następujący kod `mlContext` po zainicjowaniu:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.

Dodaj następujący kod jako następny wiersz kodu w `Main` metodzie:

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` Metoda wykonuje następujące zadania:

* Wyodrębnia i przekształca dane.
* Zwraca potok przetwarzania.

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main` `ProcessData`

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Wyodrębnij funkcje i Przekształć dane

Aby przewidzieć etykietę obszaru usługi GitHub dla elementu `GitHubIssue`, należy użyć `Area` metody [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) do przekształcenia kolumny w kolumnę typu `Label` klucza liczbowego (format akceptowany przez algorytmy klasyfikacji) i dodać ją jako nową kolumna zestawu danych:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Następnie należy wywołać `mlContext.Transforms.Text.FeaturizeText` , który przekształca kolumny tekstu (`Title` i `Description`) do wektora liczbowego dla każdego wywoływanego `TitleFeaturized` i `DescriptionFeaturized`. Dołącz cechowania dla obu kolumn do potoku przy użyciu następującego kodu:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Ostatnim krokiem w przygotowaniu danych jest połączenie wszystkich kolumn funkcji w kolumnie **funkcje** przy użyciu metody [złączing ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) . Domyślnie algorytm uczenia przetwarza tylko funkcje z kolumny **Features** . Dołącz tę transformację do potoku przy użyciu następującego kodu:

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 Następnie Dołącz <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> do pamięci podręcznej, aby w przypadku wielokrotnego powtarzania danych za pomocą pamięci podręcznej można było uzyskać lepszą wydajność, podobnie jak w przypadku następującego kodu:

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> Aby zmniejszyć czas uczenia, użyj AppendCacheCheckpoint dla małych i średnich zestawów danych. Nie należy używać go (Usuń. AppendCacheCheckpoint ()) podczas obsługi bardzo dużych zestawów danych.

Zwróć potok na końcu `ProcessData` metody.

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Ten krok obsługuje przetwarzanie wstępne/cechowania. Korzystanie z dodatkowych składników dostępnych w programie ML.NET może umożliwić lepsze wyniki w modelu.

## <a name="build-and-train-the-model"></a>Kompilowanie i uczenie modelu

Dodaj następujące wywołanie do `BuildAndTrainModel`metody jako następny wiersz kodu `Main` w metodzie:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Metoda wykonuje następujące zadania:

* Tworzy klasę algorytmu szkoleniowego.
* Pociąga za siebie model.
* Obszar przewidywania na podstawie danych szkoleniowych.
* Zwraca model.

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main` `BuildAndTrainModel`

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Informacje o zadaniu klasyfikacji

Klasyfikacja to zadanie uczenia maszynowego, które używa danych do **określania** kategorii, typu lub klasy elementu lub wiersza danych. jest to często jeden z następujących typów:

* Plik binarny: A lub B.
* Wieloklasowe: wiele kategorii, które mogą być przewidywane przy użyciu jednego modelu.

W przypadku tego typu problemu należy użyć wieloklasowego algorytmu uczenia klasyfikacji, ponieważ przewidywanie kategorii problemu może być jedną z wielu kategorii (wiele klas), a nie tylko dwóch (binarnych).

Dołącz algorytm uczenia maszynowego do definicji transformacji danych, dodając następujący kod jako pierwszy wiersz kodu w `BuildAndTrainModel()`:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) to algorytm szkoleniowy klasyfikacji wieloklasowej. Jest on dołączany do `pipeline` i akceptuje featurized `Title` `Label` i `Description` (`Features`) oraz parametry wejściowe, aby poznać dane historyczne.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj model do `splitTrainSet` danych i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu `BuildAndTrainModel()` w metodzie:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

`Fit()`Metoda pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który pozwala na przekazywanie danych, a następnie wykonywanie prognozowania na jednym wystąpieniu. Dodaj tę wartość jako następny wiersz w `BuildAndTrainModel()` metodzie:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Przewidywanie przy użyciu przeszkolonego modelu

Dodaj problem w usłudze GitHub, aby przetestować prognozę przeszkolonego `Predict` modelu w metodzie, tworząc `GitHubIssue`wystąpienie:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) służy do prognozowania pojedynczego wiersza danych:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Korzystanie z modelu: wyniki przewidywania

Wyświetlaj `GitHubIssue` i `Area` odpowiadaj prognozie etykiet, aby udostępnić wyniki i wykonać odpowiednie działania.  Utwórz ekran dla wyników przy użyciu następującego <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwróć model przeszkolony do użycia na potrzeby oceny

Zwróć model na końcu `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Oceń model

Teraz, gdy tworzysz i przeszkolony model, musisz go oszacować z innym zestawem danych w celu zapewnienia jakości i weryfikacji. W metodzie model utworzony w `BuildAndTrainModel` jest przeszedł do oceny. `Evaluate` Utwórz metodę, tuż po `BuildAndTrainModel`, jak w poniższym kodzie: `Evaluate`

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

`Evaluate` Metoda wykonuje następujące zadania:

* Ładuje zestaw danych testowych.
* Tworzy ewaluatora wieloklasowe.
* Oblicza model i tworzy metryki.
* Wyświetla metryki.

Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio `BuildAndTrainModel` pod wywołaniem metody, przy użyciu następującego kodu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Tak jak wcześniej z zestawem danych szkoleniowych, Załaduj zestaw danych testowych, dodając następujący kod `Evaluate` do metody:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

Metoda COMPUTE [()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) oblicza metryki jakości dla modelu przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> obiekt, który zawiera metryki ogólne obliczone przez konstruktory klasyfikacji wieloklasowej.
Aby wyświetlić metryki w celu określenia jakości modelu, należy je najpierw pobrać.
Zwróć uwagę na użycie metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) zmiennej globalnej uczenia `_trainedModel` maszynowego ( [ITransformer](xref:Microsoft.ML.ITransformer)) w celu wejścia do funkcji i zwracania prognoz. Dodaj następujący kod do `Evaluate` metody w następnym wierszu:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Następujące metryki są oceniane dla klasyfikacji wieloklasowej:

* Mikro-dokładność — każda para klasy próbek bezproblemowo przyczynia się do metryki dokładności.  Potrzebujesz Micro dokładności, jak najbliżej 1.

* Dokładność makra — każda klasa przyczynia się równo do metryki dokładności. Klasy mniejszości są traktowane jako takie same wagi jak większe klasy. Dokładność makra powinna być jak najbliżej 1, jak to możliwe.

* Dziennik — utrata — zobacz [Dziennik strat](../resources/glossary.md#log-loss). Utrata dziennika powinna być jak najbliżej zera.

* Redukcja utraconych plików dziennika — zakresy z [-inf, 100], gdzie 100 są idealnym przewidywaniam, a wartość 0 oznacza przewidywania. Zmniejszenie liczby utraconych dzienników może być zbliżone do zera, jak to możliwe.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk na potrzeby walidacji modelu

Użyj poniższego kodu, aby wyświetlić metryki, Udostępnij wyniki, a następnie wykonaj na nich czynności:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Zapisz model w pliku

Po spełnieniu modelu należy zapisać go w pliku, aby dokonać prognoz w późniejszym czasie lub w innej aplikacji. Dodaj następujący kod do `Evaluate` metody. 

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

`SaveModelAsFile` Utwórz metodę`Evaluate` poniżej metody.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Dodaj następujący kod do `SaveModelAsFile` metody. Ten kod używa [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) metody do serializacji i przechowywania przeszkolonego modelu jako pliku zip.

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Wdrażanie i prognozowanie przy użyciu modelu

Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio `Evaluate` pod wywołaniem metody, przy użyciu następującego kodu:

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Utwórz metodę, tuż `Evaluate` po metodzie `SaveModelAsFile` (i tuż przed metodą), używając następującego kodu: `PredictIssue`

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue` Metoda wykonuje następujące zadania:

* Ładuje zapisany model
* Tworzy pojedynczy problem dotyczący danych testowych.
* Obszar przewidywania na podstawie danych testowych.
* Łączy dane testowe i prognozy na potrzeby raportowania.
* Wyświetla przewidywane wyniki.

Załaduj zapisany model do aplikacji, dodając następujący kod do `PredictIssue` metody:

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

Dodaj problem w usłudze GitHub, aby przetestować prognozę przeszkolonego `Predict` modelu w metodzie, tworząc `GitHubIssue`wystąpienie:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

Tak jak wcześniej, Utwórz `PredictionEngine` wystąpienie o następującym kodzie:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Użyj, `PredictionEngine` aby przewidzieć etykietę obszaru GitHub, dodając następujący kod `PredictIssue` do metody przewidywania:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Używanie załadowanego modelu do prognozowania

Wyświetlaj `Area` w celu skategoryzowania problemu i działania na nim odpowiednio. Utwórz ekran dla wyników przy użyciu następującego <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Wyniki

Wyniki powinny wyglądać podobnie do poniższego. Proces potokowy wyświetla komunikaty. Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów. Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego służący do klasyfikowania i przewidywania etykiet obszaru dla problemu usługi GitHub. Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Oceń model
> * Przewidywanie przy użyciu przeszkolonego modelu
> * Wdrażanie i przewidywanie z załadowanym modelem

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Predykcyjny opłat za taksówkę](taxi-fare.md)
