---
title: 'Samouczek: kategoryzowanie problemów z pomocą techniczną — Klasyfikacja wieloklasowa'
description: Dowiedz się, jak używać ML.NET w scenariuszu klasyfikacji wieloklasowej do klasyfikowania problemów z usługi GitHub w celu przypisywania ich do danego obszaru.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 65b83c4396c1f80281cbb60b5e9e6e91c802472b
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205038"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a>Samouczek: kategoryzowanie problemów z pomocą techniczną przy użyciu klasyfikacji wieloklasowej z .NET ML

Ten przykładowy samouczek ilustruje użycie ML.NET do utworzenia klasyfikatora problemu w usłudze GitHub w celu uczenia modelu, który klasyfikuje i przewidywalnuje etykietę obszaru dla problemu usługi GitHub za pośrednictwem aplikacji konsolowej .NET Core C# w programie Visual Studio.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
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

* [Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform w środowisku .NET Core".

* [Plik rozdzielony tabulatorami problemów usługi GitHub (issues_train. tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Plik rozdzielony kart testów problemów GitHub (issues_test. tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Wybierz pozycję **plik** > **Nowy** > **projekt** na pasku menu. W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **.NET Core** . Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "GitHubIssueClassification", a następnie wybierz przycisk **OK** .

2. Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**. Wpisz "Data" i naciśnij klawisz ENTER.

3. Utwórz katalog o nazwie *models* w projekcie, aby zapisać model:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**. Wpisz "models" i naciśnij klawisz ENTER.

4. Zainstaluj **pakiet NuGet Microsoft.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml** i wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz zestawy danych [issues_train. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) i Zapisz je w utworzonym wcześniej folderze *danych* . Pierwszy zestaw danych pociąga za niego model uczenia maszynowego, a drugi może służyć do oszacowania, jak dokładny jest model.

2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy z plików \*. tsv i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* :

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Utwórz trzy pola globalne do przechowywania ścieżek do ostatnio pobranych plików i zmienne globalne dla `MLContext`,`DataView`i `PredictionEngine`:

* `_trainDataPath` ma ścieżkę do zestawu danych używanego do uczenia modelu.
* `_testDataPath` ma ścieżkę do zestawu danych używanego do szacowania modelu.
* `_modelPath` ma ścieżkę, w której jest zapisywany model szkolony.
* `_mlContext` jest <xref:Microsoft.ML.MLContext>, który udostępnia kontekst przetwarzania.
* `_trainingDataView` jest <xref:Microsoft.ML.IDataView> używany do przetwarzania zestawu danych szkoleniowych.
* `_predEngine` jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczych prognoz.

Dodaj następujący kod do wiersza bezpośrednio powyżej metody `Main`, aby określić te ścieżki i inne zmienne:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Utwórz klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *GitHubIssueData.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *GitHubIssueData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję `using` na początku *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `GitHubIssue` i `IssuePrediction`, do pliku *GitHubIssueData.cs* :

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`label` to kolumna, która ma zostać przewidywalna. Zidentyfikowane `Features` są danymi wejściowymi, które dają model do przewidywania etykiet.

Użyj [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) , aby określić indeksy kolumn źródłowych w zestawie danych.

`GitHubIssue` jest klasą wejściowego zestawu danych i zawiera następujące pola <xref:System.String>:

* Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)
* Druga kolumna `Area` (Prognoza dla szkolenia)
* Trzecia kolumna `Title` (tytuł problemu GitHub) to pierwszy `feature` używany do przewidywania `Area`
* czwarta kolumna `Description` jest drugim `feature` używanym do przewidywania `Area`

`IssuePrediction` jest klasą używaną do przewidywania po przeszkoleniu modelu. Ma on jeden `string` (`Area`) i `PredictedLabel` `ColumnName` atrybut.  `PredictedLabel` jest używany podczas przewidywania i oceny. W celu dokonania oceny dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model są używane.

Wszystkie operacje ML.NET są uruchamiane w klasie [MLContext](xref:Microsoft.ML.MLContext) . Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo, aby `DBContext` w `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Inicjuj zmienne w głównym

Zainicjuj `_mlContext` zmienną globalną z nowym wystąpieniem `MLContext` z losowym inicjatorem (`seed: 0`) dla powtarzalnych/deterministycznych wyników dla wielu szkoleń.  Zamień wiersz `Console.WriteLine("Hello World!")` na następujący kod w metodzie `Main`:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Ładowanie danych

ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznej, wydajnej metody opisywania danych tabelarycznych lub tekstowych. `IDataView` może ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dzienników).

Aby zainicjować i załadować zmienną globalną `_trainingDataView`, aby użyć jej dla potoku, Dodaj następujący kod po zainicjowaniu `mlContext`:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.

Dodaj następujący kod jako następny wiersz kodu w metodzie `Main`:

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

Metoda `ProcessData` wykonuje następujące zadania:

* Wyodrębnia i przekształca dane.
* Zwraca potok przetwarzania.

Utwórz metodę `ProcessData` po prostu po metodzie `Main`, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Wyodrębnij funkcje i Przekształć dane

Aby przewidzieć etykietę obszaru usługi GitHub dla `GitHubIssue`, należy użyć metody [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) do przekształcenia kolumny `Area` na typ numeryczny `Label` kolumny (format akceptowany przez algorytmy klasyfikacji) i dodać go jako nową kolumnę zestawu danych:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Następnie Wywołaj `mlContext.Transforms.Text.FeaturizeText`, która przekształca kolumny tekstu (`Title` i `Description`) do wektora liczbowego dla każdego wywołanego `TitleFeaturized` i `DescriptionFeaturized`. Dołącz cechowania dla obu kolumn do potoku przy użyciu następującego kodu:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Ostatnim krokiem w przygotowaniu danych jest połączenie wszystkich kolumn funkcji w kolumnie **funkcje** przy użyciu metody [złączing ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) . Domyślnie algorytm uczenia przetwarza tylko funkcje z kolumny **Features** . Dołącz tę transformację do potoku przy użyciu następującego kodu:

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 Następnie Dołącz <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> do buforowania danych, tak aby podczas iteracji przez wiele razy przekroczyć dane za pomocą pamięci podręcznej można uzyskać lepszą wydajność, podobnie jak w przypadku następującego kodu:

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> Aby zmniejszyć czas uczenia, użyj AppendCacheCheckpoint dla małych i średnich zestawów danych. Nie należy używać go (Usuń. AppendCacheCheckpoint ()) podczas obsługi bardzo dużych zestawów danych.

Zwróć potok na końcu metody `ProcessData`.

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Ten krok obsługuje przetwarzanie wstępne/cechowania. Korzystanie z dodatkowych składników dostępnych w programie ML.NET może umożliwić lepsze wyniki w modelu.

## <a name="build-and-train-the-model"></a>Kompilowanie i uczenie modelu

Dodaj następujące wywołanie do metody `BuildAndTrainModel`jako następny wiersz kodu w metodzie `Main`:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

Metoda `BuildAndTrainModel` wykonuje następujące zadania:

* Tworzy klasę algorytmu szkoleniowego.
* Pociąga za siebie model.
* Obszar przewidywania na podstawie danych szkoleniowych.
* Zwraca model.

Utwórz metodę `BuildAndTrainModel` po prostu po metodzie `Main`, używając następującego kodu:

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

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) to algorytm szkoleniowy klasyfikacji wieloklasowej. Jest to dołączane do `pipeline` i akceptuje `Title` featurized i `Description` (`Features`) oraz parametry wejściowe `Label`, aby poznać dane historyczne.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj model do danych `splitTrainSet` i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu w metodzie `BuildAndTrainModel()`:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

Metoda `Fit()`pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który pozwala na przekazywanie danych, a następnie wykonywanie prognozowania na jednym wystąpieniu. Dodaj tę wartość jako następny wiersz w `BuildAndTrainModel()` metodzie:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Przewidywanie przy użyciu przeszkolonego modelu

Dodaj problem w usłudze GitHub, aby przetestować prognozę przeszkolonego modelu w metodzie `Predict` przez utworzenie wystąpienia `GitHubIssue`:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) służy do prognozowania pojedynczego wiersza danych:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Korzystanie z modelu: wyniki przewidywania

Wyświetlanie `GitHubIssue` i odpowiadanie na `Area` prognozowanie etykiet w celu udostępniania wyników i wykonywania odpowiednich czynności.  Utwórz ekran dla wyników przy użyciu następującego kodu <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwróć model przeszkolony do użycia na potrzeby oceny

Zwróć model na końcu metody `BuildAndTrainModel`.

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Oceń model

Teraz, gdy tworzysz i przeszkolony model, musisz go oszacować z innym zestawem danych w celu zapewnienia jakości i weryfikacji. W metodzie `Evaluate` model utworzony w `BuildAndTrainModel` jest przenoszona do oceny. Utwórz metodę `Evaluate` po `BuildAndTrainModel`, tak jak w poniższym kodzie:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

Metoda `Evaluate` wykonuje następujące zadania:

* Ładuje zestaw danych testowych.
* Tworzy ewaluatora wieloklasowe.
* Oblicza model i tworzy metryki.
* Wyświetla metryki.

Dodaj wywołanie do nowej metody z metody `Main`, bezpośrednio pod wywołaniem metody `BuildAndTrainModel`, przy użyciu następującego kodu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Tak jak wcześniej z zestawem danych szkoleniowych, Załaduj zestaw danych testowych, dodając następujący kod do metody `Evaluate`:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

Metoda COMPUTE [()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) oblicza metryki jakości dla modelu przy użyciu określonego zestawu danych. Zwraca obiekt <xref:Microsoft.ML.Data.MulticlassClassificationMetrics>, który zawiera metryki ogólne obliczone przez konstruktory klasyfikacji wieloklasowej.
Aby wyświetlić metryki w celu określenia jakości modelu, należy je najpierw pobrać.
Zwróć uwagę na użycie metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) `_trainedModel` zmiennej globalnej ( [ITransformer](xref:Microsoft.ML.ITransformer)), aby wejść do funkcji i zwracać prognoz. Dodaj następujący kod do metody `Evaluate` w następnym wierszu:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Następujące metryki są oceniane dla klasyfikacji wieloklasowej:

* Mikro-dokładność — każda para klasy próbek bezproblemowo przyczynia się do metryki dokładności.  Chcesz, aby program Micro dokładności był możliwie blisko jednej, jak to możliwe.

* Dokładność makra — każda klasa przyczynia się równo do metryki dokładności. Klasy mniejszości są traktowane jako takie same wagi jak większe klasy. Dokładność makra powinna być jak najbliżej jednego z nich.

* Dziennik — utrata — zobacz [Dziennik strat](../resources/glossary.md#log-loss). Utrata dziennika powinna być jak najbliżej zera.

* Redukcja utraconych plików dziennika — zakresy z [-inf, 1,00], gdzie 1,00 są idealnym przewidywaniam, a wartość 0 oznacza przewidywania. Zmniejszenie liczby utraconych dzienników jest możliwie najbliżej jednego z nich.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk na potrzeby walidacji modelu

Użyj poniższego kodu, aby wyświetlić metryki, Udostępnij wyniki, a następnie wykonaj na nich czynności:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Zapisz model w pliku

Po spełnieniu modelu należy zapisać go w pliku, aby dokonać prognoz w późniejszym czasie lub w innej aplikacji. Dodaj następujący kod do metody `Evaluate`.

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

Utwórz metodę `SaveModelAsFile` poniżej metody `Evaluate`.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Dodaj następujący kod do metody `SaveModelAsFile`. Ten kod używa metody [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) do serializacji i przechowywania przeszkolonego modelu jako pliku zip.

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Wdrażanie i prognozowanie przy użyciu modelu

Dodaj wywołanie do nowej metody z metody `Main`, bezpośrednio pod wywołaniem metody `Evaluate`, przy użyciu następującego kodu:

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Utwórz metodę `PredictIssue`, tuż po metodzie `Evaluate` (i tuż przed metodą `SaveModelAsFile`), używając następującego kodu:

```csharp
private static void PredictIssue()
{

}
```

Metoda `PredictIssue` wykonuje następujące zadania:

* Ładuje zapisany model
* Tworzy pojedynczy problem dotyczący danych testowych.
* Obszar przewidywania na podstawie danych testowych.
* Łączy dane testowe i prognozy na potrzeby raportowania.
* Wyświetla przewidywane wyniki.

Załaduj zapisany model do aplikacji, dodając następujący kod do metody `PredictIssue`:

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

Dodaj problem w usłudze GitHub, aby przetestować prognozę przeszkolonego modelu w metodzie `Predict` przez utworzenie wystąpienia `GitHubIssue`:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

Tak jak wcześniej, Utwórz wystąpienie `PredictionEngine` przy użyciu następującego kodu:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczna wątkowo. Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, Użyj usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji. Zapoznaj się z tym przewodnikiem dotyczącym [korzystania z `PredictionEnginePool` w interfejsie API sieci Web ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)

> [!NOTE]
> rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.

Użyj `PredictionEngine`, aby przewidzieć etykietę obszaru GitHub, dodając następujący kod do metody `PredictIssue` w celu przewidywania:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Używanie załadowanego modelu do prognozowania

Wyświetl `Area` w celu skategoryzowania problemu i działania na nim odpowiednio. Utwórz ekran dla wyników przy użyciu następującego kodu <xref:System.Console.WriteLine?displayProperty=nameWithType>:

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
> [Predykcyjny opłat za taksówkę](predict-prices.md)
