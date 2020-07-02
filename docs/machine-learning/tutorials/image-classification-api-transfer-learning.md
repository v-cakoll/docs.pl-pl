---
title: 'Samouczek: automatyczna Inspekcja wizualizacji przy użyciu uczenia przenoszenia'
description: W tym samouczku pokazano, jak używać uczenia przeniesienia do uczenia modelu uczenia głębokiego TensorFlow w ML.NET przy użyciu interfejsu API wykrywania obrazów do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niepękniętych.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 17fbb8c6714f3af47c0b554aec2c53c8046021bb
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803745"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Samouczek: automatyczne Inspekcja wizualizacji przy użyciu uczenia transferowego za pomocą interfejsu API klasyfikacji obrazów ML.NET

Dowiedz się, jak uczenie niestandardowego modelu uczenia głębokiego przy użyciu uczenia transferu, przedTensorFlowego modelu i interfejsu API klasyfikacji obrazów ML.NET do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niepękniętych.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się więcej o interfejsie API klasyfikacji obrazów ML.NET
> - Omówienie modelu przedniego
> - Korzystanie z uczenia transferowego do uczenia niestandardowego modelu klasyfikacji obrazów TensorFlow
> - Klasyfikowanie obrazów przy użyciu modelu niestandardowego

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

## <a name="image-classification-transfer-learning-sample-overview"></a>Omówienie przykładu szkoleniowego dotyczącego przenoszenia klasyfikacji obrazów

Ten przykład jest aplikacją konsolową w języku C# .NET Core, która klasyfikuje obrazy przy użyciu preszkolenego modelu TensorFlow uczenia głębokiego. Kod dla tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) w witrynie GitHub.

## <a name="understand-the-problem"></a>Omówienie problemu

Klasyfikacja obrazu jest problemem z obsługą komputera. Klasyfikacja obrazu pobiera obraz jako dane wejściowe i klasyfikuje go do wskazanej klasy. Niektóre scenariusze, w których klasyfikacja obrazów jest przydatna:

- Rozpoznawanie twarzy
- Wykrywanie rozpoznawania emocji
- Diagnoza medyczna
- Wykrywanie punktu orientacyjnego

W tym samouczku przedstawiono niestandardowy model klasyfikacji obrazów służący do przeprowadzania zautomatyzowanej inspekcji wizualizacji w celu identyfikowania struktur, które są uszkodzone przez pęknięcia.

## <a name="mlnet-image-classification-api"></a>Interfejs API klasyfikacji obrazów ML.NET

ML.NET zapewnia różne sposoby wykonywania klasyfikacji obrazów. W tym samouczku zastosowana jest nauka transferu przy użyciu interfejsu API klasyfikacji obrazu. Interfejs API klasyfikacji obrazów korzysta z [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), biblioteki niskiego poziomu, która zapewnia powiązania języka C# dla interfejsu API TensorFlow C++.

## <a name="what-is-transfer-learning"></a>Co to jest uczenie transferu?

Nauka przenoszenia dotyczy wiedzy uzyskanej w wyniku rozwiązywania jednego problemu z innym powiązanym problemem.

Uczenie modelu uczenia głębokiego od podstaw wymaga ustawienia kilku parametrów, dużej ilości danych szkoleniowych z etykietą i ogromnej ilości zasobów obliczeniowych (setki godzin procesora GPU). Przy użyciu wstępnie przemieszczonego modelu wraz z uczeniem transferu można przystąpić do tworzenia skrótów do procesu szkolenia.

## <a name="training-process"></a>Proces uczenia

Interfejs API klasyfikacji obrazów uruchamia proces szkolenia, ładując wstępnie przeszkolony model TensorFlow. Proces uczenia składa się z dwóch kroków:

1. Faza wąskiego gardła
2. Faza szkoleniowa

