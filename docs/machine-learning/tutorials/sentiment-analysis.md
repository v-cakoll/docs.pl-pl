---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 12/20/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: c6ef4da7f429b92591c90daa3fb06f367d8a578a
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030168"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Ten przykładowy samouczek przedstawia tworzenie klasyfikatora tonacji za pomocą aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2017 przy użyciu strukturze ML.NET.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie uczenia odpowiedniej maszyny
> * Przygotowywanie danych
> * Tworzenie potoku uczenia
> * Ładowanie klasyfikatora
> * Uczenie modelu
> * Ocena modelu za pomocą innego zestawu danych
> * Pojedyncze wystąpienie wynik danych testu przy użyciu modelu prognozowania
> * Przewidywanie wyników danych testów przy użyciu załadować modelu

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
2. **Przygotowywanie danych**
   * **Ładowanie danych**
   * **Wyodrębnianie funkcji (przekształcania danych)**
3. **Kompilowanie i szkolenie** 
   * **Uczenie modelu**
   * **Ocena modelu**
4. **Uruchom**
   * **Model użycia**

### <a name="understand-the-problem"></a>Omówienie problemu

Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu. Potężne problem umożliwia prognozowanie i ocena wyników.

Ten problem, w tym samouczku jest zrozumienie, przychodzące tonacji komentarz witryny sieci Web podejmowanie odpowiednich działań.

Ten problem można podzielić do tonacji tekstu i wartości tonacji danych mają do nauczenia modelu, z, a wartości tonacji przewidywane, można obliczyć, a następnie za pomocą pod względem.

Następnie należy **określić** tonacji, która ułatwia wybieranie zadań uczenia maszynowego.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie uczenia odpowiedniej maszyny

W rozwiązaniu tego problemu znasz następujące fakty:

Szkolenie danych: komentarze witryny sieci Web może być toksyczne (1) czy nie toksyczne (0) (**tonacji**).
Przewidywanie **tonacji** nowego komentarza witryny sieci Web, toksyczne lub nie toksyczne, takie jak w następujących przykładach:

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

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "SentimentAnalysis", a następnie wybierz **OK** przycisku.

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

Musisz utworzyć trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki, a dla zmiennej globalnej `TextLoader`:

* `_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.
* `_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.
* `_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.
* `_textLoader` jest <xref:Microsoft.ML.Runtime.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek i `_textLoader` zmiennej:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku.

    *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` Klasa wejściowy zestaw danych i ma `float` (`Sentiment`) zawierający wartości tonacji dodatnie lub ujemne, a ciąg komentarza (`SentimentText`). Oba pola mają `Column` atrybuty dołączonych do nich. Ten atrybut wykonywania działań Opisuje kolejność każdego pola w pliku danych, i które `Label` pola. `SentimentPrediction` Klasa służy do prognozowania po wyszkoliła modelu. Ma ona pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu. `Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu. `PredictedLabel` Używany podczas prognoz i oceny. W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.

Podczas tworzenia modelu za pomocą platformy ML.NET rozpoczyna się od utworzenia `MLContext`. To jest porównywalna koncepcyjnie za pomocą `DbContext` platformy Entity Framework. Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Utwórz zmienną o nazwie `mlContext` i zainicjuj ją o nowe wystąpienie klasy `MLContext`.  Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

Następnie do Instalatora w celu załadowania zainicjować danych `_textLoader` zmienna globalna, aby można było użyć go ponownie.  Należy zauważyć, że używasz `TextReader`. Po utworzeniu `TextLoader` przy użyciu `TextReader`, są przekazywane w kontekście potrzebne i <xref:Microsoft.ML.Runtime.Data.TextLoader.Arguments> klasy, która umożliwia dostosowanie.

 Określ schemat danych, przekazując tablicę <xref:Microsoft.ML.Runtime.Data.TextLoader.Column> obiektów modułu ładującego zawierająca wszystkie nazwy kolumn i ich typy. Wcześniej zdefiniowany schemat danych podczas tworzenia naszej `SentimentData` klasy. Dla naszych schematu jest pierwszą kolumnę (etykieta) <xref:System.Boolean> (Prognozowane) i druga kolumna (SentimentText) to funkcja typu/ciąg tekstowy używany do prognozowania tonacji.
`TextReader` Klasa zwraca w pełni zainicjowane <xref:Microsoft.ML.Runtime.Data.TextLoader>  

Aby zainicjować `_textLoader` zmienna globalna, aby można było użyć go ponownie w przypadku wymaganych zestawów danych, Dodaj następujący kod po `mlContext` inicjowania:

[!code-csharp[initTextReader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextReader")]

Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

`Train` Metoda wykonuje następujące zadania:

* Służy do ładowania danych.
* Wyodrębnia i przekształca dane.
* Szkolenie modeli modelu.
* Prognozuje tonacji na podstawie danych testowych.
* Zwraca wartość modelu.

Tworzenie `Train` metody tuż za `Main` metody, używając następującego kodu:

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

Należy zauważyć, że dwa parametry są przekazywane do metody Train; `MLContext` kontekstu (`mlContext`), a <xref:System.String> dla ścieżki zestawu danych (`dataPath`). Użytkownik chce użyć tej metody w więcej niż jeden raz celów szkoleniowych i testów.

## <a name="load-the-data"></a>Ładowanie danych

Będzie załadować dane przy użyciu `_textLoader` zmienna globalna z `dataPath` parametru. Zwraca <xref:Microsoft.ML.Runtime.Data.IDataView>. Jako dane wejściowe i wyjściowe `Transforms`, `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.

