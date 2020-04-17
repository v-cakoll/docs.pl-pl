---
title: 'Samouczek: Wykrywanie obiektów przy użyciu modelu uczenia głębokiego ONNX'
description: W tym samouczku pokazano, jak używać wstępnie przeszkolonego modelu uczenia głębokiego ONNX w ML.NET do wykrywania obiektów na obrazach.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9677c6c9da542123146fc9eef9c311ef30c174e
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608013"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Samouczek: Wykrywanie obiektów przy użyciu ONNX w ML.NET

Dowiedz się, jak używać wstępnie przeszkolonego modelu ONNX w ML.NET do wykrywania obiektów na obrazach.

Szkolenie modelu wykrywania obiektów od podstaw wymaga ustawienia milionów parametrów, dużej ilości oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu). Za pomocą wstępnie przeszkolonego modelu pozwala na skrót procesu szkolenia.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się, czym jest ONNX i jak działa z ML.NET
> - Opis modelu
> - Ponowne wykorzystanie wstępnie przeszkolonego modelu
> - Wykrywanie obiektów za pomocą załadowanego modelu

## <a name="pre-requisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".
- [Microsoft.ML Pakiet NuGet](https://www.nuget.org/packages/Microsoft.ML/)
- [Microsoft.ML.ImageAnalytics Pakiet NuGet](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Pakiet NuGet firmy Microsoft.ML.OnnxTransformer](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Tiny YOLOv2 wstępnie wyszkolony model](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) (opcjonalnie)

## <a name="onnx-object-detection-sample-overview"></a>Omówienie przykładu wykrywania obiektów ONNX

W tym przykładzie tworzy aplikację konsoli .NET, która wykrywa obiekty w obrazie przy użyciu wstępnie przeszkolonego modelu ONNX uczenia głębokiego. Kod dla tego przykładu można znaleźć na [repozytorium dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) w usłudze GitHub.

## <a name="what-is-object-detection"></a>Co to jest wykrywanie obiektów?

Wykrywanie obiektów jest problemem widzenia komputerowego. Podczas gdy ściśle związane z klasyfikacją obrazu, wykrywanie obiektów wykonuje klasyfikację obrazu w skali bardziej szczegółowej. Wykrywanie obiektów lokalizuje _i_ kategoryzuje jednostki w obrazach. Wykrywanie obiektów należy używać, gdy obrazy zawierają wiele obiektów różnych typów.

![Zrzuty ekranu przedstawiające klasyfikację obrazów a klasyfikację obiektów.](./media/object-detection-onnx/img-classification-obj-detection.png)

Niektóre przypadki użycia do wykrywania obiektów obejmują:

- Samochody autonomiczne
- Robotyka
- Wykrywanie twarzy
- Bezpieczeństwo w miejscu pracy
- Zliczanie obiektów
- Rozpoznawanie aktywności

## <a name="select-a-deep-learning-model"></a>Wybieranie modelu uczenia głębokiego

Uczenie głębokie jest podzbiorem uczenia maszynowego. Aby szkolić modele uczenia głębokiego, wymagane są duże ilości danych. Wzorce w danych są reprezentowane przez serię warstw. Relacje w danych są kodowane jako połączenia między warstwami zawierającymi wagi. Im wyższa waga, tym silniejszy związek. Łącznie ta seria warstw i połączeń jest znana jako sztuczne sieci neuronowe. Im więcej warstw w sieci, tym "głębiej" jest, co czyni ją głęboką siecią neuronową.

Istnieją różne typy sieci neuronowych, najczęściej jest wielowarstwowy perceptron (MLP), convolutional neural network (CNN) i nawracające sieci neuronowe (RNN). Najbardziej podstawowy jest MLP, który mapuje zestaw wejść do zestawu wyjść. Ta sieć neuronowa jest dobra, gdy dane nie mają składnika przestrzennego lub czasowego. CNN wykorzystuje splotowe warstwy do przetwarzania informacji przestrzennych zawartych w danych. Dobrym przypadkiem użycia sieci CPN jest przetwarzanie obrazu w celu wykrycia obecności obiektu w regionie obrazu (na przykład, czy w środku obrazu znajduje się nos?). Na koniec RNNs umożliwiają trwałość stanu lub pamięci, które mają być używane jako dane wejściowe. Rnns są używane do analizy szeregów czasowych, gdzie sekwencyjne porządkowanie i kontekst zdarzeń jest ważne.

### <a name="understand-the-model"></a>Opis modelu

Wykrywanie obiektów jest zadaniem przetwarzania obrazu. Dlatego większość modeli uczenia głębokiego przeszkolonych w celu rozwiązania tego problemu to sieci CNN. Model używany w tym poradniku jest model Tiny YOLOv2, bardziej zwarta wersja modelu YOLOv2 opisane w artykule: ["YOLO9000: Lepiej, szybciej, mocniej" przez Redmon i Fadhari](https://arxiv.org/pdf/1612.08242.pdf). Tiny YOLOv2 jest przeszkolony w zestawie danych Pascal VOC i składa się z 15 warstw, które mogą przewidzieć 20 różnych klas obiektów. Ponieważ Tiny YOLOv2 jest skondensowana wersja oryginalnego modelu YOLOv2, kompromis jest między prędkością i dokładnością. Różne warstwy, które tworzą model, można wizualizować za pomocą narzędzi, takich jak Netron. Inspekcja modelu dałoby mapowanie połączeń między wszystkimi warstwami tworzącymi sieć neuronową, gdzie każda warstwa zawierałaby nazwę warstwy wraz z wymiarami odpowiedniego wejścia /wyjścia. Struktury danych używane do opisywania danych wejściowych i wyjściowych modelu są znane jako tensory. Tensory można traktować jako kontenery, które przechowują dane w wymiarach N. W przypadku Tiny YOLOv2, nazwa warstwy `image` wejściowej jest i oczekuje `3 x 416 x 416`tensor wymiarów . Nazwa warstwy wyjściowej `grid` jest i generuje tensor `125 x 13 x 13`wyjściowy wymiarów .

![Warstwa wejściowa jest podzielona na warstwy ukryte, a następnie warstwa wyjściowa](./media/object-detection-onnx/netron-model-map-layers.png)

Model YOLO wykonuje `3(RGB) x 416px x 416px`obraz . Model pobiera te dane wejściowe i przekazuje go przez różne warstwy do uzyskania danych wyjściowych. Dane wyjściowe dzieli obraz `13 x 13` wejściowy do siatki, a `125` każda komórka w siatce składa się z wartości.

### <a name="what-is-an-onnx-model"></a>Co to jest model ONNX?

Open Neural Network Exchange (ONNX) jest formatem open source dla modeli AI. ONNX obsługuje interoperacyjność między strukturami. Oznacza to, że można trenować model w jednym z wielu popularnych platform uczenia maszynowego, takich jak PyTorch, przekonwertować go na format ONNX i korzystać z modelu ONNX w innej ramach, takich jak ML.NET. Aby dowiedzieć się więcej, odwiedź [witrynę ONNX](https://onnx.ai/).

![Diagram używanych formatów obsługiwanych przez ONNX.](./media/object-detection-onnx/onnx-supported-formats.png)

Wstępnie przeszkolony model Tiny YOLOv2 jest przechowywany w formacie ONNX, serializowanej reprezentacji warstw i wyuczonych wzorów tych warstw. W ML.NET współdziałanie z ONNX jest osiągana [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) za pomocą pakietów i NuGet. Pakiet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) zawiera serię przekształceń, które przyjmują obraz i kodują go do wartości liczbowych, które mogą być używane jako dane wejściowe do potoku przewidywania lub szkolenia. Pakiet [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) wykorzystuje środowisko uruchomieniowe ONNX do ładowania modelu ONNX i używa go do tworzenia prognoz na podstawie dostarczonych danych wejściowych.

![Przepływ danych pliku ONNX do środowiska wykonawczego ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>Konfigurowanie projektu .NET Core

Teraz, gdy masz ogólne zrozumienie, czym jest ONNX i jak działa Tiny YOLOv2, nadszedł czas, aby zbudować aplikację.

### <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsoli .NET** Core o nazwie "ObjectDetection".

1. Zainstaluj **pakiet nuget Microsoft.ML:**

    - W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.
    - Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**.
    - Wybierz przycisk **Zainstaluj.**
    - Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.
    - Powtórz te kroki dla **microsoft.ml.ImageAnalytics** i **Microsoft.ML.OnnxTransformer**.

### <a name="prepare-your-data-and-pre-trained-model"></a>Przygotuj swoje dane i wstępnie przeszkolony model

1. Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) i rozpakuj.

1. Skopiuj `assets` katalog do katalogu projektu *ObjectDetection.* Ten katalog i jego podkatalogi zawierają pliki obrazów (z wyjątkiem modelu Tiny YOLOv2, który pobierzesz i dodasz w następnym kroku) potrzebne do tego samouczka.

1. Pobierz [model Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)i rozpakuj.

    Otwórz wiersz polecenia i wprowadź następujące polecenie:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Skopiuj `model.onnx` wyodrębniony plik z katalogu, który został po prostu rozpakowany `TinyYolo2_model.onnx`do katalogu projektu `assets\Model` *ObjectDetection* i zmień jego nazwę na . Ten katalog zawiera model potrzebny do tego samouczka.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu i podkatalogach zasobów, a następnie wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

Otwórz plik *Program.cs* i dodaj następujące `using` dodatkowe instrukcje do górnej części pliku:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Następnie zdefiniuj ścieżki różnych zasobów.

1. Najpierw dodaj `GetAbsolutePath` metodę poniżej `Main` metody `Program` w klasie.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Następnie wewnątrz `Main` metody utwórz pola do przechowywania lokalizacji zasobów.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Dodaj nowy katalog do projektu do przechowywania danych wejściowych i klas przewidywanie.

W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy folder**. Gdy nowy folder pojawi się w Eksploratorze rozwiązań, nazwij go "DataStructures".

Utwórz klasę danych wejściowych w nowo utworzonym katalogu *DataStructures.*

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *Struktura danych,* a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ImageNetData.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *ImageNetData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *ImageNetData.cs:*

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Usuń istniejącą definicję klasy i `ImageNetData` dodaj następujący kod dla klasy do pliku *ImageNetData.cs:*

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:

    - `ImagePath`zawiera ścieżkę, w której obraz jest przechowywany.
    - `Label`zawiera nazwę pliku.

    Ponadto zawiera `ImageNetData` metodę, `ReadFromFile` która ładuje wiele plików `imageFolder` obrazów przechowywanych w określonej ścieżce i zwraca je jako kolekcję `ImageNetData` obiektów.

Utwórz klasę przewidywania w katalogu *DataStructures.*

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *Struktura danych,* a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ImageNetPrediction.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *ImageNetPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *ImageNetPrediction.cs:*

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Usuń istniejącą definicję klasy i `ImageNetPrediction` dodaj następujący kod dla klasy do pliku *ImageNetPrediction.cs:*

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction`jest klasą danych przewidywania `float[]` i ma następujące pole:

    - `PredictedLabel`zawiera wymiary, wynik obiektywizmu i prawdopodobieństwa klasy dla każdego z pól ograniczających wykrytych na obrazie.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w trybie Głównym

Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w entity framework.

Zainicjować `mlContext` zmienną z nowym `MLContext` wystąpieniem, dodając `Main` następujący wiersz do metody `outputFolder` *Program.cs* poniżej pola.

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>Tworzenie analizatora do poprocesowych wyników modelu

Model segmentuje obraz w `13 x 13` siatkę, w `32px x 32px`której znajduje się każda komórka siatki . Każda komórka siatki zawiera 5 pól ograniczających potencjalnych obiektów. Obwiednia ma 25 elementów:

![Próbka siatki po lewej stronie i próbka Obwiednia po prawej stronie](./media/object-detection-onnx/model-output-description.png)

- `x`położenie x środka obwiedni względem komórki siatki, z której jest skojarzona.
- `y`położenie y środka obwiedni względem komórki siatki, z której jest skojarzona.
- `w`szerokości obwiedni.
- `h`wysokości obwiedni.
- `o`wartość zaufania, że obiekt istnieje w obwiedni, znany również jako wynik obiektywizmu.
- `p1-p20`prawdopodobieństwa klasy dla każdej z 20 klas przewidywanych przez model.

W sumie 25 elementów opisujących każde z 5 obwiedni składa się na 125 elementów zawartych w każdej komórce siatki.

Dane wyjściowe generowane przez wstępnie przeszkolony model ONNX `21125`to tablica zmiennoprzecinkowa `125 x 13 x 13`o długości, reprezentująca elementy tensora o wymiarach. Aby przekształcić prognoz generowane przez model w tensor, niektóre prace przetwarzania końcowego jest wymagane. Aby to zrobić, należy utworzyć zestaw klas, aby pomóc przeanalizować dane wyjściowe.

Dodaj nowy katalog do projektu, aby zorganizować zestaw klas analizatora.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy folder**. Gdy nowy folder pojawi się w Eksploratorze rozwiązań, nazwij go "YoloParser".

### <a name="create-bounding-boxes-and-dimensions"></a>Tworzenie obwiedni i wymiarów

Dane wyjściowe przez model zawiera współrzędne i wymiary obwiedni obiektów w obrazie. Utwórz klasę bazową dla wymiarów.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz pozycję **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *DimensionsBase.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *DimensionsBase.cs* zostanie otwarty w edytorze kodu. Usuń `using` wszystkie instrukcje i istniejącą definicję klasy.

    Dodaj następujący kod `DimensionsBase` klasy do pliku *DimensionsBase.cs:*

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase`posiada następujące `float` właściwości:

    - `X`zawiera położenie obiektu wzdłuż osi x.
    - `Y`zawiera położenie obiektu wzdłuż osi y.
    - `Height`zawiera wysokość obiektu.
    - `Width`zawiera szerokość obiektu.

Następnie utwórz klasę dla obwiedni.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz pozycję **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *YoloBoundingBox.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *YoloBoundingBox.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *YoloBoundingBox.cs:*

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Tuż powyżej istniejącej definicji klasy dodaj `BoundingBoxDimensions` nową definicję `DimensionsBase` klasy o nazwie, która dziedziczy z klasy, aby zawierać wymiary odpowiedniego obwiedni.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Usuń istniejącą `YoloBoundingBox` definicję klasy i `YoloBoundingBox` dodaj następujący kod dla klasy do pliku *YoloBoundingBox.cs:*

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox`posiada następujące właściwości:

    - `Dimensions`zawiera wymiary obwiedni.
    - `Label`zawiera klasę obiektu wykrytego w obwiedni.
    - `Confidence`zawiera zaufanie klasy.
    - `Rect`zawiera prostokątne przedstawienie wymiarów obwiedni.
    - `BoxColor`zawiera kolor skojarzony z odpowiednią klasą używaną do rysowania na obrazie.

### <a name="create-the-parser"></a>Tworzenie analizatora

Teraz, gdy klasy dla wymiarów i obwiedni są tworzone, nadszedł czas, aby utworzyć analizatora.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz pozycję **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *YoloOutputParser.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *YoloOutputParser.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *YoloOutputParser.cs:*

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Wewnątrz istniejącej `YoloOutputParser` definicji klasy dodaj klasę zagnieżdżoną zawierającą wymiary każdej z komórek na obrazie. Dodaj następujący kod `CellDimensions` dla klasy, która `DimensionsBase` dziedziczy z `YoloOutputParser` klasy w górnej części definicji klasy.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. Wewnątrz `YoloOutputParser` definicji klasy dodaj następujące stałe i pola.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT`to liczba wierszy w siatce, na które obraz jest podzielony.
    - `COL_COUNT`to liczba kolumn w siatce, na które obraz jest podzielony.
    - `CHANNEL_COUNT`to całkowita liczba wartości zawartych w jednej komórce siatki.
    - `BOXES_PER_CELL`to liczba obwiedni w komórce,
    - `BOX_INFO_FEATURE_COUNT`to liczba operacji zawartych w polu (x,y,height,width,confidence).
    - `CLASS_COUNT`jest liczbą prognoz klasy zawartych w każdej obwiedni.
    - `CELL_WIDTH`to szerokość jednej komórki w siatce obrazu.
    - `CELL_HEIGHT`to wysokość jednej komórki w siatce obrazu.
    - `channelStride`jest pozycją początkową bieżącej komórki w siatce.

    Gdy model tworzy prognozy, znany również jako `416px x 416px` punktacji, dzieli obraz wejściowy `13 x 13`do siatki komórek wielkości . Każda komórka `32px x 32px`zawiera jest . W każdej komórce znajduje się 5 obwiedni zawierających 5 obiektów (x, y, szerokość, wysokość, pewność). Ponadto każde obwiednia zawiera prawdopodobieństwo każdej z klas, która w tym przypadku wynosi 20. W związku z tym każda komórka zawiera 125 sztuk informacji (5 funkcji + prawdopodobieństwa klasy 20).

Utwórz listę zakotwiczeń poniżej `channelStride` dla wszystkich 5 obwiedni:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Kotwy są wstępnie zdefiniowane proporcje wysokości i szerokości obwiedni. Większość obiektów lub klas wykrytych przez model mają podobne proporcje. Jest to cenne, jeśli chodzi o tworzenie obwiedni. Zamiast przewidywać obwiednie, przesunięcie od wstępnie zdefiniowanych wymiarów jest obliczane, zmniejszając w związku z tym zmniejszenie obliczeń wymaganych do przewidzenia obwiedni. Zazwyczaj te współczynniki zakotwiczenia są obliczane na podstawie używanego zestawu danych. W takim przypadku, ponieważ zestaw danych jest znany, a wartości zostały wstępnie obliczone, kotwice mogą być zakodowane na komputerze.

Następnie zdefiniuj etykiety lub klasy, które model będzie przewidzieć. Ten model przewiduje 20 klas, co jest podzbiorem całkowitej liczby klas przewidywanych przez oryginalny model YOLOv2.

Dodaj listę etykiet poniżej . `anchors`

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Istnieją kolory skojarzone z każdą z klas. Przypisz kolory klasy `labels`poniżej:

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Tworzenie funkcji pomocnika

Istnieje szereg kroków związanych z fazą przetwarzania końcowego. Aby pomóc w tym, można zastosować kilka metod pomocniczych.

Metody pomocnicze używane przez analizatora są:

- `Sigmoid`stosuje funkcję esicy, która wyprowadza liczbę z 0 do 1.
- `Softmax`normalizuje wektor wejściowy do rozkładu prawdopodobieństwa.
- `GetOffset`mapuje elementy w jednowymiarowym wyjściu modelu `125 x 13 x 13` do odpowiedniej pozycji w tensorze.
- `ExtractBoundingBoxes`wyodrębnia wymiary obwiedni `GetOffset` przy użyciu metody z danych wyjściowych modelu.
- `GetConfidence`wyodrębnia wartość zaufania, która określa, jak pewny jest model, że `Sigmoid` wykrył obiekt i używa funkcji, aby przekształcić go w procent.
- `MapBoundingBoxToCell`używa wymiarów obwiedni i mapuje je na odpowiednią komórkę w obrazie.
- `ExtractClasses`wyodrębnia prognoz klasy dla obwiedni z danych `GetOffset` wyjściowych modelu przy użyciu metody `Softmax` i zamienia je w rozkład prawdopodobieństwa przy użyciu metody.
- `GetTopResult`wybiera klasę z listy przewidywanych klas z najwyższym prawdopodobieństwem.
- `IntersectionOverUnion`filtruje nakładające się obwiedni o niższym prawdopodobieństwie.

Dodaj kod dla wszystkich metod pomocnika poniżej listy `classColors`.

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Po zdefiniowaniu wszystkich metod pomocnika, nadszedł czas, aby użyć ich do przetwarzania danych wyjściowych modelu.

Poniżej `IntersectionOverUnion` metody należy `ParseOutputs` utworzyć metodę przetwarzania danych wyjściowych generowanych przez model.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Utwórz listę do przechowywania obwiedni i `ParseOutputs` definiowania zmiennych wewnątrz metody.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Każdy obraz jest podzielony na `13 x 13` siatkę komórek. Każda komórka zawiera pięć obwiedni. Poniżej `boxes` zmiennej dodaj kod, aby przetworzyć wszystkie pola w każdej z komórek.

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

Wewnątrz pętli wewnętrznej obliczyć położenie początkowe bieżącego pola w jednowymiarowym wyjściu modelu.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Bezpośrednio poniżej tej `ExtractBoundingBoxDimensions` metody, aby uzyskać wymiary bieżącego obwiedni.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Następnie użyj `GetConfidence` metody, aby uzyskać zaufanie dla bieżącego obwiedni.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Następnie użyj `MapBoundingBoxToCell` metody, aby zamapować bieżące obwiednie na bieżącą przetwarzającą komórkę.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Przed wykonaniem dalszego przetwarzania sprawdź, czy wartość zaufania jest większa niż podany próg. Jeśli nie, przetwórz następne obwiednie.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

W przeciwnym razie kontynuuj przetwarzanie danych wyjściowych. Następnym krokiem jest uzyskanie rozkładu prawdopodobieństwa przewidywanych klas dla bieżącego obwiedni przy użyciu `ExtractClasses` metody.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Następnie należy `GetTopResult` użyć metody, aby uzyskać wartość i indeks klasy z najwyższym prawdopodobieństwem dla bieżącego pola i obliczyć jego wynik.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

Użyj, `topScore` aby ponownie zachować tylko te granice, które są powyżej określonego progu.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Na koniec, jeśli bieżące pole ograniczające przekracza `BoundingBox` próg, utwórz `boxes` nowy obiekt i dodaj go do listy.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Po przetworzeniu wszystkich komórek obrazu zwróć `boxes` listę. Dodaj następującą instrukcję return poniżej zewnętrznej `ParseOutputs` większości for-pętli w metodzie.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Filtruj nakładające się pola

Teraz, gdy wszystkie bardzo pewne granice zostały wyodrębnione z danych wyjściowych modelu, należy wykonać dodatkowe filtrowanie w celu usunięcia nakładających się obrazów. Dodaj metodę `FilterBoundingBoxes` o `ParseOutputs` nazwie poniżej metody:

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

Wewnątrz `FilterBoundingBoxes` metody zacznij od utworzenia tablicy równej rozmiarowi wykrytych pól i oznaczenia wszystkich gniazd jako aktywnych lub gotowych do przetworzenia.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Następnie posortuj listę zawierającą obwiednie w porządku malejącym na podstawie zaufania.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Następnie utwórz listę, aby pomieścić filtrowane wyniki.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Rozpocznij przetwarzanie każdego obwiedni przez iterację nad każdym z obwiedni.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Wewnątrz tej pętli sprawdź, czy można przetworzyć bieżące obwiednię.

```csharp
if (isActiveBoxes[i])
{

}
```

Jeśli tak, dodaj obwiednię do listy wyników. Jeśli wyniki przekroczą określony limit pól do wyodrębnienia, wyłam się z pętli. Dodaj następujący kod wewnątrz if-instrukcji.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

W przeciwnym razie spójrz na sąsiednie obwiednie. Dodaj poniższy kod poniżej pola wyboru limitu.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

Podobnie jak w pierwszym polu, jeśli sąsiednie pole jest aktywne `IntersectionOverUnion` lub gotowe do przetworzenia, użyj metody, aby sprawdzić, czy pierwsze i drugie pole przekracza określony próg. Dodaj następujący kod do najbardziej wewnętrznej pętli dla.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Poza wewnętrznej większości for-pętli, która sprawdza sąsiednich pól ograniczających, zobacz, czy istnieją wszystkie pozostałe pola ograniczające do przetworzenia. Jeśli nie, wyrwaj się z zewnętrznej pętli.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Na koniec, poza początkową pętlą `FilterBoundingBoxes` dla metody, zwracaj wyniki:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Wspaniale! Teraz nadszedł czas, aby użyć tego kodu wraz z modelu do oceniania.

## <a name="use-the-model-for-scoring"></a>Użyj modelu do oceniania

Podobnie jak w przetwarzaniu pocztowym, istnieje kilka kroków w krokach oceniania. Aby pomóc w tym, należy dodać klasę, która będzie zawierać logiki oceniania do projektu.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *OnnxModelScorer.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *OnnxModelScorer.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *OnnxModelScorer.cs:*

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    Wewnątrz `OnnxModelScorer` definicji klasy dodaj następujące zmienne.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Bezpośrednio poniżej tego, utworzyć konstruktor dla `OnnxModelScorer` klasy, która rozpocznie wcześniej zdefiniowane zmienne.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Po utworzeniu konstruktora zdefiniuj kilka struktur, które zawierają zmienne związane z ustawieniami obrazu i modelu. Utwórz strukturę `ImageNetSettings` wywoływaną, aby zawierała oczekiwaną wysokość i szerokość jako dane wejściowe dla modelu.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Następnie należy utworzyć inną `TinyYoloModelSettings` strukturę o nazwie, która zawiera nazwy warstw wejściowych i wyjściowych modelu. Aby wizualizować nazwę warstw wejściowych i wyjściowych modelu, można użyć narzędzia, takiego jak [Netron](https://github.com/lutzroeder/netron).

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Następnie utwórz pierwszy zestaw metod używanych do oceniania. Utwórz `LoadModel` metodę wewnątrz `OnnxModelScorer` klasy.

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Wewnątrz `LoadModel` metody dodaj następujący kod do rejestrowania.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    ML.NET potoki muszą znać schemat danych do pracy, [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) gdy metoda jest wywoływana. W takim przypadku zostanie użyty proces podobny do szkolenia. Jednak, ponieważ nie rzeczywiste szkolenia dzieje, jest [`IDataView`](xref:Microsoft.ML.IDataView)dopuszczalne, aby użyć pustego . Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) nowy dla potoku z pustej listy.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Poniżej zdefiniuj potok. Rurociąg będzie składał się z czterech przekształceń.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)ładuje obraz jako bitmapę.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)przeskaluje obraz do określonego rozmiaru (w tym przypadku `416 x 416`).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)zmienia reprezentację obrazu w pikselach z mapy bitowej na wektor numeryczny.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ładuje model ONNX i używa go do punktacji na dostarczonych danych.

    Zdefiniuj `LoadModel` potok `data` w metodzie poniżej zmiennej.

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Teraz nadszedł czas, aby utworzyć wystąpienie modelu do oceniania. Wywołanie [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metody w potoku i zwrócić ją do dalszego przetwarzania.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Po załadowaniu modelu, może następnie służyć do prognozowania. Aby ułatwić ten proces, `PredictDataUsingModel` należy `LoadModel` utworzyć metodę o nazwie poniżej metody.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

Wewnątrz `PredictDataUsingModel`, dodaj następujący kod do rejestrowania.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody, aby uzyskać dane.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Wyodrębnij przewidywane prawdopodobieństwa i zwróć je do dodatkowego przetwarzania.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Teraz, gdy oba kroki są skonfigurowane, połącz je w jedną metodę. Poniżej `PredictDataUsingModel` metody dodaj nową `Score`metodę o nazwie .

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Prawie tam! Teraz nadszedł czas, aby umieścić to wszystko w użyciu.

## <a name="detect-objects"></a>Wykrywanie obiektów

Teraz, gdy cała konfiguracja została ukończona, nadszedł czas, aby wykryć niektóre obiekty. Zacznij od dodania odniesień do strzelca i analizatora w *klasie Program.cs.*

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Wyniki i analizowanie wyników modelu

Wewnątrz `Main` metody *Program.cs* klasy dodaj instrukcję try-catch.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

Wewnątrz `try` bloku rozpocznij implementowanie logiki wykrywania obiektów. Najpierw załaduj [`IDataView`](xref:Microsoft.ML.IDataView)dane do pliku .

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Następnie utwórz wystąpienie `OnnxModelScorer` i użyj go do oceny załadowanych danych.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Teraz nadszedł czas na etap przetwarzania końcowego. Utwórz wystąpienie `YoloOutputParser` i użyj go do przetworzenia danych wyjściowych modelu.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Po przetworzeniu danych wyjściowych modelu nadszedł czas, aby narysować obwiednie na obrazach.

### <a name="visualize-predictions"></a>Wizualizuj prognozy

Po modelu zdobył obrazy i dane wyjściowe zostały przetworzone, granice muszą być rysowane na obrazie. Aby to zrobić, należy `DrawBoundingBox` dodać `GetAbsolutePath` metodę o nazwie poniżej metody wewnątrz *Program.cs*.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

Najpierw załaduj obraz i uzyskaj `DrawBoundingBox` wymiary wysokości i szerokości w metodzie.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Następnie należy utworzyć for-each pętli do iteracji nad każdym z obwiedni wykrytych przez model.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

Wewnątrz pętli dla każdej, uzyskać wymiary obwiedni.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Ponieważ wymiary obwiedni odpowiadają wejściu `416 x 416`modelu , skaluj wymiary obwiedni, aby dopasować rzeczywisty rozmiar obrazu.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Następnie zdefiniuj szablon dla tekstu, który pojawi się nad każdym obwiednią. Tekst będzie zawierał klasę obiektu wewnątrz odpowiedniego obwiedni, a także pewność.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Aby narysować na obrazie, przekonwertuj go na [`Graphics`](xref:System.Drawing.Graphics) obiekt.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

Wewnątrz `using` bloku kodu dostroić [`Graphics`](xref:System.Drawing.Graphics) ustawienia obiektu grafiki.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Poniżej ustaw czcionkę i opcje kolorów tekstu i obwiedni.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Utwórz i wypełnij prostokąt nad obwiednią, [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) aby zawierał tekst przy użyciu metody. Pomoże to kontrast tekstu i poprawić czytelność.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Następnie narysuj tekst i obwiednię na obrazie za pomocą [`DrawString`](xref:System.Drawing.Graphics.DrawString*) metod i. [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*)

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

Poza pętlą dla każdego dodaj kod, aby `outputDirectory`zapisać obrazy w pliku .

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Aby uzyskać dodatkowe informacje zwrotne, że aplikacja robi prognoz `LogDetectedObjects` zgodnie `DrawBoundingBox` z oczekiwaniami w czasie wykonywania, dodaj metodę o nazwie poniżej metody w pliku *Program.cs* do wyprowadzania wykrytych obiektów do konsoli.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Teraz, gdy masz metody pomocnicze do tworzenia wizualnych informacji zwrotnych z prognoz, dodaj for-loop do iteracji nad każdym z obrazów zdobył.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

Wewnątrz for-loop, uzyskać nazwę pliku obrazu i granice skojarzone z nim.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Poniżej użyj `DrawBoundingBox` metody, aby narysować obwiednie na obrazie.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Wreszcie należy `LogDetectedObjects` użyć metody do wyprowadzania prognoz do konsoli.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Po instrukcji try-catch dodaj dodatkową logikę, aby wskazać, że proces jest wykonywany.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

Gotowe.

## <a name="results"></a>Wyniki

Po wykonać poprzednie kroki uruchom aplikację konsoli (Ctrl + F5). Wyniki powinny być podobne do następujących danych wyjściowych. Możesz zobaczyć ostrzeżenia lub przetwarzania wiadomości, ale te komunikaty zostały usunięte z następujących wyników dla jasności.

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

Aby wyświetlić obrazy z obwiedniami, przejdź do `assets/images/output/` katalogu. Poniżej znajduje się przykład z jednego z przetworzonych obrazów.

![Przykładowy przetworzony obraz jadalni](./media/object-detection-onnx/dinning-room-table-chairs.png)

Gratulacje! Pomyślnie zbudowano model uczenia maszynowego do wykrywania obiektów, ponownie `ONNX` korzystając z wstępnie przeszkolonego modelu w ML.NET.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się, czym jest ONNX i jak działa z ML.NET
> - Opis modelu
> - Ponowne wykorzystanie wstępnie przeszkolonego modelu
> - Wykrywanie obiektów za pomocą załadowanego modelu

Zapoznaj się z przykładami uczenia maszynowego Repozytorium GitHub, aby eksplorować przykładowy wykrywania obiektów rozszerzonych.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples Repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