![Kroki szkoleniowe](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Faza wąskiego gardła

W fazie wąskiego gardła zestaw obrazów szkoleniowych jest ładowany, a wartości pikseli są używane jako dane wejściowe lub funkcje dla zamrożonych warstw modelu przedniego. Zablokowane warstwy obejmują wszystkie warstwy w sieci neuronowych do przedstawionej warstwy, nieformalnie znanej jako warstwa wąskiego gardła. Te warstwy są określane jako zamrożone, ponieważ na tych warstwach nie ma żadnego szkolenia i operacje są przekazywane. Jest to zamrożone warstwy, w których są obliczane wzorce niższego poziomu, które pomagają w odróżnieniu od różnych klas. Im większa liczba warstw, tym większa intensywnie jest ten krok. Na szczęście, ponieważ jest to jednorazowe obliczenie, wyniki mogą być buforowane i używane w późniejszym czasie podczas eksperymentowania z innymi parametrami.

### <a name="training-phase"></a>Faza szkoleniowa

Gdy obliczane są wartości wyjściowe z fazy wąskiego gardła, są one używane jako dane wejściowe do ponownego uczenia ostatniej warstwy modelu. Ten proces jest iteracyjny i uruchamiany przez liczbę razy określony przez parametry modelu. W każdym przebiegu są oceniane straty i dokładność. Następnie wprowadzane są odpowiednie zmiany w celu ulepszenia modelu, aby zminimalizować stratę i zmaksymalizować dokładność. Po zakończeniu szkolenia dwa formaty modeli są wyjściowe. Jednym z nich jest `.pb` wersja modelu, a druga to `.zip` ml.neta wersja modelu. W przypadku pracy w środowiskach obsługiwanych przez ML.NET zaleca się użycie `.zip` wersji modelu. Jednak w środowiskach, w których ML.NET nie jest obsługiwana, dostępna jest opcja korzystania z tej `.pb` wersji.

## <a name="understand-the-pretrained-model"></a>Omówienie modelu przedniego

Wstępnie przemieszczony model używany w tym samouczku to 101-warstwowy model sieci resztkowej (ResNet) w wersji 2. Oryginalny model jest przeszkolony do klasyfikowania obrazów do tysięcy kategorii. Model przyjmuje jako dane wejściowe obraz o rozmiarze 224 x 224 i wyświetla prawdopodobieństwa klasy dla każdej klasy, w której jest szkolony. Część tego modelu służy do uczenia nowego modelu przy użyciu obrazów niestandardowych w celu wprowadzania prognoz między dwiema klasami.

## <a name="create-console-application"></a>Tworzenie aplikacji konsolowej

Teraz, gdy znasz już ogólną wiedzę o uczeniu przenoszenia i interfejsie API klasyfikacji obrazów, jest to czas na skompilowanie aplikacji.

1. Utwórz **aplikację konsolową w języku C# .NET Core** o nazwie "DeepLearning_ImageClassification_Binary".
1. Zainstaluj pakiet NuGet **Microsoft.ml** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.
    1. Wybierz pozycję "nuget.org" jako źródło pakietu.
    1. Wybierz kartę **Przeglądaj**.
    1. Zaznacz pole wyboru **Uwzględnij wersję wstępną** .
    1. Wyszukaj **Microsoft.ml**.
    1. Wybierz przycisk **Instaluj** .
    1. Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.
    1. Powtórz te kroki dla pakietów NuGet **Microsoft. ml. Vision**, **SciSharp. TensorFlow. Redist**i **Microsoft. ml. ImageAnalytics** .

### <a name="prepare-and-understand-the-data"></a>Przygotuj i poznanie danych

> [!NOTE]
> Zestawy danych dla tego samouczka pochodzą z Maguire, wytłoków; Dorafshan, Sattar; i Thomas, Robert J., "SDNET2018: zestaw danych obrazu dla konkretnych pęknięć dla aplikacji Machine Learning" (2018). Przeglądaj wszystkie zestawy danych. Papier 48. <https://digitalcommons.usu.edu/all_datasets/48>

SDNET2018 jest zestawem danych obrazu zawierającym adnotacje dla popękanych i niepękniętych struktur (talie mostków, ściany i Pavement).

![Przykłady dla talii mostka SDNET2018 DataSet](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Dane są zorganizowane w trzech podkatalogach:

- D zawiera obrazy talii mostków
- P zawiera obrazy Pavement
- W zawiera obrazy ściany

Każdy z tych podkatalogów zawiera dwa dodatkowe podkatalogi z prefiksem:

- C jest prefiksem używanym na potrzeby powierzchni pękniętych
- U to prefiks używany dla niepękanych powierzchni

W tym samouczku używane są tylko obrazy talii mostków.

1. Pobierz [zestaw danych](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) i rozpakuj.
1. Utwórz katalog o nazwie "Assets" w projekcie, aby zapisać pliki zestawu danych.
1. Skopiuj podkatalogi *CD* i *ud* z ostatnio odpakowanego katalogu do katalogu *zasobów* .

### <a name="create-input-and-output-classes"></a>Tworzenie klas wejściowych i wyjściowych

1. Otwórz plik *program.cs* i Zastąp istniejące `using` instrukcje na początku pliku następującym:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Poniżej `Program` klasy w *program.cs*Utwórz klasę o nazwie `ImageData` . Ta klasa jest używana do reprezentowania początkowo załadowanych danych.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`zawiera następujące właściwości:

    - `ImagePath`to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.
    - `Label`jest kategorią, do której należy obraz. Jest to wartość do przewidywania.

1. Tworzenie klas danych wejściowych i wyjściowych

    1. Poniżej `ImageData` klasy Zdefiniuj schemat danych wejściowych w nowej klasie o nazwie `ModelInput` .

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`zawiera następujące właściwości:

        - `Image`jest `byte[]` reprezentacją obrazu. Model oczekuje, że dane obrazu mają być tego typu dla szkolenia.
        - `LabelAsKey`jest cyfrową reprezentacją `Label` .
        - `ImagePath`to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.
        - `Label`jest kategorią, do której należy obraz. Jest to wartość do przewidywania.

        Tylko `Image` i `LabelAsKey` są używane do uczenia modelu i podejmowania prognoz. `ImagePath`Właściwości i `Label` są utrzymywane dla wygody dostępu do oryginalnej nazwy i kategorii pliku obrazu.

    1. Następnie poniżej `ModelInput` klasy Zdefiniuj schemat danych wyjściowych w nowej klasie o nazwie `ModelOutput` .

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`zawiera następujące właściwości:

        - `ImagePath`to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.
        - `Label`jest oryginalną kategorią, do której należy obraz. Jest to wartość do przewidywania.
        - `PredictedLabel`jest wartością przewidywaną przez model.

        Podobnie jak `ModelInput` , tylko `PredictedLabel` jest wymagana do przewidywania prognoz, ponieważ zawiera prognozę dokonaną przez model. `ImagePath`Właściwości i `Label` są zachowywane dla wygody dostępu do oryginalnej nazwy i kategorii pliku obrazu.

### <a name="create-workspace-directory"></a>Utwórz katalog obszaru roboczego

Gdy dane szkoleniowe i weryfikacyjne nie zmieniają się często, dobrym rozwiązaniem jest buforowanie obliczonych wartości wąskich gardeł dla dalszych przebiegów.

1. W projekcie Utwórz nowy katalog o nazwie *obszar roboczy* do przechowywania obliczonych wartości wąskich gardeł i `.pb` wersji modelu.

### <a name="define-paths-and-initialize-variables"></a>Zdefiniuj ścieżki i zainicjuj zmienne

1. Wewnątrz `Main` metody Zdefiniuj lokalizację zasobów, obliczone wartości wąskich gardeł i `.pb` wersję modelu.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Zainicjuj `mlContext` zmienną z nowym wystąpieniem [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie MLContext tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

## <a name="load-the-data"></a>Ładowanie danych

### <a name="create-data-loading-utility-method"></a>Metoda tworzenia narzędzia do ładowania danych

Obrazy są przechowywane w dwóch podkatalogach. Przed załadowaniem danych należy je sformatować w postaci listy `ImageData` obiektów. W tym celu należy utworzyć `LoadImagesFromDirectory` metodę poniżej `Main` metody.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Wewnątrz `LoadImagesDirectory` Dodaj następujący kod, aby uzyskać wszystkie ścieżki plików z podkatalogów:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Następnie wykonaj iterację poszczególnych plików przy użyciu `foreach` instrukcji.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. Wewnątrz `foreach` instrukcji Sprawdź, czy rozszerzenia plików są obsługiwane. Interfejs API klasyfikacji obrazów obsługuje formaty JPEG i PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Następnie Pobierz etykietę dla tego pliku. Jeśli `useFolderNameAsLabel` parametr jest ustawiony na `true` , katalog nadrzędny, w którym zapisano plik, jest używany jako etykieta. W przeciwnym razie oczekuje, że etykieta będzie prefiksem nazwy pliku lub samej nazwy pliku.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Na koniec Utwórz nowe wystąpienie `ModelInput` .

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Przygotowywanie danych

1. Z powrotem w `Main` metodzie Użyj `LoadFromDirectory` metody narzędziowej, aby uzyskać listę obrazów używanych do szkoleń.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Następnie załaduj obrazy do [`IDataView`](xref:Microsoft.ML.IDataView) przy użyciu [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Dane są ładowane w kolejności, w której zostały odczytane z katalogów. Aby zrównoważyć dane, należy je losowo użyć [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) metody.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Modele uczenia maszynowego oczekują danych wejściowych w formacie liczbowym. W związku z tym, należy wykonać pewne czynności wstępne dotyczące danych przed szkoleniem. Utwórz [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) składową [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) i `LoadRawImageBytes` transformacje. `MapValueToKey`Transformacja przyjmuje wartość kategorii w `Label` kolumnie, konwertuje ją na wartość liczbową `KeyType` i zapisuje ją w nowej kolumnie o nazwie `LabelAsKey` . `LoadImages`Pobiera wartości z `ImagePath` kolumny wraz z `imageFolder` parametrem służącym do ładowania obrazów do szkoleń.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby zastosować dane do, `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) a następnie [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) metodę, która zwraca [`IDataView`](xref:Microsoft.ML.IDataView) zawierający wstępnie przetworzone dane.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Aby szkolić model, ważne jest posiadanie zestawu danych szkoleniowych oraz zestawu danych sprawdzania poprawności. Model jest szkolony na zestawie szkoleniowym. Jak również przewidywania dotyczące niewidocznych danych są mierzone przez wydajność względem zestawu walidacji. W oparciu o wyniki tej wydajności model dostosowuje się do tego, co pobrało w wysiłku, aby zwiększyć. Zestaw walidacji może pochodzić z dzielenia oryginalnego zestawu danych lub z innego źródła, które zostało już przeznaczone do tego celu. W tym przypadku wstępnie przetworzony zestaw danych jest podzielony na szkolenia, walidację i zestawy testów.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Powyższy przykład kodu wykonuje dwa podziały. Po pierwsze przetworzone dane są podzielone i 70% jest używane do uczenia, podczas gdy pozostały 30% jest używany do walidacji. Następnie zestaw walidacji 30% jest podzielona na weryfikację i zestawy testów, gdzie 90% jest używany do walidacji, a 10% jest używany do testowania.

    Aby myśleć o przeznaczeniu tych partycji danych, należy wziąć pod uwagę egzamin. Podczas badania na egzaminie możesz przejrzeć notatki, książki lub inne zasoby, aby uzyskać opanujesz na temat koncepcji, które znajdują się na egzaminie. Jest to zestaw pociągów. Następnie możesz skorzystać z egzaminu makiety, aby zweryfikować swoją wiedzę. Jest to miejsce, w którym zestaw walidacji jest dostępny. Chcesz sprawdzić, czy masz dobre opanujesz koncepcji przed rozpoczęciem rzeczywistego egzaminu. W oparciu o te wyniki należy zwrócić uwagę na to, co się stało lub które nie jest dobrze zrozumiałe i uwzględnić zmiany podczas przeglądania dla rzeczywistego egzaminu. Na koniec przejęcie egzaminu. Jest to zestaw testów używany przez. Nie widzisz już pytań dotyczących egzaminu i teraz korzystamy z tego, co uczysz się od szkoleń i weryfikacji, aby od razu zastosować swoją wiedzę do tego zadania.

1. Przypisz partycje ich odpowiednie wartości dla danych dotyczących pouczenia, sprawdzania poprawności i testowania.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Definiowanie potoku szkoleniowego

Szkolenia modeli składają się z kilku kroków. Najpierw interfejs API klasyfikacji obrazu jest używany do uczenia modelu. Następnie kodowane etykiety w `PredictedLabel` kolumnie są konwertowane z powrotem na oryginalną wartość kategorii przy użyciu `MapKeyToValue` transformacji.

1. Utwórz nową zmienną do przechowywania zestawu wymaganych i opcjonalnych parametrów dla `ImageClassificationTrainer` .

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    `ImageClassificationTrainer`Przyjmuje kilka parametrów opcjonalnych:

    - `FeatureColumnName`jest kolumną używaną jako dane wejściowe dla modelu.
    - `LabelColumnName`to kolumna, dla której ma zostać przewidywalna wartość.
    - `ValidationSet`[`IDataView`](xref:Microsoft.ML.IDataView)zawiera dane sprawdzania poprawności.
    - `Arch`definiuje, które z premieszczonych architektur modelu mają być używane. W tym samouczku jest stosowana 101-warstwowa odmiana modelu ResNetv2.
    - `MetricsCallback`wiąże funkcję w celu śledzenia postępu podczas szkolenia.
    - `TestOnTrainSet`nakazuje modelowi pomiar wydajności względem zestawu szkoleniowego, gdy nie ma zestawu walidacji.
    - `ReuseTrainSetBottleneckCachedValues`informuje model, czy należy używać buforowanych wartości z fazy wąskich gardeł w kolejnych uruchomieniach. Faza wąskich gardeł to jednokrotne obliczenie przekazujące, które jest intensywnie czasochłonne podczas pierwszego wykonywania. Jeśli dane szkoleniowe nie zmieniają się i chcesz eksperymentować przy użyciu innej liczby epok lub rozmiaru partii, użycie pamięci podręcznej znacznie zmniejsza ilość czasu wymaganego do uczenia modelu.
    - `ReuseValidationSetBottleneckCachedValues`jest podobny do tego `ReuseTrainSetBottleneckCachedValues` , że w tym przypadku jest przeznaczony dla zestawu danych walidacji.
    - `WorkspacePath`Określa katalog, w którym mają być przechowywane obliczone wartości wąskich gardeł i `.pb` wersja modelu.

1. Zdefiniuj [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) potok szkoleniowy, który składa się zarówno z, `mapLabelEstimator` jak i `ImageClassificationTrainer` .

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody do uczenia modelu.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Korzystanie z modelu

Teraz, gdy korzystasz z modelu, możesz go użyć do klasyfikowania obrazów.

Poniżej `Main` metody Utwórz nową metodę narzędzia wywołana, `OutputPrediction` Aby wyświetlić informacje o prognozie w konsoli programu.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Klasyfikowanie pojedynczego obrazu

1. Dodaj nową metodę o nazwie `ClassifySingleImage` poniżej `Main` metody, aby utworzyć i wyprowadzić prognozę pojedynczego obrazu.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wewnątrz `ClassifySingleImage` metody. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)Jest wygodnym interfejsem API, który pozwala na przekazywanie danych, a następnie przeprowadzenie prognozowania na jednym wystąpieniu.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Aby uzyskać dostęp do jednego `ModelInput` wystąpienia, należy przekonwertować go `data` [`IDataView`](xref:Microsoft.ML.IDataView) na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) za pomocą [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody, a następnie pobrać pierwsze obserwacje.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Użyj [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) metody do klasyfikowania obrazu.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Wyprowadzanie danych wyjściowych do konsoli za pomocą `OutputPrediction` metody.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Wewnątrz `Main` metody wywołania `ClassifySingleImage` przy użyciu zestawu testów obrazu.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Klasyfikowanie wielu obrazów

1. Dodaj nową metodę o nazwie `ClassifyImages` poniżej `ClassifySingleImage` metody, aby utworzyć i wyprowadzić wiele prognoz obrazu.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) zawierający przewidywania przy użyciu [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody. Dodaj następujący kod wewnątrz `ClassifyImages` metody.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Aby wykonać iterację prognoz, przekonwertuj na `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) użycie [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody, a następnie Pobierz pierwsze 10 obserwacji.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Wykonaj iterację i wyprowadzaj oryginalne i przewidywane etykiety dla prognoz.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Na koniec wewnątrz `Main` metody Wywołaj `ClassifyImages` przy użyciu zestawu testów obrazu.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Uruchom aplikację konsolową. Dane wyjściowe powinny być podobne do poniższych. Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości. W przypadku zwięzłości dane wyjściowe zostały zagęszczone.

**Faza wąskiego gardła**

Żadna wartość nie jest drukowana dla nazwy obrazu, ponieważ obrazy są ładowane jako z `byte[]` tego powodu nie istnieje nazwa obrazu do wyświetlenia.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Faza szkoleniowa**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Klasyfikowanie obrazów wyjściowych**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Po inspekcji *7001-220.jpg* obrazu można zobaczyć, że w rzeczywistości nie jest to pęknięte.

![Obraz zestawu danych SDNET2018 służący do przewidywania](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Gratulacje! Pomyślnie skompilowano model uczenia głębokiego na potrzeby klasyfikowania obrazów.

### <a name="improve-the-model"></a>Ulepszanie modelu

Jeśli wyniki Twojego modelu nie są zadowalające, możesz spróbować zwiększyć jego wydajność, wykonując kilka następujących metod:

- **Więcej danych**: więcej przykładów, z których uzyskuje się model, tym lepiej. Pobierz pełny [zestaw danych SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) i użyj go do uczenia się.
- **Rozszerzanie danych**: typową techniką dodawania odmiany do danych jest rozszerzanie danych przez pobranie obrazu i zastosowanie różnych transformacji (Obróć, przerzuć, Shift, Kadruj). Spowoduje to dodanie bardziej zróżnicowanych przykładów dla modelu, z których można się uczyć.
- **Uczenie się przez dłuższy czas**: im dłużej są nauczeni, tym bardziej dostrojony model. Zwiększenie liczby epok może zwiększyć wydajność modelu.
- **Eksperymentowanie z parametrami funkcji Hyper-Parameters**: Oprócz parametrów używanych w tym samouczku, inne parametry można dostrajać w celu zwiększenia wydajności. Zmiana stawki szkoleniowej, która określa wielkość aktualizacji dokonanych w modelu po każdej epoki, może zwiększyć wydajność.
- **Użyj innej architektury modelu**: w zależności od tego, jak wyglądają Twoje dane, model, który najlepiej uczy się, że jego funkcje mogą się różnić. Jeśli nie masz zadowalającej wydajności modelu, spróbuj zmienić architekturę.

### <a name="additional-resources"></a>Dodatkowe zasoby

- [Uczenie głębokie a Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Następne kroki

W tym samouczku pokazano, jak utworzyć niestandardowy model uczenia głębokiego przy użyciu uczenia przeniesienia, premieszczony model klasyfikacji obrazu TensorFlow oraz interfejs API klasyfikacji obrazów ML.NET do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niesilnie.

Przejdź do następnego samouczka, aby dowiedzieć się więcej.

> [!div class="nextstepaction"]
> [Wykrywanie obiektów](object-detection-onnx.md)
