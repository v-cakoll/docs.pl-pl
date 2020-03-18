---
title: 'Samouczek: ML.NET model klasyfikacji obrazów firmy TensorFlow'
description: Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET. Model TensorFlow został przeszkolony do klasyfikowania obrazów na tysiąc kategorii. Model ML.NET korzysta z uczenia się transferu do klasyfikowania obrazów w mniej szerszych kategoriach.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 1e5478f53c82f36ddafe19e3659e2234ff9687b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241029"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Samouczek: Generowanie modelu klasyfikacji obrazów ML.NET z wstępnie przeszkolonego modelu TensorFlow

Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET.

Model TensorFlow został przeszkolony do klasyfikowania obrazów na tysiąc kategorii. Model ML.NET korzysta z części modelu TensorFlow w swoim potoku do szkolenia modelu do klasyfikowania obrazów na 3 kategorie.

Szkolenie modelu [klasyfikacji obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od podstaw wymaga ustawienia milionów parametrów, mnóstwo oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin GPU). Chociaż nie jest tak skuteczny jak szkolenie niestandardowego modelu od podstaw, uczenie się transferu pozwala na skróty tego procesu, pracując z tysiącami obrazów w porównaniu z milionami oznaczonych obrazów i dość szybko zbudować dostosowany model (w ciągu godziny na komputerze bez GPU). Ten samouczek skaluje, że proces w dół jeszcze bardziej, przy użyciu tylko kilkanaście obrazów szkoleniowych.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Włącz wstępnie przeszkolony model TensorFlow do ML.NET potoku
> * Trenuj i oceniaj model ML.NET
> * Klasyfikowanie obrazu testowego

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) Należy zauważyć, że domyślnie konfiguracja projektu .NET dla tego samouczka jest przeznaczona dla .NET core 2.2.

## <a name="what-is-transfer-learning"></a>Co to jest uczenie się transferowe?

Transfer learning to proces wykorzystywania wiedzy zdobytej podczas rozwiązywania jednego problemu i stosowania go do innego, ale powiązanego problemu.

