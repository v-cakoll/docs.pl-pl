---
title: 'Samouczek: Generuj model klasyfikacji obrazów ML.NET na podstawie wstępnie nauczonego modelu TensorFlow'
description: Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET. Model TensorFlow został przeszkolony do klasyfikowania obrazów do tysięcy kategorii. Model ML.NET wykorzystuje uczenie transferu do klasyfikowania obrazów do mniejszej liczby szerszej kategorii.
ms.date: 09/26/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 28d8c18721bd353e961284935758a87679c8c8e0
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353683"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Samouczek: Generuj model klasyfikacji obrazów ML.NET na podstawie wstępnie nauczonego modelu TensorFlow

Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET.

Model TensorFlow został przeszkolony do klasyfikowania obrazów do tysięcy kategorii. Model ML.NET wykorzystuje część modelu TensorFlow w potoku do uczenia modelu do klasyfikowania obrazów do 3 kategorii.

Uczenie modelu [klasyfikacji obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od podstaw wymaga ustawienia milionów parametrów, moc z etykietami danych szkoleniowych i ogromną ilość zasobów obliczeniowych (setki godzin procesora GPU). Chociaż nie jest tak wydajny, jak uczenie modelu niestandardowego od podstaw, uczenie przenoszenia pozwala na podjęcie tego procesu przez pracę z tysiącami obrazów i milionów obrazów z etykietami, a następnie szybko utworzyć dostosowany model (w ciągu godziny na maszynie bez PROCESOR GPU). Ten samouczek skaluje się jeszcze bardziej dokładnie przy użyciu dziesiątych obrazów szkoleniowych.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Uwzględnij wstępnie szkolony model TensorFlow do potoku ML.NET
> * Uczenie i szacowanie modelu ML.NET
> * Klasyfikowanie obrazu testowego

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) . Należy pamiętać, że domyślnie konfiguracja projektu .NET dla tego samouczka dotyczy platformy .NET Core 2,2.

## <a name="what-is-transfer-learning"></a>Co to jest uczenie transferu?

Nauka transferu to proces korzystania z wiedzy zdobytej podczas rozwiązywania jednego problemu i stosowania go do innego, ale związanego z nim problemu.

Na potrzeby tego samouczka należy użyć części TensorFlow model — przeszkolonej do klasyfikowania obrazów do tysięcy kategorii — w modelu ML.NET, który klasyfikuje obrazy do 3 kategorii.

## <a name="prerequisites"></a>Wymagania wstępne

