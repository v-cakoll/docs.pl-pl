---
title: 'Samouczek: Klasyfikator obraz TensorFlow ponownego próbkowania - transferu uczenia'
description: Dowiedz się, jak ponowne szkolenie modelu TensorFlow Klasyfikacja obrazów przy użyciu transferu uczenia i strukturze ML.NET. Oryginalny model został skonfigurowanych pod kątem klasyfikowania poszczególnych obrazów. Po ponownego trenowania, nowy model organizuje obrazów w ogólne kategorie.
ms.date: 06/12/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 62a926795ce34a8c1639f1d42ebbb34b53dc67ad
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401740"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>Samouczek: Ponowne szkolenie TensorFlow klasyfikatora obrazu przy użyciu transferu uczenia i strukturze ML.NET

Dowiedz się, jak ponowne szkolenie modelu TensorFlow Klasyfikacja obrazów przy użyciu transferu uczenia i strukturze ML.NET. Oryginalny model został skonfigurowanych pod kątem klasyfikowania poszczególnych obrazów. Po ponownego trenowania, nowy model organizuje obrazów w ogólne kategorie. 

Szkolenie [Klasyfikacja obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelu od podstaw wymaga ustawienie miliony parametry ogromnej ilości danych szkoleniowych etykietami i dużych ilości zasobów obliczeniowych (setki procesorów GPU godzin). Nie tak skuteczne, jak szkolenie modelu niestandardowego od podstaw, transfer uczenia umożliwia skrótów tego procesu poprzez współdziałanie z tysięcy obrazów, a miliony obrazy z etykietami i dość szybko utworzyć dostosowany model (w ciągu godziny na maszynie bez PROCESOR GPU).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Ponowne użycie i dostosowywanie wstępnie uczonego modelu
> * Klasyfikowanie obrazów

## <a name="what-is-transfer-learning"></a>Co to jest uczenie transferu?

Co zrobić, jeśli można ponownie użyć modelu, który został już wstępnie przeszkolonych do rozwiązywania podobny problem i ponownie ucz wszystkie lub niektóre z warstw tego modelu, aby pomóc w rozwiązaniu problemu? Ta technika ponownego wykorzystania część już trenowanego modelu, aby utworzyć nowy model jest znany jako [transferu learning](https://en.wikipedia.org/wiki/Transfer_learning).

## <a name="image-classification-sample-overview"></a>Omówienie przykładowych klasyfikacji obrazów

Próbka jest aplikacja konsolowa która używa strukturze ML.NET do tworzenia obrazu klasyfikatora na podstawie wstępnie uczonego modelu do klasyfikowania obrazów z małą ilością danych szkoleniowych.

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repozytorium.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

* Pakiet Nuget Microsoft.ML 1.0.0
* Pakiet Nuget Microsoft.ML.ImageAnalytics 1.0.0
* Pakiet Nuget Microsoft.ML.TensorFlow 0.12.0

* [Katalog zasobów samouczka. Plik ZIP](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [Model uczenia maszynowego InceptionV3](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie uczenia odpowiedniej maszyny

[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzestaw funkcji usługi Machine Learning, która jest revolutionizing zagadnień, takich jak przetwarzanie obrazów i rozpoznawanie mowy.

Głębokiego uczenia, modele są uczone przy użyciu dużych zestawach [etykietą danych](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych](https://en.wikipedia.org/wiki/Artificial_neural_network) zawierające wiele warstw uczenia. Uczenie głębokie:

* Działa lepiej, w niektórych zadań, takich jak przetwarzanie obrazów.

* Wykonuje również na olbrzymich ilościach danych kwoty.

Klasyfikacja obrazów jest typowym zadaniem usługi Machine Learning, która umożliwia nam automatycznego klasyfikowania obrazów do wielu kategorii, takich jak:

* Wykrywanie ludzkich twarzy na obrazie, czy nie.
* Wykrywanie koty a psy.

 Lub tak jak w następujących obrazów, określania, czy obraz jest strumieniowe żywności, zabawki lub urządzenie:

![Obraz pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![obrazu należy sobie zdawać sprawę Kubuś](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![tostera obrazu](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Poprzednie obrazy należą do Wikimedia Commons i są określane w następujący sposób:
>
> * "220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster.jpg" przez [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -własnej pracy, CC BY SA 3.0 https://commons.wikimedia.org/w/index.php?curid=27403

Transfer uczenia obejmuje kilka strategii, takie jak *Ponowne szkolenie wszystkie warstwy* i *przedostatni warstwy*. W tym samouczku zostanie wyjaśnić oraz pokazano, jak używać *strategii przedostatni warstwy*. *Strategii przedostatni warstwy* ponownie używa modelu, który jest już został wstępnie skonfigurowanych pod kątem rozwiązania konkretnego problemu. Strategia retrains następnie ostatnią warstwą tego modelu, aby rozwiązać nowy problem. Ponowne używanie wstępnie uczonego modelu w ramach nowego modelu zapisze znaczną ilość czasu i zasobów.

Model klasyfikacji obrazów ponownie używa [modelu powstania](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), model rozpoznawania popularnego obrazu skonfigurowanych pod kątem w `ImageNet` zestawu danych, gdzie próbuje klasyfikowania cały TensorFlow model obrazy na tysiąc klasy, takie jak " Ogólny","Jersey"i"Zmywarki".

`Inception v3 model` Mogą być klasyfikowane jako [głębokiego splotowe sieci neuronowe](https://en.wikipedia.org/wiki/Convolutional_neural_network) i mogą osiągnąć rozsądną wydajność na twardych visual zadań rozpoznawania, dopasowania lub przekroczenie ludzi wydajności w niektórych domen. Model/algorytm został opracowany przez wielu pracowników naukowo-badawczych i oparta na oryginalny dokument: ["Przemyślenie architektury powstania dla przetwarzania obrazów" przez Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)

Ponieważ `Inception model` została już wstępnie przeszkolonych na tysiącach różnych obrazów, zawiera on [obrazu funkcji](https://en.wikipedia.org/wiki/Feature_(computer_vision)) służące do identyfikacji obrazu. Niższych warstwach obrazu w funkcji rozpoznaje proste funkcje (na przykład krawędzie) i wyższe warstwy rozpoznaje bardziej złożonych funkcji (np. kształty). Ostatnia warstwa jest uczony względem znacznie mniejszy zestaw danych, ponieważ trwa uruchamianie za pomocą uczonego modelu sprzed i już zrozumienie sposobu klasyfikowania obrazów. Jako model umożliwia klasyfikowanie więcej niż dwie kategorie, jest to przykład [klasyfikatora wieloklasowej](../resources/tasks.md#multiclass-classification). 

`TensorFlow` Popularne uczenia głębokiego i zestaw narzędzi do usługi machine learning umożliwia szkolenia głębokich sieciach neuronowych (i ogólne obliczeń numerycznych), która jest implementowany jako `transformer` w strukturze ML.NET. W tym samouczku jest używana do ponownego użycia `Inception model`.

Jak pokazano na poniższym diagramie, możesz dodać odwołania do pakietów NuGet w strukturze ML.NET w aplikacjach platformy .NET Core lub .NET Framework. Dzieje się w tle, strukturze ML.NET obejmuje i odwołuje się do macierzystych `TensorFlow` biblioteki, który pozwala napisać kod, który ładuje, istniejące skonfigurowanych pod kątem `TensorFlow` pliku modelu do oceniania.  

![Przekształcanie TensorFlow diagram Arch strukturze ML.NET](./media/image-classification/tensorflow-mlnet.png)

`Inception model` Jest uczony do klasyfikowania obrazów do tysięcy kategorii, ale należy do klasyfikowania obrazów w mniejszy zestaw kategorii i tylko te kategorie. Wprowadź `transfer` wchodzi w skład `transfer learning`. W przypadku transferu `Inception model`firmy możliwość rozpoznaje i klasyfikowania obrazów do nowej kategorii ograniczone klasyfikatora obrazu niestandardowego.  

 Zamierzasz Ponowne szkolenie ostatnią warstwą modelu przy użyciu zestawu trzy kategorie:

* Żywność
* Zabawki
* Urządzenia

Korzysta z warstwą [algorytmu regresji logistycznej wielomian](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) możliwie jak najszybciej odnaleźć prawidłową kategorię. Ten algorytm klasyfikuje przy użyciu prawdopodobieństwa, aby określić odpowiedzi, zapewniając jednej wartości do odpowiedniej kategorii i wartość zero do innych osób.  

### <a name="dataset"></a>DataSet

Istnieją dwa źródła danych: `.tsv` plików i pliki obrazów.  `tags.tsv` Plik zawiera dwie kolumny: pierwszy z nich jest zdefiniowany jako `ImagePath` , a drugi jest `Label` odpowiadający obrazu. Następujący przykład pliku nie ma wiersz nagłówka i wygląda następująco:

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

Szkolenia i testowania obrazów znajdują się w folderach zasoby, które, konieczne będzie pobranie w formie pliku zip. Te obrazy należy do Wikimedia Commons.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych nośników.* Pobrane 10:48, 17 października 2018 r. od:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Tworzenie **aplikacji konsoli .NET Core** o nazwie "TransferLearningTF".

2. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**. Kliknij pozycję **wersji** listę rozwijaną, wybierz opcję **1.0.0** pakietu na liście, a następnie wybierz pozycję **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych. Powtórz te kroki dla **1.0.0 Microsoft.ML.ImageAnalytics** i **Microsoft.ML.TensorFlow v0.12.0**.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [pliku zip projektu zasobów katalogu](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)i Rozpakuj go.

2. Kopiuj `assets` katalogu do usługi *TransferLearningTF* katalogu projektu. Ten katalog i jego podkatalogach zawierać plików danych i pomocy technicznej (z wyjątkiem powstania modelu, który można pobrać i dodać w następnym kroku) potrzebne w tym samouczku.

3. Pobierz [modelu powstania](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i Rozpakuj go.

4. Skopiuj zawartość `inception5h` katalogu po prostu rozpakowano do Twojej *TransferLearningTF* projektu `assets\inputs-train\inception` katalogu. Ten katalog zawiera model i dodatkowe pliki obsługi potrzebne w tym samouczku, jak pokazano na poniższej ilustracji:

   ![Zawartość katalogu powstania](./media/image-classification/inception-files.png)

5. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu zasobów i podkatalogi i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowania ścieżek

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Utwórz globalne pola do przechowywania ścieżek do różnych zasobów i zmiennych globalnych `LabelTokey`,`ImageReal`, i `PredictedLabelValue`:

* `_assetsPath` zawiera ścieżkę do zasobów.
* `_trainTagsTsv` ma ścieżkę do pliku tsv szkolenia obrazu danych tagów.
* `_predictTagsTsv` ma ścieżkę do pliku tsv prognozowania obrazu danych tagów.
* `_trainImagesFolder` zawiera ścieżkę do obrazów użytych do nauczenia modelu.
* `_predictImagesFolder` zawiera ścieżkę do obrazów do sklasyfikowania trenowanego modelu.
* `_inceptionPb` zawiera ścieżkę do wstępnie przeszkolonych powstania modelu, który ma zostać ponownie użyte do Ponowne szkolenie modelu.
* `_inputImageClassifierZip` ma ścieżkę, gdzie uczony model jest ładowany z.
* `_outputImageClassifierZip` ma ścieżkę, w którym jest zapisany trenowanego modelu.
* `LabelTokey` jest `Label` wartość mapowane z kluczem.
* `ImageReal`  to kolumny zawierającej wartość przewidywane obrazu.
* `PredictedLabelValue` to kolumny zawierającej wartość przewidywane etykiety.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Utwórz niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *ImageData.cs*. Następnie wybierz **Dodaj** przycisku.

    *ImageData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *ImageData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageData` klasy *ImageData.cs* pliku:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData` Klasa danych obrazu wejściowego i ma następujące <xref:System.String> pola:

* `ImagePath` zawiera nazwę pliku obrazu.
* `Label` zawiera wartość dla etykiety obrazu.

Dodaj nową klasę do projektu, aby `ImagePrediction`:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *ImagePrediction.cs*. Następnie wybierz **Dodaj** przycisku.

    *ImagePrediction.cs* plik zostanie otwarty w edytorze kodu. Usuń oba `System.Collections.Generic` i `System.Text` `using` instrukcji na górze *ImagePrediction.cs*:

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma `ImagePrediction` klasy do *ImagePrediction.cs* pliku:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction` jest klasą prognozowania obrazu i zawiera następujące pola:

* `Score` zawiera stopień ufności klasyfikacji danego obrazu.
* `PredictedLabelValue` zawiera wartość etykiety klasyfikacji przewidywane obrazu.

`ImagePrediction` Klasa służy do prognozowania po wyszkoliła modelu. Ma ona `string` (`ImagePath`) dla ścieżki obrazu. `Label` Służy do ponownego użycia i ponowne szkolenie modelu. `PredictedLabelValue` Używany podczas prognoz i oceny. W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.

[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Przypomina, model `DBContext` platformy Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Inicjowanie `mlContext` zmiennej za pomocą nowego wystąpienia `MLContext`.  Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Tworzenie struktury dla parametrów domyślnych

Model powstania ma kilka domyślnych parametrów, które musisz przekazać. Tworzenie struktury do mapowania wartości domyślne parametrów do przyjaznych nazw następującym kodem, zaraz po `Main()` metody:

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Utwórz metodę narzędzie wyświetlania

Ponieważ więcej niż jeden raz będą wyświetlane dane obrazu i powiązane prognoz, należy utworzyć metody wyświetlania narzędzia do obsługi wyświetlania obrazów i przewidywania wyników.

`DisplayResults()` Metoda wykonuje następujące zadania:

* Wyświetla przewidywane wyniki.

Tworzenie `DisplayResults()` metody tuż za `InceptionSettings` struktury, używając następującego kodu:

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

`Transform()` Metoda wypełnione `ImagePath` w `ImagePrediction` oraz przewidywany pola. W trakcie procesu strukturze ML.NET każdego składnika dodaje kolumny, a dzięki temu można łatwo wyświetlić wyniki:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

Wywołasz `DisplayResults()` metody w dwóch obraz metody klasyfikacji.

### <a name="create-a-tsv-file-utility-method"></a>Utwórz metodę narzędzie plik tsv

`ReadFromTsv()` Metoda wykonuje następujące zadania:

* Odczytuje dane obrazu `tags.tsv` pliku.
* Dodaje ścieżkę pliku do nazwy pliku obrazu.
* Ładuje dane plików do elementu IEnumerable`ImageData` obiektu.

Tworzenie `ReadFromTsv()` metody tuż za `PairAndDisplayResults()` metody, używając następującego kodu:

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

Poniższy kod zostanie przetworzony za pośrednictwem `tags.tsv` plik, aby dodać ścieżkę pliku do nazwy pliku obrazu dla `ImagePath` właściwości, a następnie załaduj i `Label` do `ImageData` obiektu. Dodaj ją jako pierwszy wiersz `ReadFromTsv()` metody.  Konieczne jest w pełni kwalifikowana ścieżka do wyświetlenia wyników przewidywań.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
Istnieją trzy główne pojęcia w strukturze ML.NET: [Dane](../resources/glossary.md#data), [transformatory](../resources/glossary.md#transformer), i [aplikacjom](../resources/glossary.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Ponowne użycie i dostosowywanie wstępnie uczonego modelu

Dodaj następujące wywołanie do `ReuseAndTuneInceptionModel()`metodę jako następnego wiersza kodu w `Main()` metody:

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` Metoda wykonuje następujące zadania:

* Służy do ładowania danych
* Wyodrębnia i przekształca dane.
* Ocenia TensorFlow model.
* Dostraja (retrains) modelu.
* Wyświetla wyniki modelu.
* Oblicza modelu.
* Zwraca wartość modelu.

Tworzenie `ReuseAndTuneInceptionModel()` metody tuż za `InceptionSettings` struktury i tuż przed `DisplayResults()` metody, używając następującego kodu:

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Ładowanie danych

Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView). `IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe). Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.

Ładowanie danych przy użyciu `MLContext.Data.LoadFromTextFile` otoki. Dodaj następujący kod w następnym wierszu `ReuseAndTuneInceptionModel()` metody:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Wyodrębnianie funkcji i przekształcania danych

Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.  Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.

Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) danych, a kiedy dotyczących głębokich sieciach neuronowych należy dostosować obrazy do formatu oczekiwanego przez sieć. Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).

Po uczenie i Ewaluacja Prognozowanie za pomocą **etykiety** wartości w kolumnie. Ponieważ używasz wstępnie przeszkolonych modelu mapowanie pól do nowego modelu za pomocą [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody. Ta metoda przekształca `Label` do klucza typu liczbowego (`LabelTokey`) kolumny i dodaj ją jako nowe kolumny zestawu danych:  Nazwij to `estimator` jako trainer będzie również dodać do niego. Dodaj kolejny wiersz kodu:

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

Obraz przetwarzania używa narzędzie do szacowania wstępnie przeszkolonych [głębokiego Network(DNN) neuronowych](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers do wyodrębnienia funkcji. Podczas zajmowania się sieci neuronowej, można przystosować obrazy w formacie oczekiwanego sieci. Jest to przyczyną kilku przekształcenia obraz umożliwia pobieranie danych obrazu do postaci oczekiwanej modelu:

1. `LoadImages`Przekształcanie obrazów są ładowane do pamięci jako typ mapy bitowej.
2. `ResizeImages` Przekształcenie zmieni rozmiar obrazów, zgodnie z wstępnie przeszkolonych model nie ma zdefiniowanych danych wejściowych szerokość i wysokość obrazu.
3. `ExtractPixels` Przekształcenie wyodrębnia pikseli z obrazy wejściowe i konwertuje je do wektora liczbowych.

Dodaj te przekształcenia obrazu jako następnej linii kodu:

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

`LoadTensorFlowModel` Jest to wygodna metoda, która umożliwia `TensorFlow` modelu, należy załadować raz, a następnie tworzy `TensorFlowEstimator` przy użyciu `ScoreTensorFlowModel`. `ScoreTensorFlowModel` Wyodrębnia określone dane wyjściowe ( `Inception model`firmy obrazu funkcji `softmax2_pre_activation`) i ocenia zestawu danych za pomocą wstępnie przeszkolonych `TensorFlow` modelu.

`softmax2_pre_activation` ułatwia utrzymanie modelu o określenie, które klasy obrazów należy do. `softmax2_pre_activation` Zwraca prawdopodobieństwo dla każdej z kategorii w przypadku obrazu i wszystkich tych prawdopodobieństw, należy dodać do 1. Przyjęto założenie, że obraz będzie należał do tylko jednej kategorii, jak pokazano w poniższym przykładzie:

| Class         | Prawdopodobieństwo   |
| ------------- | ------------- |
| `Food`        |  0.001        |
| `Toy`         |  0.95         |
| `Appliance`   |  0,06         |

Dołącz `TensorFlowTransform` do `estimator` przy użyciu następującego kodu:

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Wybieranie algorytmu szkolenia

Aby dodać uczenie algorytmu, należy wywołać `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` metody otoki.  [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) jest dołączany do `estimator` i akceptuje funkcji obraz powstania (`softmax2_pre_activation`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.  Należy dodać instruktora następującym kodem:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Musisz również zmapować `predictedlabel` do `predictedlabelvalue`:

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` Metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia. Dopasowania modelu do zestawu danych szkoleniowych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `ReuseAndTuneInceptionModel()` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda wykonuje prognozy dla wielu podać wiersze danych wejściowych zestawu testów.  Przekształcanie `Training` danych przez dodanie poniższego kodu `ReuseAndTuneInceptionModel()`:

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Konwertuj obraz danych i prognozowania `DataViews` do silnie typizowanych `IEnumerables` parą do wyświetlenia łatwiejsze. Użyj `MLContext.CreateEnumerable()` metodę, aby to zrobić, używając następującego kodu:

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Wywołaj `DisplayResults()` metodę w celu wyświetlenia danych i prognozy w następnym wierszu `ReuseAndTuneInceptionModel()` metody:

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

Po utworzeniu prognozowania ustawiona, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metody:

* Ocenia modelu (porównuje przewidywane wartości z rzeczywistych zestawu danych `Labels`).

* Zwraca wartość metryki wydajności modelu.

Dodaj następujący kod do `ReuseAndTuneInceptionModel()` metodę jako następny wiersz:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

Następujące metryki są oceniane pod kątem Klasyfikacja obrazów:

* `Log-loss` — zobacz [utraty dziennika](../resources/glossary.md#log-loss). Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.

* `Per class Log-loss`. Chcesz na klasy utraty dziennika być maksymalnie zbliżone do zera, jak to możliwe.

Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 Dodaj następujący kod, aby zwrócić uczonego modelu w postaci następny wiersz:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>Klasyfikowanie obrazów za pomocą załadować modelu

Dodaj następujące wywołanie do `ClassifyImages()` metodę jako następnego wiersza kodu w `Main` metody:

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` Metoda wykonuje następujące zadania:

* Odczytuje. Plik TSV do `IEnumerable`.
* Prognozuje klasyfikacji obrazów na podstawie danych testowych.

Tworzenie `ClassifyImages()` metody tuż za `ReuseAndTuneInceptionModel()` metody i tuż przed `PairAndDisplayResults()` metody, używając następującego kodu:

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

Po pierwsze wywołanie `ReadFromTsv()` metodę w celu utworzenia `IEnumerable<ImageData>` klasę, która zawiera w pełni kwalifikowana ścieżka dla każdego `ImagePath`. Należy tę ścieżkę pliku, aby sparować wyniki danych i prognozowania. Musisz też przekonwertować `IEnumerable<ImageData>` klasy `IDataView` używanego do prognozowania. Dodaj następujący kod jako następne dwa wiersze w `ClassifyImages()` metody:

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

Tak jak poprzednio w przypadku danych obrazu szkolenia, przewidywanie kategorii testów obraz dane za pomocą [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) przekazanego do metody w modelu. Dodaj następujący kod do `ClassifyImages()` metodę dla prognoz i przekonwertować `predictions` `IDataView` do `IEnumerable` parowania i wyświetlania:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Sparuj i wyświetlanie danych obrazu testu i prognozy, Dodaj następujący kod do wywoływania `DisplayResults()` metoda wcześniej utworzony w następnym wierszu `ClassifyImages()` metody:

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Klasyfikowanie pojedynczy obraz z modelem załadowany

Dodaj następujące wywołanie do `ClassifySingleImage()` metodę jako następnego wiersza kodu w `Main` metody:

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifySingleImage()` Metoda wykonuje następujące zadania:

* Ładunki `ImageData` wystąpienia.
* Prognozuje Klasyfikacja obrazów na podstawie danych testowych.

Tworzenie `ClassifySingleImage()` metody tuż za `ClassifyImages()` metody i tuż przed `PairAndDisplayResults()` metody, używając następującego kodu:

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

Najpierw utwórz `ImageData` klasę, która zawiera pełną ścieżkę i obrazu nazwę pliku dla pojedynczego `ImagePath`. Dodaj następujący kod jako dalej wiersze w `ClassifySingleImage()` metody:

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[Klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, która wykonuje prognozy w pojedynczym wystąpieniu danych. [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognozę na pojedynczej kolumny danych. Przekaż `imageData` do `PredictionEngine` do prognozowania Kategoria obrazu, dodając następujący kod do `ClassifySingleImage()`:

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

Wyświetl wyniki prognozowania jako następnego wiersza kodu w `ClassifySingleImage()` metody:

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Wyniki

Po wykonaniu poprzednich kroków, uruchom aplikację konsoli (Ctrl + F5). Wyniki powinny być podobne do następujących danych wyjściowych.  Może zostać wyświetlony, ostrzeżenia i przetwarzanie komunikatów, ale te komunikaty zostały usunięte z następujące wyniki dla przejrzystości.

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

Gratulacje! Teraz pomyślnie dołączeniu model uczenia maszynowego klasyfikacji obrazów na podstawie wstępnie przeszkolonych `TensorFlow` model w strukturze ML.NET.

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repozytorium.

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Ponowne użycie i dostosowywanie wstępnie uczonego modelu
> * Klasyfikowanie obrazów za pomocą załadować modelu

Zapoznaj się z repozytorium GitHub przykładów uczenia maszynowego można eksplorować przykładową klasyfikacji obrazów rozwinięty.
> [!div class="nextstepaction"]
> [repozytorium GitHub machinelearning-DotNet-samples](https://github.com/dotnet/machinelearning-samples/)