W tym samouczku należy użyć części modelu TensorFlow - uczonego do klasyfikowania obrazów na tysiąc kategorii — w modelu ML.NET, który klasyfikuje obrazy na 3 kategorie.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".
* [Samouczek katalog zasobów . Plik ZIP](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [Model uczenia maszynowego InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

### <a name="deep-learning"></a>Uczenie głębokie

[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzbiór uczenia maszynowego, który rewolucjonizuje obszary takie jak wzmożenie komputerowe i rozpoznawanie mowy.

Modele uczenia głębokiego są trenowane przy użyciu dużych zestawów [oznaczonych danych](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych,](https://en.wikipedia.org/wiki/Artificial_neural_network) które zawierają wiele warstw uczenia się. Głębokie uczenie się:

* Działa lepiej w niektórych zadaniach, takich jak Wzmożenie komputera.
* Wymaga ogromnych ilości danych szkoleniowych.

Klasyfikacja obrazów jest typowym zadaniem uczenia maszynowego, które pozwala nam automatycznie klasyfikować obrazy do kategorii, takich jak:

* Wykrywanie ludzkiej twarzy na obrazie, czy nie.
* Wykrywanie kotów vs. psów.

 Lub jak na poniższych obrazach, określenie, czy obraz jest a(n) jedzeniem, przekąską lub urządzeniem:

![obraz](./media/image-classification/220px-Pepperoni_pizza.jpg)
![pizzy](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![obraz teddy misia obraz toster obrazu](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Powyższe obrazy należą do Wikimedia Commons i są przypisywane w następujący sposób:
>
> * "220px-Pepperoni_pizza.jpg" Domena https://commons.wikimedia.org/w/index.php?curid=79505publiczna, ,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA https://commons.wikimedia.org/w/index.php?curid=481662.0, .
> * "193px-Broodrooster.jpg" [Autor: M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Własna praca, CC BY-SA 3.0,https://commons.wikimedia.org/w/index.php?curid=27403

Jest `Inception model` przeszkolony do klasyfikowania obrazów na tysiąc kategorii, ale w tym samouczku musisz sklasyfikować obrazy w mniejszym zestawie kategorii i tylko tych kategoriach. Wprowadź `transfer` część `transfer learning`pliku . Można przenieść `Inception model`zdolność rozpoznawania i klasyfikowania obrazów do nowych ograniczonych kategorii niestandardowego klasyfikatora obrazów.

* Żywności
* Zabawka
* Urządzenia

W tym samouczku [użyto](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) modelu uczenia głębokiego modelu TensorFlow, `ImageNet` popularnego modelu rozpoznawania obrazów uczonego w zestawie danych. Model TensorFlow klasyfikuje całe obrazy na tysiąc klas, takich jak "Parasol", "Jersey" i "Zmywarka".

Ponieważ `Inception model` został już wstępnie przeszkolony na tysiącach różnych obrazów, wewnętrznie zawiera [funkcje obrazu](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potrzebne do identyfikacji obrazu. Możemy skorzystać z tych wewnętrznych funkcji obrazu w modelu, aby nabyć nowy model ze znacznie mniejszą liczbą klas.

Jak pokazano na poniższym diagramie, należy dodać odwołanie do pakietów ML.NET NuGet w aplikacjach .NET Core lub .NET Framework. Pod okładkami ML.NET zawiera i `TensorFlow` odwołuje się do macierzystej biblioteki, `TensorFlow` która umożliwia pisanie kodu ładowanego istniejącego pliku uczonego modelu.

![Diagram transformatorem TensorFlow ML.NET Arch](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Klasyfikacja wieloklasowa

Po użyciu modelu powstania TensorFlow do wyodrębniania funkcji odpowiednich jako dane wejściowe dla klasycznego algorytmu uczenia maszynowego, dodajemy ML.NET [klasyfikatora wieloklasowego.](../resources/tasks.md#multiclass-classification)

Specyficzny trener używany w tym przypadku jest [algorytm regresji logistycznej multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Algorytm zaimplementowany przez tego trenera dobrze sprawdza problemy z dużą liczbą funkcji, co ma miejsce w przypadku modelu uczenia głębokiego działającego na danych obrazu.

### <a name="data"></a>Dane

Istnieją dwa źródła danych: `.tsv` plik i pliki obrazów.  Plik `tags.tsv` zawiera dwie kolumny: pierwsza z `ImagePath` nich jest zdefiniowana jako, a druga `Label` odpowiada obrazowi. Poniższy przykładowy plik nie ma wiersza nagłówka i wygląda następująco:

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

Obrazy szkoleniowe i testowe znajdują się w folderach zasobów, które zostaną pobrane w pliku zip. Te obrazy należą do Wikimedia Commons.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych mediów.* Pobrane 10:48, 17 października 2018 od: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toasterhttps://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Konfiguracja

### <a name="create-a-project"></a>Tworzenie projektu

1. Utwórz **aplikację .NET Core Console** o nazwie "TransferLearningTF".

1. Zainstaluj **pakiet Microsoft.ML NuGet:**

    * W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.
    * Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**.
    * Kliknij listę rozwijaną **Wersja,** wybierz pakiet **1.4.0** na liście i wybierz przycisk **Zainstaluj.**
    * Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian.**
    * Wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencji dla wymienionych pakietów.
    * Powtórz te kroki dla **firm Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** i **Microsoft.ML.TensorFlow v1.4.0**.

### <a name="download-assets"></a>Pobieranie zasobów

1. Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)i rozpakuj.

1. Skopiuj `assets` katalog do katalogu projektów *TransferLearningTF.* Ten katalog i jego podkatalogi zawierają dane i pliki wsparcia (z wyjątkiem modelu Inception, który pobierzesz i dodasz w następnym kroku) potrzebnych do tego samouczka.

1. Pobierz [model Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i rozpakuj.

1. Skopiuj `inception5h` zawartość katalogu po prostu rozpakowany `assets/inception` do katalogu projektu *TransferLearningTF.* Ten katalog zawiera model i dodatkowe pliki pomocy technicznej potrzebne w tym samouczku, jak pokazano na poniższym obrazku:

   ![Zawartość katalogu początkowego](./media/image-classification/inception-files.png)

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu i podkatalogach zasobów i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

1. Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić ścieżki zasobów:

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. Tworzenie klas dla danych wejściowych i prognoz.

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    `ImageData`jest klasą danych wejściowych <xref:System.String> obrazu i ma następujące pola:

    * `ImagePath`zawiera nazwę pliku obrazu.
    * `Label`zawiera wartość etykiety obrazu.

1. Dodaj nową klasę do `ImagePrediction`projektu dla:

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction`jest klasą przewidywania obrazu i ma następujące pola:

    * `Score`zawiera procent ufności dla danej klasyfikacji obrazu.
    * `PredictedLabelValue`zawiera wartość dla etykiety klasyfikacji przewidywanego obrazu.

    `ImagePrediction`jest klasą używaną do przewidywania po przeszkoloniu modelu. Ma `string` (`ImagePath`) dla ścieżki obrazu. Służy `Label` do ponownego użycia i przeszkolenia modelu. Jest `PredictedLabelValue` używany podczas przewidywania i oceny. Do oceny dane wejściowe z danymi treningowymi, przewidywane wartości i model są używane.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w main

1. Inicjuj zmienną `mlContext` z `MLContext`nowym wystąpieniem .  Zastąp `Console.WriteLine("Hello World!")` wiersz następującym `Main` kodem w metodzie:

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    [Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji `mlContext` ML.NET, a inicjowanie tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

### <a name="create-a-struct-for-inception-model-parameters"></a>Tworzenie struktury parametrów modelu początkowego

1. Model Inception ma kilka parametrów, które musisz przekazać. Utwórz strukturę, aby zamapować wartości parametrów na przyjazne `Main()` nazwy za pomocą następującego kodu, tuż po metodzie:

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Tworzenie metody narzędzia wyświetlania

Ponieważ dane obrazu i powiązane prognozy będą wyświetlane więcej niż jeden raz, utwórz metodę narzędzia wyświetlania do obsługi wyświetlania obrazu i wyników przewidywania.

1. Utwórz `DisplayResults()` metodę, tuż `InceptionSettings` po strukturze, używając następującego kodu:

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Wypełnij treść `DisplayResults` metody:

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Tworzenie metody narzędzia pliku tsv

1. Utwórz `ReadFromTsv()` metodę, tuż `DisplayResults()` po tej metodzie, używając następującego kodu:

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Wypełnij treść `ReadFromTsv` metody:

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    Kod analizuje za pośrednictwem `tags.tsv` pliku, aby dodać ścieżkę pliku `ImagePath` do nazwy pliku `Label` obrazu `ImageData` dla właściwości i załadować go i do obiektu.

### <a name="create-a-method-to-make-a-prediction"></a>Tworzenie metody przewidywania

1. Utwórz `ClassifySingleImage()` metodę tuż `DisplayResults()` przed metodą, używając następującego kodu:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Utwórz `ImageData` obiekt zawierający w pełni kwalifikowaną nazwę pliku `ImagePath`ścieżki i obrazu dla pojedynczego pliku . Dodaj następujący kod jako następne `ClassifySingleImage()` wiersze w metodzie:

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. Dokonaj pojedynczego przewidywania, dodając następujący kod jako `ClassifySingleImage` następny wiersz w metodzie:

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    Aby uzyskać przewidywanie, należy użyć [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) metody. [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

1. Wyświetl wynik przewidywania jako następny wiersz `ClassifySingleImage()` kodu w metodzie:

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Konstruowanie potoku modelu ML.NET

Potok modelu ML.NET jest łańcuchem estymatorów. Należy zauważyć, że wykonanie nie dzieje się podczas budowy rurociągu. Obiekty estymatora są tworzone, ale nie są wykonywane.

1. Dodawanie metody generowania modelu

    Ta metoda jest sercem samouczka. Tworzy potok dla modelu i szkoli potoku do produkcji modelu ML.NET. Ocenia również model w stosunku do niektórych wcześniej niewidocznych danych testowych.

    Utwórz `GenerateModel()` metodę tuż `InceptionSettings` po strukturze i `DisplayResults()` tuż przed metodą, używając następującego kodu:

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Dodaj estymatory, aby załadować, zmienić rozmiar i wyodrębnić piksele z danych obrazu:

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    Dane obrazu muszą zostać przetworzone w formacie, który oczekuje model TensorFlow. W takim przypadku obrazy są ładowane do pamięci, zmieniane na spójny rozmiar, a piksele są wyodrębniane do wektora numerycznego.

1. Dodaj estymatora, aby załadować model TensorFlow i zdobądź go:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    Ten etap w potoku ładuje model TensorFlow do pamięci, a następnie przetwarza wektor wartości pikseli za pośrednictwem sieci modelu TensorFlow. Stosowanie danych wejściowych do modelu uczenia głębokiego i generowanie danych wyjściowych przy użyciu modelu jest określane jako **scoring**. Korzystając z modelu w całości, ocenianie sprawia, że wnioskowanie lub przewidywanie.

    W takim przypadku należy użyć wszystkich modelu TensorFlow z wyjątkiem ostatniej warstwy, która jest warstwą, która sprawia, że wnioskowanie. Dane wyjściowe przedostatniej warstwy są `softmax_2_preactivation`oznaczone . Dane wyjściowe tej warstwy są skutecznie wektorem obiektów charakteryzujących oryginalne obrazy wejściowe.

    Ten wektor funkcji generowany przez model TensorFlow będzie używany jako dane wejściowe do algorytmu szkolenia ML.NET.

1. Dodaj estymator, aby zamapować etykiety ciągów w danych szkoleniowych na wartości klucza całkowitego:

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    Trener ML.NET, który jest dołączany dalej `key` wymaga jego etykiety być w formacie, a nie arbitralne ciągi. Klucz jest liczbą, która ma mapowanie jeden do jednego do wartości ciągu.

1. Dodaj algorytm szkolenia ML.NET:

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. Dodaj estymatora, aby odwzorować przewidywaną wartość klucza z powrotem na ciąg:

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Uczenie modelu

1. Załaduj dane szkoleniowe przy użyciu otoki [LoadFromTextFile.](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) Dodaj następujący kod jako następny `GenerateModel()` wiersz w metodzie:

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    Dane w ML.NET jest reprezentowana jako [klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`to elastyczny i skuteczny sposób opisywania danych tabelarycznych (numerycznych i tekstowych). Dane mogą być ładowane z pliku tekstowego lub w czasie rzeczywistym `IDataView` (na przykład bazy danych SQL lub plików dziennika) do obiektu.

1. Przeszkolić model z danymi załadowanymi powyżej:

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    Metoda `Fit()` szkoli model, stosując zestaw danych szkolenia do potoku.

## <a name="evaluate-the-accuracy-of-the-model"></a>Ocena dokładności modelu

1. Załaduj i przekształcaj dane testowe, dodając następujący `GenerateModel` kod do następnego wiersza metody:

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Istnieje kilka przykładowych obrazów, których można użyć do oceny modelu. Podobnie jak dane szkoleniowe, muszą one `IDataView`zostać załadowane do , tak, że mogą być przekształcane przez model.

1. Dodaj następujący kod `GenerateModel()` do metody, aby ocenić model:

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    Po ustawieniu przewidywania metoda [Evaluate():](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A)

    * Ocenia model (porównuje przewidywane wartości z testowym `labels`zestawem danych).
    * Zwraca metryki wydajności modelu.

1. Wyświetlanie metryk dokładności modelu

    Użyj następującego kodu, aby wyświetlić metryki, udostępnić wyniki, a następnie działać na nich:

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    Dla klasyfikacji obrazów oceniane są następujące metryki:

    * `Log-loss`- patrz [Utrata dziennika](../resources/glossary.md#log-loss). Chcesz, aby strata dziennika była jak najbardziej zbliżony do zera.
    * `Per class Log-loss`. Chcesz, aby na klasę Strata dziennika była jak najbliżej zera, jak to możliwe.

1. Dodaj następujący kod, aby zwrócić uczonego modelu jako następny wiersz:

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Uruchom aplikację!

1. Dodaj wywołanie `GenerateModel` w `Main` metodzie po utworzeniu mlcontext klasy:

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. Dodaj wywołanie `ClassifySingleImage()` do metody jako następny wiersz `Main` kodu w metodzie:

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. Uruchom aplikację konsoli (Ctrl + F5). Wyniki powinny być podobne do następujących danych wyjściowych.  Mogą zostać wyświetlone ostrzeżenia lub wiadomości przetwarzania, ale te komunikaty zostały usunięte z następujących wyników dla jasności.

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego dla klasyfikacji obrazów, stosując naukę transferu do `TensorFlow` modelu w ML.NET.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF)

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Włącz wstępnie przeszkolony model TensorFlow do ML.NET potoku
> * Trenuj i oceniaj model ML.NET
> * Klasyfikowanie obrazu testowego

Zapoznaj się z przykładów uczenia maszynowego Repozytorium GitHub do eksplorowania rozwiniętego przykładu klasyfikacji obrazów.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples Repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/)
