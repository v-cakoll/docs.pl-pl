---
title: 'Samouczek: Ponowne uczenie klasyfikatora obrazu TensorFlow — uczenie transferu'
description: Dowiedz się, jak ponownie przeprowadzić uczenie modelu TensorFlow klasyfikacji obrazów przy użyciu uczenia transferowego i ML.NET. Oryginalny model został przeszkolony do klasyfikowania poszczególnych obrazów. Po przeprowadzeniu ponownego uczenia nowy model organizuje obrazy w szerokich kategoriach.
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: eb6e3d3f3a33aa7360802ce1bc6c16532539c828
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929239"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>Samouczek: Ponowne uczenie klasyfikatora obrazu TensorFlow z uczeniem transferu i ML.NET

Dowiedz się, jak ponownie przeprowadzić uczenie modelu TensorFlow klasyfikacji obrazów przy użyciu uczenia transferowego i ML.NET. Oryginalny model został przeszkolony do klasyfikowania poszczególnych obrazów. Po przeprowadzeniu ponownego uczenia nowy model organizuje obrazy w szerokich kategoriach. 

Uczenie modelu [klasyfikacji obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od podstaw wymaga ustawienia milionów parametrów, moc z etykietami danych szkoleniowych i ogromną ilość zasobów obliczeniowych (setki godzin procesora GPU). Chociaż nie jest tak wydajny, jak uczenie modelu niestandardowego od podstaw, uczenie przenoszenia pozwala na podjęcie tego procesu przez pracę z tysiącami obrazów i milionów obrazów z etykietami, a następnie szybko utworzyć dostosowany model (w ciągu godziny na maszynie bez PROCESOR GPU).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Ponowne użycie i dostosowanie modelu wstępnie przeszkolonego
> * Klasyfikowanie obrazów

## <a name="what-is-transfer-learning"></a>Co to jest uczenie transferu?

Co zrobić, jeśli możesz użyć wcześniej przeszkolonego modelu, aby rozwiązać podobny problem i przeszkolić wszystkie lub niektóre warstwy tego modelu w celu rozwiązania problemu? Ta technika ponownego wykorzystania części już przeszkolonego modelu w celu utworzenia nowego modelu jest znana jako [nauka transferu](https://en.wikipedia.org/wiki/Transfer_learning).

## <a name="image-classification-sample-overview"></a>Przykład klasyfikacji obrazów — Omówienie

Przykładem jest Aplikacja konsolowa, która używa ML.NET do tworzenia klasyfikatora obrazu przez ponowne użycie wstępnie przeszkolonego modelu do klasyfikowania obrazów z niewielką ilością danych szkoleniowych.

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) . Należy pamiętać, że domyślnie konfiguracja projektu .NET dla tego samouczka dotyczy platformy .NET Core 2,2.

## <a name="prerequisites"></a>Wymagania wstępne

* [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core. 

* Pakiet NuGet Microsoft.ML 1.0.0
* Pakiet NuGet Microsoft. ML. ImageAnalytics 1.0.0
* Pakiet NuGet Microsoft. ML. TensorFlow 0.12.0

* [Katalog zasobów samouczka. Plik ZIP](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [Model uczenia maszynowego InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzbiór Machine Learning, które są obszarami revolutionizing, takimi jak przetwarzanie obrazów i rozpoznawanie mowy.

Modele uczenia głębokiego są przeszkolone przy użyciu dużych zestawów [danych z etykietami](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych](https://en.wikipedia.org/wiki/Artificial_neural_network) , które zawierają wiele warstw szkoleniowych. Uczenie głębokie:

* Wykonuje lepsze zadania, takie jak przetwarzanie obrazów.

* Dobrze sprawdza się w przypadku dużych ilości danych.

Klasyfikacja obrazu to typowe zadanie Machine Learning, które pozwala nam na automatyczne klasyfikowanie obrazów do wielu kategorii, takich jak:

* Wykrywanie ludzkiej twarz w obrazie.
* Wykrywanie kotów a psy.

 Lub tak jak w przypadku następujących obrazów określających, czy obraz jest (n) jedzeniem, Zabawka lub urządzeniem:

![obraz przedstawiający obraz przedstawiający zdjęcie z obrazu Pizza Teddy](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![![](./media/image-classification/220px-Pepperoni_pizza.jpg)
](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Powyższe obrazy należą do Wikimedia Commons Attribution i są przypisywane w następujący sposób:
>
> * "220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear. jpg" przez [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) — własne grafy, CC przez-sa 2,0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster. jpg" według [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) — zadania własne, CC według-sa 3,0, https://commons.wikimedia.org/w/index.php?curid=27403

Nauka transferu obejmuje kilka strategii, takich jak ponowne *uczenie wszystkich warstw* i przedniej *warstwy*. Ten samouczek wyjaśnia i pokazuje, jak używać *przedostatniej strategii warstwy*. Przedstawiona *strategia warstwy* ponownie używa modelu, który jest już wstępnie przeszkolony do rozwiązywania określonego problemu. Następnie strategia ponownie przeprowadzi przeszkolenie ostatniej warstwy tego modelu w celu rozwiązania nowego problemu. Użycie wstępnie nauczonego modelu w ramach nowego modelu spowoduje znaczne oszczędności czasu i zasobów.

Model klasyfikacji obrazów ponownie używa [modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), który jest popularnym modelem rozpoznawania obrazu przeszkolonym na `ImageNet` zestawie danych, gdzie model TensorFlow próbuje klasyfikować całe obrazy do tysięcy klas, takich jak "parasol", "Jersey" i " Zmywarka ".

Może być sklasyfikowany jako [głębokiej sieci neuronowych splotowych](https://en.wikipedia.org/wiki/Convolutional_neural_network) , dzięki czemu można uzyskać odpowiednią wydajność w przypadku zadań rozpoznawania wizualnego, dopasowanie lub przekroczenie wydajności ludzkich w niektórych domenach. `Inception v1 model` Model/algorytm został opracowany przez wielu badaczy i w oparciu o oryginalny papier: ["Rozmyślisz architekturę rozpoczęcia dla przetwarzanie obrazów" według Szegedy. wsp.](https://arxiv.org/abs/1512.00567)

Ponieważ program został już wstępnie przeszkolony na tysiącach różnych obrazów, zawiera [funkcje obrazu](https://en.wikipedia.org/wiki/Feature_(computer_vision)) niezbędne do identyfikacji obrazu. `Inception model` Niższe warstwy funkcji obrazu rozpoznają proste funkcje (takie jak krawędzie), a wyższe warstwy rozpoznają bardziej złożone funkcje (takie jak kształty). Warstwa końcowa jest przeszkolone względem znacznie mniejszego zestawu danych, ponieważ zaczynasz od wstępnie nauczonego modelu, który już rozumie sposób klasyfikowania obrazów. Ponieważ model pozwala na klasyfikowanie więcej niż dwóch kategorii, jest to przykład [klasyfikatora wieloklasowego](../resources/tasks.md#multiclass-classification). 

`TensorFlow`jest popularnym zestawem narzędzi uczenia głębokiego i uczenia maszynowego, który umożliwia uczenie rozległych sieci neuronowych (i ogólnych obliczeń `transformer` liczbowych), i jest zaimplementowany w ml.NET. Ten samouczek służy do ponownego użycia programu `Inception model`.

Jak pokazano na poniższym diagramie, należy dodać odwołanie do pakietów NuGet ML.NET w aplikacjach .NET Core lub .NET Framework. W obszarze okładek ml.NET obejmuje i odwołuje się do `TensorFlow` biblioteki natywnej, która umożliwia pisanie kodu ładującego istniejący plik `TensorFlow` modelu wyszkolonego do oceny.  

![Diagram TensorFlow transformacji ML.NET](./media/image-classification/tensorflow-mlnet.png)

Program `Inception model` jest szkolony do klasyfikowania obrazów do tysięcy kategorii, ale należy sklasyfikować obrazy w mniejszym zestawie kategorii i tylko te kategorie. Wprowadź część elementu `transfer learning`. `transfer` Można przenieść `Inception model`możliwość rozpoznawania i klasyfikowania obrazów do nowych, ograniczonej kategorii klasyfikatora niestandardowego obrazu.  

 Zamierzasz ponownie przeprowadzić przeszkolenie ostatniej warstwy tego modelu przy użyciu zestawu trzech kategorii:

* Żywność
* Zabawki
* Wprowadzony

Warstwa używa [algorytmu regresji logistycznej](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) w celu wyszukania odpowiedniej kategorii tak szybko, jak to możliwe. Ten algorytm klasyfikuje przy użyciu prawdopodobieństwa, aby określić odpowiedź, dając jedną wartość do właściwej kategorii i wartość zerową innym.  

### <a name="dataset"></a>DataSet

Istnieją dwa źródła danych: `.tsv` plik i pliki obrazów.  Plik zawiera dwie kolumny: pierwszy jest zdefiniowany jako `ImagePath` , a drugi jest `Label` odpowiadający obrazowi. `tags.tsv` Następujący przykładowy plik nie ma wiersza nagłówka i wygląda następująco:

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

Obrazy szkoleniowe i testowe znajdują się w folderach zasobów, które zostaną pobrane w pliku zip. Te obrazy należą do Wikimedia Commons Attribution.
> *[Wikimedia Commons Attribution](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych nośników.* Pobrano 10:48, 17 października 2018 z:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Utwórz **aplikację konsolową .NET Core** o nazwie "TransferLearningTF".

2. Zainstaluj **pakiet NuGet Microsoft.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**. Kliknij listę rozwijaną **wersja** , wybierz pakiet **1.0.0** z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów. Powtórz te kroki dla **Microsoft. ml. ImageAnalytics v 1.0.0** i **Microsoft. ml. TensorFlow v 0.12.0**.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [plik zip katalogu zasobów projektu](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)i rozpakuj.

2. Skopiuj katalog do katalogu projektu *TransferLearningTF.* `assets` Ten katalog i jego podkatalogi zawierają pliki danych i obsługi (z wyjątkiem modelu, który zostanie pobrany i dodany w następnym kroku), co jest potrzebne w tym samouczku.

3. Pobierz [model rozpoczęcia](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i rozpakuj.

4. Skopiuj zawartość `inception5h` katalogu w sposób niespakowany do katalogu projektu `assets\inputs-train\inception` *TransferLearningTF* . Ten katalog zawiera model i dodatkowe pliki pomocnicze, które są odpowiednie dla tego samouczka, jak pokazano na poniższej ilustracji:

   ![Zawartość katalogu początkowej](./media/image-classification/inception-files.png)

5. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu zasobów i podkatalogach i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Utwórz pola globalne, aby przechowywać ścieżki do różnych elementów zawartości, oraz zmienne globalne dla `LabelTokey`,`ImageReal`i `PredictedLabelValue`:

* `_assetsPath`ma ścieżkę do zasobów.
* `_trainTagsTsv`ma ścieżkę do pliku TSV tagów danych obrazu.
* `_predictTagsTsv`ma ścieżkę do pliku TSV ze znacznikami danych obrazu predykcyjnego.
* `_trainImagesFolder`ma ścieżkę do obrazów używanych do uczenia modelu.
* `_predictImagesFolder`ma ścieżkę do obrazów, które mają być klasyfikowane przez szkolony model.
* `_inceptionPb`ma ścieżkę do wstępnie przeszkolonego modelu, który ma zostać ponownie użyty w celu ponownego nauczenia modelu.
* `_inputImageClassifierZip`ma ścieżkę, z której jest ładowany przeszkolony model.
* `_outputImageClassifierZip`ma ścieżkę, w której jest zapisywany model szkolony.
* `LabelTokey``Label` jest wartością zamapowana na klucz.
* `ImageReal`jest kolumną zawierającą przewidywaną wartość obrazu.
* `PredictedLabelValue`jest kolumną zawierającą przewidywaną wartość etykiety.

Dodaj następujący kod do wiersza bezpośrednio powyżej `Main` metody, aby określić te ścieżki i inne zmienne:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Utwórz klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageData.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *ImageData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *ImageData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageData` klasy do pliku *ImageData.cs* :

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:

* `ImagePath`zawiera nazwę pliku obrazu.
* `Label`zawiera wartość etykiety obrazu.

Dodaj nową klasę do projektu dla `ImagePrediction`:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImagePrediction.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *ImagePrediction.cs* zostanie otwarty w edytorze kodu. `System.Collections.Generic` Usuń obie `System.Text` iteinstrukcjew`using` górnej części *ImagePrediction.cs*:

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma `ImagePrediction` klasę, do pliku *ImagePrediction.cs* :

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction`jest klasą przewidywania obrazów i ma następujące pola:

* `Score`zawiera procent zaufania dla danej klasyfikacji obrazu.
* `PredictedLabelValue`zawiera wartość dla etykiety klasyfikacji predykcyjnej obrazu.

`ImagePrediction`jest klasą używaną do przewidywania po przeszkoleniu modelu. Ma `string` (`ImagePath`) dla ścieżki obrazu. `Label` Służy do ponownego użycia i ponownej nauczenia modelu. `PredictedLabelValue` Jest używany podczas przewidywania i oceny. W celu dokonania oceny dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model są używane.

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicjuj zmienne w głównym

`MLContext`Zainicjuj `mlContext` zmienną z nowym wystąpieniem.  Zamień wiersz na następujący kod `Main` w metodzie: `Console.WriteLine("Hello World!")`

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Tworzenie struktury dla domyślnych parametrów

Model rozpoczęcia zawiera kilka domyślnych parametrów, które należy przekazać. Utwórz strukturę służącą do mapowania domyślnych wartości parametrów na przyjazne nazwy o następującym kodzie, zaraz po `Main()` metodzie:

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Utwórz metodę narzędzia do wyświetlania

Ponieważ wyświetlasz dane obrazu i powiązane przewidywania więcej niż raz, Utwórz metodę narzędzia do wyświetlania, aby obsłużyć wyświetlanie obrazu i wyników przewidywania.

`DisplayResults()` Metoda wykonuje następujące zadania:

* Wyświetla przewidywane wyniki.

Utwórz metodę, tuż po strukturze, przy użyciu następującego kodu: `InceptionSettings` `DisplayResults()`

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

Metoda wypełniana `ImagePath`wrazzprzewidywanymi polami.`ImagePrediction` `Transform()` W miarę postępów procesu ML.NET każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

`DisplayResults()` Metoda zostanie wywołana przy użyciu dwóch metod klasyfikacji obrazu.

### <a name="create-a-tsv-file-utility-method"></a>Tworzenie metody narzędziowej pliku. tsv

`ReadFromTsv()` Metoda wykonuje następujące zadania:

* Odczytuje plik danych `tags.tsv` obrazu.
* Dodaje ścieżkę pliku do nazwy pliku obrazu.
* Ładuje dane pliku do obiektu IEnumerable`ImageData` .

Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `PairAndDisplayResults()` `ReadFromTsv()`

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

Poniższy kod analizuje `tags.tsv` plik, aby dodać ścieżkę pliku do nazwy pliku obrazu `ImagePath` dla właściwości `Label` i załadować `ImageData` ją oraz do obiektu. Dodaj ją jako pierwszy wiersz `ReadFromTsv()` metody.  Do wyświetlania wyników przewidywania potrzebna jest w pełni kwalifikowana ścieżka do pliku.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
Istnieją trzy podstawowe koncepcje w ML.NET: [Dane](../resources/glossary.md#data), [Transformatory](../resources/glossary.md#transformer)i [szacowania](../resources/glossary.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Ponowne użycie i dostrajanie modelu wstępnie przeszkolonego

Dodaj następujące wywołanie do `ReuseAndTuneInceptionModel()`metody jako następny wiersz kodu `Main()` w metodzie:

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` Metoda wykonuje następujące zadania:

* Ładuje dane
* Wyodrębnia i przekształca dane.
* Ocenia model TensorFlow.
* Dostraja (reciągia) model.
* Wyświetla wyniki modelu.
* Oblicza model.
* Zwraca model.

Utwórz metodę, tuż `InceptionSettings` po `DisplayResults()` strukturze i tuż przed metodą, używając następującego kodu: `ReuseAndTuneInceptionModel()`

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Ładowanie danych

Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.

Załaduj dane przy użyciu `MLContext.Data.LoadFromTextFile` otoki. Dodaj następujący kod w następnym wierszu `ReuseAndTuneInceptionModel()` metody:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Wyodrębnij funkcje i Przekształć dane

Wstępne przetwarzanie i czyszczenie danych to ważne zadania, które wystąpiły, zanim zestaw danych jest efektywnie używany do uczenia maszynowego.  Korzystanie z danych bez wykonywania zadań modelowania może dawać mylące wyniki.

Algorytmy uczenia maszynowego rozumieją dane [featurized](../resources/glossary.md#feature) i podczas pracy z sieciami głębokiej neuronowych należy dostosować obrazy do formatu oczekiwanego przez sieć. Ten format jest [wektorem liczbowym](../resources/glossary.md#numerical-feature-vector).

Po przeprowadzeniu szkolenia i oceny należy przewidzieć wartości kolumn **etykiet** . Gdy korzystasz z wstępnie przeszkolonego modelu, Mapuj pola do nowego modelu przy użyciu metody [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) . Ta metoda `Label` przekształca w kolumnę typu liczbowego (`LabelTokey`) i dodaje ją jako nową kolumnę DataSet:  Nadaj mu nazwę, ponieważ spowoduje to również dodanie do niego Trainer. `estimator` Dodaj następny wiersz kodu:

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

Szacowania do przetwarzania obrazów używa wstępnie przeszkolonego featurizers [sieci neuronowych (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) do wyodrębniania funkcji. W przypadku głębokiej sieci neuronowych można dostosować obrazy do oczekiwanego formatu sieci. Jest to powód użycia kilku przekształceń obrazu w celu uzyskania danych obrazu w oczekiwanej postaci modelu:

1. Obrazy `LoadImages`transformacji są ładowane w pamięci jako typ mapy bitowej.
2. `ResizeImages` Transformacja zmienia rozmiar obrazów, ponieważ wstępnie szkolony model ma zdefiniowaną szerokość i wysokość obrazu wejściowego.
3. `ExtractPixels` Transformacja wyodrębnia piksele z obrazów wejściowych i konwertuje je na wektor liczbowy.

Dodaj te przekształcenia obrazu jako kolejne wiersze kodu:

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

Jest to wygodna metoda `TensorFlow` umożliwiająca załadowanie modelu, a następnie utworzenie `TensorFlowEstimator` elementu using `ScoreTensorFlowModel`. `LoadTensorFlowModel` Wyodrębnione dane wyjściowe `Inception model`(funkcje `softmax2_pre_activation`obrazu) i oceniają zestaw danych przy użyciu wstępnie nauczonego `TensorFlow` modelu. `ScoreTensorFlowModel`

`softmax2_pre_activation`ułatwia modelowi określenie, do której klasy należą obrazy. `softmax2_pre_activation`Zwraca prawdopodobieństwo dla każdej z kategorii obrazu, a wszystkie te prawdopodobieństwo muszą mieć wartość 1. Przyjęto założenie, że obraz będzie należeć tylko do jednej kategorii, jak pokazano w poniższym przykładzie:

| Class         | Rozkład   |
| ------------- | ------------- |
| `Food`        |  0,001        |
| `Toy`         |  0,95         |
| `Appliance`   |  0,06         |

`TensorFlowTransform` Dołącz`estimator` do z następującym wierszem kodu:

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Wybierz algorytm szkoleniowy

Aby dodać algorytm szkoleniowy, wywołaj `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` metodę otoki.  [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) jest dołączany do `estimator` i akceptuje funkcje obrazu rozpoczęcia `Label` (`softmax2_pre_activation`) i parametry wejściowe, aby poznać dane historyczne.  Dodaj Trainer przy użyciu następującego kodu:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Należy również zmapować `predictedlabel` `predictedlabelvalue`do:

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` Metoda pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia. Dopasuj model do zestawu danych szkoleniowych i zwróć przeszkolony model, dodając następujący element jako następny wiersz kodu w `ReuseAndTuneInceptionModel()` metodzie:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) udostępnia prognozy dla wielu podanych danych wejściowych dla testu zestawu danych.  Przekształć `ReuseAndTuneInceptionModel()`dane, dodając następujący kod do: `Training`

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Przekształć dane obrazu i przeprowadź prognozowanie `DataViews` do pary o jednoznacznie określonym typie `IEnumerables` , aby umożliwić wyświetlanie. `MLContext.CreateEnumerable()` Użyj metody, aby to zrobić, przy użyciu następującego kodu:

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Wywołaj `ReuseAndTuneInceptionModel()` metodę, aby wyświetlić dane i przewidywania w następnym wierszu metody: `DisplayResults()`

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

Po wybraniu zestawu prognoz Metoda [szacowania ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

* Ocenia model (porównuje wartości przewidywane z rzeczywistym zestawem danych `Labels`).

* Zwraca metryki wydajności modelu.

Dodaj następujący kod do `ReuseAndTuneInceptionModel()` metody w następnym wierszu:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

Następujące metryki są oceniane pod kątem klasyfikacji obrazów:

* `Log-loss`-Zobacz [utrata dzienników](../resources/glossary.md#log-loss). Utrata dziennika powinna być jak najbliżej zera.

* `Per class Log-loss`. Dla każdej klasy Dziennik ma być zbliżony do zera, jak to możliwe.

Użyj poniższego kodu, aby wyświetlić metryki, Udostępnij wyniki, a następnie wykonaj na nich czynności:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 Dodaj następujący kod, aby zwrócić przeszkolony model jako następny wiersz:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>Klasyfikowanie obrazów z załadowanym modelem

Dodaj następujące wywołanie do `ClassifyImages()` metody jako następny wiersz kodu `Main` w metodzie:

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` Metoda wykonuje następujące zadania:

* Odczytywan. Plik TSV do `IEnumerable`.
* Przewiduje klasyfikacje obrazów na podstawie danych testowych.

Utwórz metodę, tuż `ReuseAndTuneInceptionModel()` po `PairAndDisplayResults()` metodzie i tuż przed metodą, używając następującego kodu: `ClassifyImages()`

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

Najpierw Wywołaj `ReadFromTsv()` metodę, aby `IEnumerable<ImageData>` utworzyć klasę, która zawiera w pełni kwalifikowaną ścieżkę dla każdej `ImagePath`z nich. Ta ścieżka pliku jest potrzebna do sparowania danych i wyników przewidywania. Należy również przekonwertować klasę `IEnumerable<ImageData>` `IDataView` na wartość, która będzie używana do przewidywania. Dodaj następujący kod jako następne dwa wiersze w `ClassifyImages()` metodzie:

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

Podobnie jak w przypadku danych obrazu szkoleniowego, przewidywana jest kategoria danych obrazu testowego przy użyciu metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) modelu. `ClassifyImages()` Dodaj następujący kod do metody prognoz i `predictions` `IDataView` Przekształć element `IEnumerable` na na potrzeby parowania i Display:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Aby sparować i wyświetlić dane obrazu testu i przewidywania, Dodaj następujący kod, aby wywołać `DisplayResults()` metodę wcześniej utworzoną jako następny wiersz `ClassifyImages()` w metodzie:

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Klasyfikowanie pojedynczego obrazu z załadowanym modelem

Dodaj następujące wywołanie do `ClassifySingleImage()` metody jako następny wiersz kodu `Main` w metodzie:

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifySingleImage()` Metoda wykonuje następujące zadania:

* `ImageData` Ładuje wystąpienie.
* Przewiduje klasyfikację obrazów na podstawie danych testowych.

Utwórz metodę, tuż `ClassifyImages()` po `PairAndDisplayResults()` metodzie i tuż przed metodą, używając następującego kodu: `ClassifySingleImage()`

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

Najpierw Utwórz `ImageData` klasę, która zawiera w pełni kwalifikowaną ścieżkę i nazwę pliku obrazu dla jednego `ImagePath`z nich. Dodaj następujący kod jako następny wiersz w `ClassifySingleImage()` metodzie:

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[Klasa PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który wykonuje prognozowanie jednego wystąpienia danych. Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczej kolumny danych. Przekaż `imageData` do, `PredictionEngine` aby przewidzieć kategorię obrazu, dodając następujący kod do `ClassifySingleImage()`:

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

Wyświetl wynik przewidywania jako następny wiersz kodu w `ClassifySingleImage()` metodzie:

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Wyniki

Po wykonaniu poprzednich kroków uruchom aplikację konsolową (Ctrl + F5). Wyniki powinny wyglądać podobnie do poniższych danych wyjściowych.  Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.

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

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego na potrzeby klasyfikacji obrazów przez ponowne użycie wstępnie nauczonego `TensorFlow` modelu w ml.NET.

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Ponowne użycie i dostosowanie modelu wstępnie przeszkolonego
> * Klasyfikowanie obrazów z załadowanym modelem

Zapoznaj się z przykładem Machine Learning przykładowe repozytorium GitHub, aby poznać rozszerzoną próbkę klasyfikacji obrazów.
> [!div class="nextstepaction"]
> [dotnet/machinelearning — przykłady repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/)
