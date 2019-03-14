---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d94e254f0cdf56c21c94012f824f05a550e4da2f
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788469"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji

Ten przykładowy samouczek przedstawia tworzenie klasyfikatora opinii do prognozowania dodatnie lub ujemne wskaźniki nastrojów klientów za pośrednictwem używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017. W środowisku usługi machine learning tego rodzaju prognozowania nosi nazwę klasyfikacji binarnej.

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0,11**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [dotnet/machinelearning repozytorium GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybieranie algorytmu uczenia maszynowego odpowiednie
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

## <a name="sentiment-analysis-sample-overview"></a>Omówienie przykładowych analizy tonacji

Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje wskaźniki nastrojów klientów, jak dodatnie lub ujemne. Zestaw danych tonacji Yelp pochodzi z uniwersytet kalifornijski-Irvine (UCI), która zostanie podzielona na szkolenie zestaw danych i zestawy danych testowych. Przykład oblicza model z zestawu danych testowych do analizy jakości dostawców. 

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

* [Plik zip zdania etykietą tonacji na zestaw danych](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a>Maszyny uczenie się przepływu pracy

W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.

Fazy przepływu pracy są następujące:

1. **Omówienie problemu**
2. **Przygotowywanie danych**
   * **Ładowanie danych**
   * **Wyodrębnianie funkcji (przekształcania danych)**
3. **Kompilowanie i szkolenie** 
   * **Uczenie modelu**
   * **Ocena modelu**
4. **Wdrażanie modelu**
   * **Użyj modelu do prognozowania**

### <a name="understand-the-problem"></a>Omówienie problemu

Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu. Potężne problem umożliwia prognozowanie i ocena wyników.

Ten problem, w tym samouczku jest zrozumienie, przychodzące tonacji komentarz witryny sieci Web podejmowanie odpowiednich działań.

Ten problem można podzielić do tonacji tekstu i wartości tonacji danych mają do nauczenia modelu, z, a wartości tonacji przewidywane, można obliczyć, a następnie za pomocą pod względem.

Następnie należy **określić** tonacji, która ułatwia wybieranie zadań uczenia maszynowego.

## <a name="select-the-appropriate-machine-learning-algorithm"></a>Wybieranie algorytmu uczenia maszynowego odpowiednie

W rozwiązaniu tego problemu znasz następujące fakty:

Szkolenie danych: komentarze witryny sieci Web może być liczbą dodatnią (1) lub fałszywie ujemny (0) (**tonacji**).

Przewidywanie **tonacji** nowego komentarza witryny sieci Web, dodatnie lub ujemne, takie jak w następujących przykładach:

* Uwielbiam kelnerów w tym miejscu. One dzieła.
* To miejsce ma najgorszy od początku.

Algorytmu uczenia maszynowego klasyfikacji najlepiej nadaje się dla tego scenariusza.

### <a name="about-the-classification-algorithm"></a>Temat algorytm klasyfikacji

Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersza danych. Na przykład można użyć klasyfikacji:

* Zidentyfikuj tonacji jako dodatnia lub ujemna.
* Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.
* Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.
* Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.

Algorytmy klasyfikacji są często jednym z następujących typów:

* Plik binarny: A i B.
* Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.

Ponieważ komentarze witryny sieci Web muszą być klasyfikowane jako dodatnie lub ujemne, użycie algorytmu klasyfikacji binarnej. 

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

3. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [pliku zip zestawu danych na wskaźniki nastrojów klientów etykietą zdań (patrz cytaty poniżej)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i Rozpakuj go.

2. Kopiuj `yelp_labelled.txt` mezzanine do *danych* katalog został utworzony.

> [!NOTE]
> Zestawy danych, w tym samouczku są z "From grupy do poszczególnych etykiet korzystanie z funkcji głębokiego" Kotzias et. Al. KDD 2015 i hostowanej na Machine Learning repozytorium — Dua, D. i Karra Taniskidou, E. (2017). UCI usługi Machine Learning repozytorium [http://archive.ics.uci.edu/ml]. Irvine, CA: Uniwersytet kalifornijski School informacji i informatyki.

3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `yelp_labeled.txt` plik i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowania ścieżek

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

Należy utworzyć dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:

* `_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.
* `_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku.

    *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

Klasa wejściowy zestaw danych `SentimentData`, ma `string` dla komentarza (`SentimentText`) i `bool` (`Sentiment`) z wartością dla tonacji dodatnia lub ujemna. Oba pola mają <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> atrybuty dołączonych do nich. Ten atrybut wykonywania działań Opisuje kolejność każdego pola w pliku danych.  Ponadto `Sentiment` właściwość ma <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> do wyznaczenia jako `Label` pola. `SentimentPrediction` Klasa służy do prognozowania po wyszkoliła modelu. Ma ona pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu. `Label` Umożliwia tworzenie i uczenie modelu, a także używane z Podziel się z zestawu danych testowych do ewaluacji modelu. `PredictedLabel` Używany podczas prognoz i oceny. W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.

Podczas tworzenia modelu za pomocą platformy ML.NET rozpoczyna się od utworzenia <xref:Microsoft.ML.MLContext>. `MLContext` można porównywać pod względem koncepcyjnym do korzystania z `DbContext` platformy Entity Framework. Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Utwórz zmienną o nazwie `mlContext` i zainicjuj ją o nowe wystąpienie klasy `MLContext`.  Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

`LoadData` Metoda wykonuje następujące zadania:

* Służy do ładowania danych.
* Dzieli załadowanego zestawu danych na szkolenie i testowanie zestawów danych.
* Zwraca podziału nauczenia i przetestowania zestawów danych.

Tworzenie `LoadData` metody tuż za `Main` metody, używając następującego kodu:

```csharp
public static (IDataView trainSet, IDataView testSet) LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a>Ładowanie danych

Ponieważ utworzone wcześniej `SentimentData` typ modelu danych jest zgodny schemat zestawu danych, inicjowanie, mapowanie i ładowanie na jeden wiersz kodu za pomocą zestawu danych można łączyć `MLContext.Data.ReadFromTextFile` otoki dla <xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29>. Zwraca <xref:Microsoft.Data.DataView.IDataView>. 

 Jako dane wejściowe i wyjściowe `Transforms`, `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.

W strukturze ML.NET dane są podobne do widoku SQL. Jest opóźnieniem ocenianą informatycznych i heterogenicznych. Obiekt jest pierwszą częścią potoku i służy do ładowania danych. W tym samouczku ładuje zestaw danych o komentarze i odpowiednie toksyczne lub inne niż toksyczne tonacji. Służy do tworzenia modelu i szkoleń.

 Dodaj następujący kod jako pierwsza linia `LoadData` metody:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a>Podziel zestaw danych dla modelu, szkolenia i testowania

Następnie należy zarówno zestaw danych szkoleniowych do nauczenia modelu, jak i zestawy danych testowych do ewaluacji modelu. Użyj `MLContext.BinaryClassification.TrainTestSplit` który opakowuje <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> Podziel załadowanego zestawu danych na szkolenie i testowanie zestawy danych i zwrócić wewnątrz <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>. Zestaw testów przy użyciu część danych można określić `testFraction`parametru. Wartość domyślna wynosi 10%, ale w tym przypadku użyj 20% do użycia większej ilości danych do celów oceny.  

Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod w następnym wierszu `LoadData` metody:

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

Zwróć `splitDataView` na końcu `LoadData` metody:

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Tworzenie i trenowanie modelu

Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main` metody:

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Metoda wykonuje następujące zadania:

* Wyodrębnia i przekształca dane.
* Szkolenie modeli modelu.
* Prognozuje tonacji na podstawie danych testowych.
* Zwraca wartość modelu.

Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

Należy zauważyć, że dwa parametry są przekazywane do metody Train; `MLContext` kontekstu (`mlContext`), a `IDataView`dla zestawu danych szkoleniowych (`splitTrainSet`). 

## <a name="extract-and-transform-the-data"></a>Wyodrębnianie i przekształcania danych

Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego. Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości. Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.

UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą zbiór niestandardowych przekształceń, które są stosowane do danych przed szkolenie i testowanie. Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering). Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego. Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).

Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` które featurizes kolumny tekstowej (`SentimentText`) o nazwie kolumny do wektora liczbowych `Features` używane przez algorytm uczenia maszynowego. To wywołanie otoką zwracające <xref:Microsoft.ML.Data.EstimatorChain%601> skutecznie się potoku. Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`. Dodaj jako następnego wiersza kodu:

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> Wersja strukturze ML.NET 0.10 zmieniona kolejność parametrów transformacji. To spowoduje nie Błąd limitu do czasu uruchomienia aplikacji i tworzenie modelu. Użyj nazwy parametrów transformacji, jak pokazano w poprzednim fragmencie kodu.

Jest to krok przetwarzania wstępnego cechowania. Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

Aby dodać instruktora, należy wywołać `mlContext.BinaryClassification.Trainers.FastTree` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> obiektu. Jest to uczeń drzewa decyzyjne, które będą używane w tym potoku. `FastTreeBinaryClassificationTrainer` Jest dołączany do `pipeline` i akceptuje neural `SentimentText` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.

Dodaj następujący kod do `BuildAndTrainModel` metody:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Uczenie modelu

Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone. Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> metoda przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana. Spowoduje to zwrócenie modelu na potrzeby prognozy. `pipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany. Eksperyment nie jest wykonywane, dopóki `.Fit()` metoda przebiegów.

Dodaj następujący kod do `BuildAndTrainModel` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Zapisz i wróć model jest uczony na potrzeby oceny

W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET. Zwraca model na końcu `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności. W `Evaluate` metody, model utworzony w `BuildAndTrainModel` jest przekazywany do obliczenia. Tworzenie `Evaluate` metody tuż za `BuildAndTrainModel`, jak w poniższym kodzie:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

`Evaluate` Metoda wykonuje następujące zadania:

* Ładuje zestawy danych testowych.
* Tworzy ewaluatora binaryclassification.
* Oblicza model i tworzy metryki.
* Przedstawia metryki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

Następnie użyjemy usługi machine learning `model` parametru (transformatora) i `splitTestSet` parametr wejściowy funkcji i zwracają prognozy. Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

`mlContext.BinaryClassification.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji binarnej. Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki. Dodaj następujący kod w następnym wierszu `Evaluate` metody:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryki dotyczące weryfikacji modelu

Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

Aby zapisać swój model do pliku zip, przed zwróceniem, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `Evaluate`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a>Zapisz model jako plik a.zip

Tworzenie `SaveModelAsFile` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda wykonuje następujące zadania:

* Zapisuje modelu w postaci pliku zip.

Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach. `ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>. Aby zapisać ten element jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody. Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Wdrażanie i przewidywanie załadować modelu

Można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Wynik testu danych przy użyciu zapisanych modelu prognozowania

Tworzenie `UseModelWithSingleItem` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

`UseModelWithSingleItem` Metoda wykonuje następujące zadania:

* Tworzy pojedynczy komentarz danych testowych.
* Prognozuje tonacji na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

Gdy `model` jest `transformer` który operuje na wiele wierszy danych, to bardzo typowy scenariusz w środowisku produkcyjnym jest na potrzeby prognoz na poszczególne przykłady. <xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody. Możemy dodać następujący kod, aby utworzyć `PredictionEngine` jako pierwszy wiersz w `Predict` metody:

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
Dodaj komentarz do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 Możesz go używać, aby przewidzieć dodatnie lub ujemne tonacji pojedyncze wystąpienie danych komentarz. Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych. Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a>Użyj modelu: prognoz

Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich. Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych. Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Wdrażanie i przewidywanie załadować modelu

Tworzenie `UseLoadedModelWithBatchItems` metody, tuż przed `SaveModelAsFile` metody, używając następującego kodu:

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

`UseLoadedModelWithBatchItems` Metoda wykonuje następujące zadania:

* Tworzy dane testowe usługi batch.
* Prognozuje tonacji na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `UseModelWithSingleItem` wywołania metody, używając następującego kodu:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `UseLoadedModelWithBatchItems` metody:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

Model obciążenia

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

Teraz, gdy model, możesz go używać, aby przewidzieć toksyczne lub inne niż toksyczne tonacji przy użyciu danych komentarz <xref:Microsoft.ML.ITransformer.Transform%2A> metody. Aby uzyskać prognozę, użyj `Predict` na nowych danych. Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy. Dodaj następujący kod do `UseLoadedModelWithBatchItems` metodę dla prognoz:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a>Na użytek załadować modelu prognozowania

Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich. Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych. Utwórz nagłówek dla wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Przed wyświetleniem wyników, Połącz opinii i prognozowania ze sobą, aby zobaczyć, oryginalnym komentarzem z jego przewidywane wskaźniki nastrojów klientów. Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, obok więc Dodaj ten kod:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

Teraz, gdy zostały połączone `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

Ponieważ wywnioskować, że jest nową funkcją w C# 7.1 i wersją języka domyślnego projektu języka C# 7.0 nazwami elementów krotki, musisz zmienić wersję języka C# 7.1 lub nowszej.
Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku. Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja). Wybierz przycisk **OK**.

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących. Ponieważ przetwarza potoku, wyświetla komunikaty. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te zostały usunięte z następujących wyników dla przejrzystości.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Gratulacje! Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane. 

Tworzenie modeli pomyślne jest procesem iteracyjnym. Ten model jest początkowa niższa jakość samouczek używa małych zestawów danych na przeszkolenie szybkiego modelu. Jeśli nie jesteś zadowolony z jakość modelu, możesz spróbować ją ulepszyć, zapewniając większych zestawów danych szkoleniowych lub wybierając szkolenia różnych algorytmów przy użyciu różnych funkcji hyper parametrów dla każdego algorytmu.

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybieranie algorytmu uczenia maszynowego odpowiednie
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Klasyfikacja problemu](github-issue-classification.md)