W strukturze ML.NET dane są podobne do widoku SQL. Jest opóźnieniem ocenianą informatycznych i heterogenicznych. Obiekt jest pierwszą częścią potoku i służy do ładowania danych. W tym samouczku ładuje zestaw danych o komentarze i odpowiednie toksyczne lub inne niż toksyczne tonacji. Służy do tworzenia modelu i szkoleń.

 Dodaj następujący kod jako pierwsza linia `Train` metody:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a>Wyodrębnianie i przekształcania danych

Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego. Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości. Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.

UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą zbiór niestandardowych przekształceń, które są stosowane do danych przed szkolenie i testowanie. Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering). Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego. Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).

Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` które featurizes kolumny tekstowej (`SentimentText`) o nazwie kolumny do wektora liczbowych `Features` używane przez algorytm uczenia maszynowego. To wywołanie otoką zwracające <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601> skutecznie się potoku. Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`. Dodaj jako następnego wiersza kodu:

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

Jest to krok przetwarzania wstępnego cechowania. Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

Aby dodać instruktora, należy wywołać `mlContext.Transforms.Text.FeaturizeText` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> obiektu. Jest to uczeń drzewa decyzyjne, które będą używane w tym potoku. `FastTreeBinaryClassificationTrainer` Jest dołączany do `pipeline` i akceptuje neural `SentimentText` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.

Dodaj następujący kod do `Train` metody:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Uczenie modelu

Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone. Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601.Fit%2A> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana. Spowoduje to zwrócenie modelu na potrzeby prognozy. `pipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany. Eksperyment nie jest wykonywane, dopóki nie dzieje.

Dodaj następujący kod do `Train` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Zapisz i wróć model jest uczony na potrzeby oceny

W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET. Zwraca model na końcu `Train` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a>Ocena modelu

Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności. W `Evaluate` metody, model utworzony w `Train` jest przekazywany do obliczenia. Tworzenie `Evaluate` metody tuż za `Train`, jak w poniższym kodzie:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` Metoda wykonuje następujące zadania:

* Ładuje zestawy danych testowych.
* Tworzy ewaluatora binarnego.
* Oblicza model oraz tworzenie metryk.
* Przedstawia metryki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

Będzie załadować zestawu danych testowych za pomocą wcześniej zainicjowane `_textLoader` zmienna globalna z `_testDataPath` globalne pole. Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości. Dodaj następujący kod do `Evaluate` metody:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

Następnie użyjemy usługi machine learning `model` parametru (transformatora), aby dane wejściowe funkcji i zwracają prognozy. Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