* [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

* Pakiet NuGet Microsoft.ML 1.3.1
* Pakiet NuGet Microsoft. ML. ImageAnalytics 1.3.1
* Pakiet NuGet Microsoft. ML. TensorFlow 1.3.1

* [Katalog zasobów samouczka. Plik ZIP](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [Model uczenia maszynowego InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

### <a name="deep-learning"></a>Uczenie głębokie

[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzbiór Machine Learning, które są obszarami revolutionizing, takimi jak przetwarzanie obrazów i rozpoznawanie mowy.

Modele uczenia głębokiego są przeszkolone przy użyciu dużych zestawów [danych z etykietami](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych](https://en.wikipedia.org/wiki/Artificial_neural_network) , które zawierają wiele warstw szkoleniowych. Uczenie głębokie:

* Wykonuje lepsze zadania, takie jak przetwarzanie obrazów.
* Wymaga ogromnych ilości danych szkoleniowych.

Klasyfikacja obrazu to typowe zadanie Machine Learning, które pozwala nam na automatyczne klasyfikowanie obrazów do kategorii, takich jak:

* Wykrywanie ludzkiej twarz w obrazie.
* Wykrywanie kotów a psy.

 Lub jak na następujących ilustracjach, określenie, czy obraz jest (n) jedzeniem, Zabawka lub urządzeniem:

![obraz przedstawiający obraz przedstawiający zdjęcie z obrazu Pizza Teddy](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![![](./media/image-classification/220px-Pepperoni_pizza.jpg)
](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Powyższe obrazy należą do Wikimedia Commons Attribution i są przypisywane w następujący sposób:
>
> * "220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear. jpg" przez [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) — własne grafy, CC przez-sa 2,0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster. jpg" według [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) — zadania własne, CC według-sa 3,0, https://commons.wikimedia.org/w/index.php?curid=27403

@No__t-0 jest przeszkolony do klasyfikowania obrazów do tysięcy kategorii, ale w tym samouczku należy sklasyfikować obrazy w mniejszym zestawie kategorii i tylko te kategorie. Wprowadź część elementu `transfer learning`. `transfer` Można przenieść `Inception model`możliwość rozpoznawania i klasyfikowania obrazów do nowych, ograniczonej kategorii klasyfikatora niestandardowego obrazu.

* Żywność
* Zabawki
* Wprowadzony

W tym samouczku jest [stosowany model uczenia głębokiego](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) "TensorFlow", popularny model rozpoznawania obrazów przeszkolony na zestawie danych `ImageNet`. Model TensorFlow klasyfikuje całe obrazy do tysięcy klas, takich jak "parasol", "Jersey" i "zmywarka".

Ponieważ `Inception model` został już wstępnie przeszkolony na tysiącach różnych obrazów, wewnętrznie zawiera [funkcje obrazu](https://en.wikipedia.org/wiki/Feature_(computer_vision)) niezbędne do identyfikacji obrazu. Firma Microsoft może używać tych funkcji obrazu wewnętrznego w modelu do uczenia nowego modelu z znacznie mniejszą liczbą klas.

Jak pokazano na poniższym diagramie, należy dodać odwołanie do pakietów NuGet ML.NET w aplikacjach .NET Core lub .NET Framework. W obszarze okładek ML.NET obejmuje i odwołuje się do natywnej biblioteki `TensorFlow`, która umożliwia pisanie kodu ładującego istniejący plik z modelem `TensorFlow`.

![Diagram TensorFlow transformacji ML.NET](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Klasyfikacja wieloklasowa

Po użyciu modelu rozpoczęcia TensorFlow do wyodrębnienia funkcji odpowiednich jako dane wejściowe dla klasycznego algorytmu uczenia maszynowego dodaliśmy ML.NET [klasyfikatora wieloklasowego](../resources/tasks.md#multiclass-classification).

Konkretny Trainer używany w tym przypadku jest [algorytmem regresji logistycznej](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Algorytm wdrożony przez ten Trainer działa dobrze w przypadku problemów z dużą liczbą funkcji, czyli dla modelu uczenia głębokiego działającego na danych obrazu.

### <a name="data"></a>Data

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
> *[Wikimedia Commons Attribution](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych nośników.* Pobrano 10:48, 17 października 2018 z: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Konfiguracja

### <a name="create-a-project"></a>Tworzenie projektu

1. Utwórz **aplikację konsolową .NET Core** o nazwie "TransferLearningTF".

1. Zainstaluj **pakiet NuGet Microsoft.ml**:

    * W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.
    * Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**.
    * Kliknij listę rozwijaną **wersja** , wybierz z listy pakiet **1.3.1** i wybierz przycisk **Instaluj** .
    * Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** .
    * Jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów, **Wybierz przycisk Akceptuję w oknie** dialogowym **akceptacji licencji** .
    * Powtórz te kroki dla **Microsoft. ml. ImageAnalytics v 1.3.1** i **Microsoft. ml. TensorFlow v 1.3.1**.

### <a name="download-assets"></a>Pobierz zasoby

1. Pobierz [plik zip katalogu zasobów projektu](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)i rozpakuj.

1. Skopiuj katalog do katalogu projektu *TransferLearningTF.* `assets` Ten katalog i jego podkatalogi zawierają pliki danych i obsługi (z wyjątkiem modelu, który zostanie pobrany i dodany w następnym kroku), co jest potrzebne w tym samouczku.

1. Pobierz [model rozpoczęcia](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i rozpakuj.

1. Skopiuj zawartość `inception5h` katalogu w sposób niespakowany do katalogu projektu `assets/inputs-train/inception` *TransferLearningTF* . Ten katalog zawiera model i dodatkowe pliki pomocnicze, które są odpowiednie dla tego samouczka, jak pokazano na poniższej ilustracji:

   ![Zawartość katalogu początkowej](./media/image-classification/inception-files.png)

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu zasobów i podkatalogach i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

1. Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. Dodaj następujący kod do wiersza bezpośrednio powyżej metody `Main`, aby określić ścieżki zasobów:

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. Twórz klasy dla danych wejściowych i prognoz.

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    `ImageData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:

    * `ImagePath`zawiera nazwę pliku obrazu.
    * `Label`zawiera wartość etykiety obrazu.

1. Dodaj nową klasę do projektu dla `ImagePrediction`:

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    `ImagePrediction`jest klasą przewidywania obrazów i ma następujące pola:

    * `Score`zawiera procent zaufania dla danej klasyfikacji obrazu.
    * `PredictedLabelValue`zawiera wartość dla etykiety klasyfikacji predykcyjnej obrazu.

    `ImagePrediction`jest klasą używaną do przewidywania po przeszkoleniu modelu. Ma `string` (`ImagePath`) dla ścieżki obrazu. @No__t-0 służy do ponownego użycia i nauczenia modelu. `PredictedLabelValue` Jest używany podczas przewidywania i oceny. W celu dokonania oceny dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model są używane.

### <a name="initialize-variables-in-main"></a>Inicjuj zmienne w głównym

1. `MLContext`Zainicjuj `mlContext` zmienną z nowym wystąpieniem.  Zamień wiersz na następujący kod `Main` w metodzie: `Console.WriteLine("Hello World!")`

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    [Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

### <a name="create-a-struct-for-inception-model-parameters"></a>Tworzenie struktury dla parametrów modelu rozpoczęcia

1. Model rozpoczęcia zawiera kilka parametrów, które należy przekazać. Utwórz strukturę służącą do mapowania wartości parametrów na przyjazne nazwy o następującym kodzie po prostu po metodzie `Main()`:

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Utwórz metodę narzędzia do wyświetlania

Ponieważ wyświetlasz dane obrazu i powiązane przewidywania więcej niż raz, Utwórz metodę narzędzia do wyświetlania, aby obsłużyć wyświetlanie obrazu i wyników przewidywania.

1. Utwórz metodę, tuż po strukturze, przy użyciu następującego kodu: `InceptionSettings` `DisplayResults()`

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Wypełnij treść metody `DisplayResults`:

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Tworzenie metody narzędziowej pliku. tsv

1. Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `DisplayResults()` `ReadFromTsv()`

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Wypełnij treść metody `ReadFromTsv`:

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    Kod analizuje plik `tags.tsv`, aby dodać ścieżkę pliku do nazwy pliku obrazu dla właściwości `ImagePath` i załadować ją oraz `Label` do obiektu `ImageData`.

### <a name="create-a-method-to-make-a-prediction"></a>Tworzenie metody do prognozowania

1. Utwórz metodę `ClassifySingleImage()` tuż przed metodą `DisplayResults()`, używając następującego kodu:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Utwórz obiekt `ImageData`, który zawiera w pełni kwalifikowaną ścieżkę i nazwę pliku obrazu dla jednego `ImagePath`. Dodaj następujący kod jako następny wiersz w `ClassifySingleImage()` metodzie:

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. Utwórz jedno prognozowanie, dodając następujący kod jako następny wiersz w metodzie `ClassifySingleImage`:

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    Klasa [klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który wykonuje prognozowanie jednego wystąpienia danych. Aby uzyskać prognozę, użyj metody [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) .

1. Wyświetl wynik przewidywania jako następny wiersz kodu w `ClassifySingleImage()` metodzie:

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Konstruowanie potoku modelu ML.NET

Potok modelu ML.NET jest łańcuchem szacowania. Należy pamiętać, że podczas konstruowania potoku nie jest wykonywane żadne wykonanie. Obiekty szacowania są tworzone, ale nie wykonywane.

1. Dodawanie metody w celu wygenerowania modelu

    Ta metoda jest sercem samouczka. Tworzy potok dla modelu i pociąga potok w celu utworzenia modelu ML.NET. Oblicza również model dla niektórych poprzednio niewidocznych danych testowych.

    Utwórz metodę, tuż `InceptionSettings` po `DisplayResults()` strukturze i tuż przed metodą, używając następującego kodu: `GenerateModel()`

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Dodaj szacowania do ładowania, zmiany rozmiaru i wyodrębnienia pikseli z danych obrazu:

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    Dane obrazu należy przetworzyć w formacie, którego oczekuje model TensorFlow. W takim przypadku obrazy są ładowane do pamięci, zmieniono rozmiar do spójnego rozmiaru, a piksele są wyodrębniane do wektora liczbowego.

1. Dodaj szacowania, aby załadować model TensorFlow i wypróbować go:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    Ten etap w potoku ładuje model TensorFlow do pamięci, a następnie przetwarza wektor wartości pikseli za pomocą sieci modelu TensorFlow. Zastosowanie danych wejściowych do modelu uczenia głębokiego i wygenerowanie danych wyjściowych przy użyciu modelu jest określane jako **ocenianie**. Gdy w całości korzystasz z modelu, ocenianie wykonuje wnioskowanie lub prognozowanie. 

    W takim przypadku należy użyć wszystkich modeli TensorFlow z wyjątkiem ostatniej warstwy, czyli warstwy, która wykonuje wnioskowanie. Dane wyjściowe przedostatniej warstwy są oznaczone etykietą `softmax_2_preactivation`. Dane wyjściowe tej warstwy są efektywnie wektorami funkcji, które charakteryzują się oryginalnymi obrazami wejściowymi.

    Ten wektor funkcji generowany przez model TensorFlow będzie używany jako dane wejściowe do algorytmu szkolenia ML.NET.

1. Dodaj szacowania, aby zamapować etykiety ciągów w wartości klucza danych szkoleniowych do liczby całkowitej:

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    Dołączany dalej ML.NET Trainer wymaga, aby etykiety były w formacie `key`, a nie jako dowolne ciągi. Klucz to liczba, która ma jeden do jednego mapowania do wartości ciągu.

1. Dodaj algorytm szkoleniowy ML.NET:

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. Dodaj szacowania, aby zamapować przewidywalną wartość klucza z powrotem na ciąg:

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Uczenie modelu

1. Załaduj dane szkoleniowe przy użyciu otoki [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) . Dodaj następujący kod w następnym wierszu `GenerateModel()` metody:

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.

1. Uczenie modelu z danymi załadowanymi powyżej:

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    Metoda `Fit()` pociąga za siebie model, stosując zestaw danych szkoleniowych do potoku.

## <a name="evaluate-the-accuracy-of-the-model"></a>Oceń dokładność modelu

1. Załaduj i Przekształć dane testowe, dodając następujący kod do następnego wiersza metody `GenerateModel`:

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Istnieje kilka przykładowych obrazów, których można użyć do oszacowania modelu. Podobnie jak dane szkoleniowe, muszą zostać załadowane do `IDataView`, aby mogły być przekształcane przez model.
   
1. Dodaj następujący kod do metody `GenerateModel()`, aby oszacować model:

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    Po wybraniu zestawu prognoz Metoda [szacowania ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

    * Ocenia model (porównuje wartości przewidywane z testowym zestawem danych `labels`).
    * Zwraca metryki wydajności modelu.

1. Wyświetl metryki dokładności modelu

    Użyj poniższego kodu, aby wyświetlić metryki, Udostępnij wyniki, a następnie wykonaj na nich czynności:

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    Następujące metryki są oceniane pod kątem klasyfikacji obrazów:

    * `Log-loss`-Zobacz [utrata dzienników](../resources/glossary.md#log-loss). Utrata dziennika powinna być jak najbliżej zera.
    * `Per class Log-loss`. Dla każdej klasy Dziennik ma być zbliżony do zera, jak to możliwe.

1. Dodaj następujący kod, aby zwrócić przeszkolony model jako następny wiersz:

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Uruchom aplikację.

1. Dodaj wywołanie do `GenerateModel` w metodzie `Main` po utworzeniu klasy MLContext:

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. Dodaj wywołanie do metody `ClassifySingleImage()` jako następny wiersz kodu w metodzie `Main`:

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. Uruchom aplikację konsolową (Ctrl + F5). Wyniki powinny wyglądać podobnie do poniższych danych wyjściowych.  Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.

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
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego na potrzeby klasyfikacji obrazów przez zastosowanie uczenia przeniesienia do modelu `TensorFlow` w ML.NET.

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Uwzględnij wstępnie szkolony model TensorFlow do potoku ML.NET
> * Uczenie i szacowanie modelu ML.NET
> * Klasyfikowanie obrazu testowego

Zapoznaj się z przykładem Machine Learning przykładowe repozytorium GitHub, aby poznać rozszerzoną próbkę klasyfikacji obrazów.
> [!div class="nextstepaction"]
> [dotnet/machinelearning — przykłady repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/)