`BinaryClassificationContext.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych. Zwraca `BinaryClassificationEvaluator.CalibratedResult` obiekt zawiera ogólne metryki obliczone przez ewaluatory klasyfikacji binarnej. Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki. Dodaj następujący kod w następnym wierszu `Evaluate` metody:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryki dotyczące weryfikacji modelu

Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

Aby zapisać swój model do pliku zip, przed zwróceniem, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `TrainFinalModel`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a>Zapisz model jako plik a.zip

Tworzenie `SaveModelAsFile` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda wykonuje następujące zadania:

* Zapisuje modelu w postaci pliku zip.

Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach. `ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.Runtime.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>. Aby zapisać ten element jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody. Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]

Można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>Przewidywanie wyników danych testu za pomocą modelu i pojedynczego komentarza

Tworzenie `Predict` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

`Predict` Metoda wykonuje następujące zadania:

* Tworzy pojedynczy komentarz danych testowych.
* Prognozuje tonacji na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

Gdy `model` jest `transformer` który operuje na wiele wierszy danych, to bardzo typowy scenariusz w środowisku produkcyjnym jest na potrzeby prognoz na poszczególne przykłady. <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> Jest otoką, który jest zwracany z `MakePredictionFunction` metody. Możemy dodać następujący kod, aby utworzyć PredictionFunction jako pierwszy wiersz w `Predict` metody:

[!code-csharp[MakePredictionFunction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionFunction")]
  
Dodaj komentarz do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]


 Możesz go używać, aby przewidzieć toksyczne lub inne niż toksyczne tonacji pojedyncze wystąpienie danych komentarz. Aby uzyskać prognozę, użyj <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602.Predict(%600)> na danych. Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="model-operationalization-prediction"></a>Model operacjonalizacji: prognoz

Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich. Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych. Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="predict-the-test-data-outcomes-with-the-saved-model"></a>Przewidywanie wyników danych testów z zapisanej modelem

Tworzenie `PredictWithModelLoadedFromFile` metody, tuż przed `SaveModelAsFile` metody, używając następującego kodu:

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

`PredictWithModelLoadedFromFile` Metoda wykonuje następujące zadania:

* Tworzy dane testowe usługi batch.
* Prognozuje tonacji na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Predict` wywołania metody, używając następującego kodu:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `PredictWithModelLoadedFromFile` metody:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

Model obciążenia

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

Teraz, gdy model, możesz go używać, aby przewidzieć toksyczne lub inne niż toksyczne tonacji przy użyciu danych komentarz <xref:Microsoft.ML.Core.Data.ITransformer.Transform(Microsoft.ML.Runtime.Data.IDataView)> metody. Aby uzyskać prognozę, użyj `Predict` na nowych danych. Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy. Dodaj następujący kod do `PredictWithModelLoadedFromFile` metodę dla prognoz:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Model operacjonalizacji: prognoz

Wyświetlanie `SentimentText` i odpowiednie przewidywania opinii w celu udostępniania wyników i odpowiednie do nich działanie na nich. Jest to nazywane operacjonalizacji, jako część zasad operacyjnych przy użyciu zwracanych danych. Utwórz nagłówek dla wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

Przed wyświetleniem wyników, Połącz opinii i prognozowania ze sobą, aby zobaczyć, oryginalnym komentarzem z jego przewidywane wskaźniki nastrojów klientów. Poniższy kod używa <xref:System.Linq.Enumerable.Zip%2A> metodę, aby to zrobić, obok więc Dodaj ten kod:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

Teraz, gdy zostały połączone `SentimentText` i `Sentiment` do klasy, można wyświetlić wyniki za pomocą <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

Ponieważ wywnioskować, że jest nową funkcją w C# 7.1 i wersją języka domyślnego projektu języka C# 7.0 nazwami elementów krotki, musisz zmienić wersję języka C# 7.1 lub nowszej.
Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku. Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja). Wybierz przycisk **OK**.

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących. Ponieważ przetwarza potoku, wyświetla komunikaty. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te zostały usunięte z następujących wyników dla przejrzystości.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.0\Data\Model.zip

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: He is the best, and the article should say that. | Prediction: Not Toxic | Probability: 0.9924279

```

Gratulacje! Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
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
