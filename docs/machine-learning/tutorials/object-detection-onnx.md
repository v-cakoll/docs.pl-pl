---
title: 'Samouczek: wykrywanie obiektów przy użyciu modelu uczenia głębokiego ONNX'
description: W tym samouczku przedstawiono sposób użycia wstępnie przeszkolonego modelu uczenia głębokiego ONNX w ML.NET do wykrywania obiektów w obrazach.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b4f6457c4fab8549b3efec2e25f7c23213698414
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767783"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Samouczek: wykrywanie obiektów przy użyciu ONNX w ML.NET

Dowiedz się, jak używać wstępnie przeszkolonego modelu ONNX w programie ML.NET do wykrywania obiektów w obrazach.

Uczenie modelu wykrywania obiektów od podstaw wymaga ustawienia milionów parametrów, dużej ilości danych szkoleniowych i szerokiej ilości zasobów obliczeniowych (setki godzin procesora GPU). Korzystanie z wstępnie nauczonego modelu umożliwia podwyższenie poziomu procesu szkolenia.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się, co ONNX i jak działa z ML.NET
> - Zrozumienie modelu
> - Ponownie Użyj wstępnie nauczonego modelu
> - Wykrywanie obiektów z załadowanym modelem

## <a name="pre-requisites"></a>Wymagania wstępne

- [Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.
- [Pakiet NuGet Microsoft.ML](https://www.nuget.org/packages/Microsoft.ML/)
- [Pakiet NuGet Microsoft. ML. ImageAnalytics](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Pakiet NuGet Microsoft. ML. OnnxTransformer](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Mały model wstępnie przeszkolony YOLOv2](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny-yolov2)
- [Netron](https://github.com/lutzroeder/netron) (opcjonalnie)

## <a name="onnx-object-detection-sample-overview"></a>Przykład wykrywania obiektów ONNX

Ten przykład służy do tworzenia aplikacji konsolowej .NET Core, która wykrywa obiekty w obrazie przy użyciu wstępnie nauczonego modelu ONNX uczenia głębokiego. Kod dla tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) w witrynie GitHub.

## <a name="what-is-object-detection"></a>Co to jest wykrywanie obiektów?

Wykrywanie obiektów to problem z obsługą komputera. Chociaż ściśle powiązane z klasyfikacją obrazów, wykrywanie obiektów wykonuje klasyfikację obrazów na bardziej szczegółowym poziomie. Wykrywanie obiektów zarówno lokalizuje _, jak i_ klasyfikuje jednostki w obrazach. Użyj wykrywania obiektów, gdy obrazy zawierają wiele obiektów różnych typów.

![Zrzuty ekranu przedstawiające klasyfikację obrazu w porównaniu z klasyfikacją obiektów.](./media/object-detection-onnx/img-classification-obj-detection.png)

Niektóre przypadki użycia dotyczące wykrywania obiektów obejmują:

- Samochody samoobsługowe
- Atrybut
- Wykrywanie twarzy
- Bezpieczeństwo w miejscu pracy
- Zliczanie obiektów
- Rozpoznawanie działań

## <a name="select-a-deep-learning-model"></a>Wybierz model uczenia głębokiego

Uczenie głębokie to podzestaw uczenia maszynowego. Aby szkolić modele uczenia głębokiego, wymagane są duże ilości danych. Wzorce w danych są reprezentowane przez serię warstw. Relacje w danych są kodowane jako połączenia między warstwami zawierającymi wagi. Im wyższa waga, tym silniejszy jest związek. Zbiorczo te serie warstw i połączeń są nazywane sztucznymi sieciami neuronowych. Im więcej warstw w sieci, tym "głębiej" jest to, że jest to sieć głębokiej neuronowych.

Istnieją różne typy sieci neuronowych, najczęściej występujące wielowarstwowe Perceptron (MLP), Splotowych neuronowych Network (CNN) i Recurrent neuronowych Network (RNN). Najbardziej podstawowa jest MLP, która mapuje zestaw danych wejściowych na zestaw wyników. Ta sieć neuronowych jest dobra, gdy dane nie zawierają składnika przestrzennego ani czasu. CNN wykorzystuje warstwy splotowych do przetwarzania informacji przestrzennych zawartych w danych. Dobrym przypadkiem użycia dla CNNs jest przetwarzanie obrazu w celu wykrycia obecności funkcji w regionie obrazu (na przykład jest to nos na środku obrazu?). Na koniec RNN zezwolić na trwałość stanu lub pamięci jako dane wejściowe. RNN są używane do analizy szeregów czasowych, gdzie ważne jest porządkowanie sekwencyjne i kontekst zdarzeń.

### <a name="understand-the-model"></a>Zrozumienie modelu

Wykrywanie obiektów to zadanie przetwarzania obrazów. W związku z tym większość modeli uczenia głębokiego przeszkolonych w celu rozwiązania tego problemu jest CNNs. Model używany w tym samouczku to mały model YOLOv2, bardziej zwarta wersja modelu YOLOv2 opisana w dokumencie: ["YOLO9000: lepszy, szybszy, silniejszy" przez RedMon i Farhadi](https://arxiv.org/pdf/1612.08242.pdf). Niewielka YOLOv2 jest przeszkolony na zestawie danych LZO w języku Pascal i składa się z 15 warstw, które mogą przewidzieć 20 różnych klas obiektów. Ponieważ mała YOLOv2 to skrócona wersja oryginalnego modelu YOLOv2, kompromis między szybkością i dokładnością jest zwiększany. Różne warstwy, które tworzą model, można wizualizować przy użyciu narzędzi, takich jak Netron. Sprawdzenie modelu spowoduje odwzorowanie połączeń między wszystkimi warstwami tworzącymi sieć neuronowych, gdzie każda warstwa będzie zawierać nazwę warstwy wraz z wymiarami odpowiednich operacji wejścia/wyjścia. Struktury danych używane do opisywania wejścia i wyjścia modelu są znane jako dwuczęściowe. Mogą być uważane za kontenery, które przechowują dane w N-wymiarach. W przypadku bardzo niewielkich YOLOv2 Nazwa warstwy wejściowej jest `image` i oczekuje dwuwymiarowego wymiaru `3 x 416 x 416` . Nazwa warstwy wyjściowej jest `grid` generowana w postaci dwuwymiarowego natężenia wymiarów `125 x 13 x 13` .

![Warstwa wejściowa jest podzielona na warstwy ukryte, a następnie warstwa wyjściowa](./media/object-detection-onnx/netron-model-map-layers.png)

Model YOLO pobiera obraz `3(RGB) x 416px x 416px` . Model przyjmuje dane wejściowe i przekazuje je za pomocą różnych warstw, aby utworzyć dane wyjściowe. Dane wyjściowe dzielą obraz wejściowy na `13 x 13` siatkę, z każdą komórką w siatce składającą się z `125` wartości.

### <a name="what-is-an-onnx-model"></a>Co to jest model ONNX?

Open neuronowych Network Exchange (ONNX) to format Open Source dla modeli AI. ONNX obsługuje współdziałanie między strukturami. Oznacza to, że możesz przeszkolić model w jednym z wielu popularnych platform uczenia maszynowego, takich jak PyTorch, przekonwertować go do formatu ONNX i korzystać z modelu ONNX w różnych strukturach, takich jak ML.NET. Aby dowiedzieć się więcej, odwiedź witrynę [sieci Web ONNX](https://onnx.ai/).

![Diagram ONNX obsługiwanych formatów.](./media/object-detection-onnx/onnx-supported-formats.png)

Wstępnie szkolony model YOLOv2 jest przechowywany w formacie ONNX, szeregowaną reprezentacją warstw i wyznanie wzorców tych warstw. W programie ML.NET współdziałanie z usługą ONNX jest realizowane przy użyciu [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) pakietów NuGet i. [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image)Pakiet zawiera serię przekształceń, która pobiera obraz i koduje go na wartości liczbowe, które mogą być używane jako dane wejściowe w potoku predykcyjnym lub szkoleniowym. [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer)Pakiet wykorzystuje środowisko uruchomieniowe ONNX w celu załadowania modelu ONNX i używania go do prognozowania na podstawie dostarczonego danych wejściowych.

![Przepływ danych pliku ONNX do środowiska uruchomieniowego ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>Konfigurowanie projektu .NET Core

Teraz, gdy masz ogólne informacje o tym, co ONNX się i jak mała YOLOv2 działa, to czas na skompilowanie aplikacji.

### <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsolową .NET Core** o nazwie "ObjectDetection".

1. Zainstaluj **pakiet NuGet Microsoft.ml**:

    - W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.
    - Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**.
    - Wybierz przycisk **Instaluj** .
    - Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.
    - Powtórz te kroki dla **Microsoft. ml. ImageAnalytics**, **Microsoft. ml. OnnxTransformer** i **Microsoft. ml. OnnxRuntime**.

### <a name="prepare-your-data-and-pre-trained-model"></a>Przygotowywanie danych i wstępnie szkolony model

1. Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) i rozpakuj.

1. Skopiuj `assets` katalog do katalogu projektu *ObjectDetection* . Ten katalog i jego podkatalogi zawierają pliki obrazów (z wyjątkiem niewielkiego modelu YOLOv2, który zostanie pobrany i dodany w następnym kroku), co jest potrzebne w tym samouczku.

1. Pobierz [mały model YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [modelu ONNX zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny-yolov2)i rozpakuj.

    Otwórz wiersz polecenia i wprowadź następujące polecenie:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Skopiuj wyodrębniony `model.onnx` plik z katalogu do katalogu projektu *ObjectDetection* `assets\Model` , a następnie zmień jego nazwę na `TinyYolo2_model.onnx` . Ten katalog zawiera model wymagany dla tego samouczka.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu zasobów i podkatalogach i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i Definiowanie ścieżek

Otwórz plik *program.cs* i Dodaj następujące dodatkowe `using` instrukcje na początku pliku:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Następnie zdefiniuj ścieżki różnych zasobów.

1. Najpierw Dodaj `GetAbsolutePath` metodę poniżej `Main` metody w `Program` klasie.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Następnie wewnątrz `Main` metody Utwórz pola do przechowywania lokalizacji zasobów.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Dodaj nowy katalog do projektu w celu przechowywania danych wejściowych i klas przewidywania.

W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **Nowy folder**. Gdy nowy folder pojawi się w Eksplorator rozwiązań, nadaj mu nazwę "struktury datastructures".

Utwórz klasę danych wejściowych w nowo utworzonym katalogu *struktury* danych.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *struktury datastructures* , a następnie wybierz pozycję **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageNetData.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *ImageNetData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *ImageNetData.cs*:

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageNetData` klasy do pliku *ImageNetData.cs* :

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:

    - `ImagePath`zawiera ścieżkę, w której jest przechowywany obraz.
    - `Label`zawiera nazwę pliku.

    Ponadto program `ImageNetData` zawiera metodę `ReadFromFile` , która ładuje wiele plików obrazu przechowywanych w `imageFolder` określonej ścieżce i zwraca je jako kolekcję `ImageNetData` obiektów.

Utwórz klasę predykcyjną w katalogu *struktury* danych.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *struktury datastructures* , a następnie wybierz pozycję **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageNetPrediction.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *ImageNetPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *ImageNetPrediction.cs*:

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageNetPrediction` klasy do pliku *ImageNetPrediction.cs* :

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction`jest klasą przewidywania i ma następujące `float[]` pole:

    - `PredictedLabel`zawiera wymiary, wynik obiektu i prawdopodobieństwa klasy dla każdego z pól, które zostały wykryte w obrazie.

### <a name="initialize-variables-in-main"></a>Inicjuj zmienne w głównym

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo do `DBContext` w Entity Framework.

Zainicjuj `mlContext` zmienną z nowym wystąpieniem programu `MLContext` , dodając następujący wiersz do `Main` metody *program.cs* poniżej `outputFolder` pola.

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>Tworzenie analizatora danych wyjściowych modelu po procesie

Model segmentuje obraz w `13 x 13` siatce, gdzie każda komórka siatki ma wartość `32px x 32px` . Każda komórka siatki zawiera 5 potencjalnych pól związanych z obiektem. Pole ograniczenia ma 25 elementów:

![Przykład siatki po lewej stronie i pole ograniczenia ramki po prawej stronie](./media/object-detection-onnx/model-output-description.png)

- `x`Pozycja x środka pola ograniczenia względem komórki siatki, z którą jest skojarzona.
- `y`Pozycja y środka pola ograniczenia względem komórki siatki, z którą jest skojarzona.
- `w`Szerokość pola ograniczenia.
- `h`Wysokość pola ograniczenia.
- `o`wartość pewności, którą obiekt istnieje w polu ograniczenia, znanego również jako wynik obiektu.
- `p1-p20`prawdopodobieństwa klasy dla każdej z 20 klas przewidywanych przez model.

Łącznie 25 elementów opisujących każde z 5 pól ograniczenia tworzą elementy 125 zawarte w każdej komórce siatki.

Dane wyjściowe generowane przez wstępnie szkolony model ONNX są tablicą zmiennoprzecinkową o długości `21125` reprezentującą elementy Dwupunktowe z wymiarami `125 x 13 x 13` . Aby przekształcić przewidywania wygenerowane przez model na dwuczęściowy, wymagana jest część pracy wykonywanej po przetworzeniu. W tym celu należy utworzyć zestaw klas, aby ułatwić analizowanie danych wyjściowych.

Dodaj nowy katalog do projektu, aby zorganizować zestaw klas parsera.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **Nowy folder**. Gdy nowy folder pojawi się w Eksplorator rozwiązań, nadaj mu nazwę "YoloParser".

### <a name="create-bounding-boxes-and-dimensions"></a>Tworzenie pól ograniczenia i wymiarów

Dane wyjściowe przez model zawierają współrzędne i wymiary pól ograniczenia obiektów w obrazie. Utwórz klasę bazową dla wymiarów.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *DimensionsBase.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *DimensionsBase.cs* zostanie otwarty w edytorze kodu. Usuń wszystkie `using` instrukcje i istniejącą definicję klasy.

    Dodaj następujący kod dla `DimensionsBase` klasy do pliku *DimensionsBase.cs* :

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase`ma następujące `float` Właściwości:

    - `X`zawiera położenie obiektu wzdłuż osi x.
    - `Y`zawiera położenie obiektu wzdłuż osi y.
    - `Height`zawiera wysokość obiektu.
    - `Width`zawiera szerokość obiektu.

Następnie Utwórz klasę dla pól ograniczenia.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *YoloBoundingBox.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *YoloBoundingBox.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *YoloBoundingBox.cs*:

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Tuż powyżej istniejącej definicji klasy Dodaj nową definicję klasy o nazwie `BoundingBoxDimensions` , która dziedziczy z klasy, `DimensionsBase` aby zawierała wymiary odpowiedniego pola ograniczenia.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Usuń istniejącą `YoloBoundingBox` definicję klasy i Dodaj następujący kod dla `YoloBoundingBox` klasy do pliku *YoloBoundingBox.cs* :

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox`ma następujące właściwości:

    - `Dimensions`zawiera wymiary powiązanego pola.
    - `Label`zawiera klasę obiektu wykryty w polu ograniczenia.
    - `Confidence`zawiera zaufanie do klasy.
    - `Rect`zawiera reprezentację prostokąta wymiarów powiązanego pola.
    - `BoxColor`zawiera kolor skojarzony z odpowiednią klasą używaną do rysowania na obrazie.

### <a name="create-the-parser"></a>Tworzenie analizatora

Teraz, gdy tworzone są klasy wymiarów i pól powiązanych, czas na utworzenie analizatora.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *YoloOutputParser.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *YoloOutputParser.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *YoloOutputParser.cs*:

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Wewnątrz istniejącej `YoloOutputParser` definicji klasy Dodaj zagnieżdżoną klasę, która zawiera wymiary każdej komórki w obrazie. Dodaj następujący kod dla `CellDimensions` klasy, która dziedziczy z `DimensionsBase` klasy w górnej części `YoloOutputParser` definicji klasy.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. Wewnątrz `YoloOutputParser` definicji klasy Dodaj następujące stałe i pola.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT`to liczba wierszy w siatce, do których jest podzielona ilustracja.
    - `COL_COUNT`jest liczbą kolumn w siatce, w której jest podzielony obraz.
    - `CHANNEL_COUNT`to całkowita liczba wartości zawartych w jednej komórce siatki.
    - `BOXES_PER_CELL`jest liczbą pól ograniczenia w komórce,
    - `BOX_INFO_FEATURE_COUNT`to liczba funkcji zawartych w polu (x, y, wysokość, Szerokość, pewność).
    - `CLASS_COUNT`to liczba prognoz klas zawartych w każdym polu ograniczenia.
    - `CELL_WIDTH`jest szerokością jednej komórki w siatce obrazu.
    - `CELL_HEIGHT`to wysokość jednej komórki w siatce obrazu.
    - `channelStride`jest pozycją początkową bieżącej komórki siatki.

    Gdy model wykonuje prognozę, znaną również jako ocenianie, dzieli `416px x 416px` obraz wejściowy na siatkę komórek o rozmiarze `13 x 13` . Każda komórka zawiera `32px x 32px` . W każdej komórce istnieją 5 pól, które zawierają 5 funkcji (x, y, Szerokość, wysokość, pewność). Ponadto każde pole ograniczenia zawiera prawdopodobieństwo dla każdej z klas, co w tym przypadku wynosi 20. W związku z tym każda komórka zawiera 125 fragmenty informacji (5 funkcji + 20 prawdopodobieństwa dotyczącej klasy).

Utwórz listę kotwic poniżej `channelStride` dla wszystkich 5 pól ograniczenia:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Kotwice to wstępnie zdefiniowany stosunek wysokości i szerokości pól ograniczenia. Większość obiektów lub klas wykrywanych przez model ma podobne wskaźniki. Jest to przydatne, gdy chodzi o tworzenie pól ograniczenia. Zamiast przewidywania pól powiązanych, obliczane są przesunięcie ze wstępnie zdefiniowanych wymiarów w związku z tym redukcja obliczeń wymaganych do przewidywania pola ograniczenia. Zazwyczaj te współczynniki zakotwiczenia są obliczane na podstawie używanego zestawu danych. W tym przypadku, ponieważ zestaw danych jest znany i wartości zostały wstępnie obliczone, kotwice mogą być zakodowane na stałe.

Następnie zdefiniuj etykiety lub klasy, które będą przewidywalne przez model. Ten model przewiduje 20 klas, który jest podzbiorem całkowitej liczby klas przewidywanych przez oryginalny model YOLOv2.

Dodaj listę etykiet poniżej `anchors` .

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Istnieją kolory skojarzone z każdą z klas. Przypisz kolory klasy poniżej `labels` :

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Tworzenie funkcji pomocnika

Etap przetwarzania końcowego obejmuje szereg kroków. Aby pomóc w tym, można zastosować kilka metod pomocnika.

Metody pomocnika używane przez parser są następujące:

- `Sigmoid`stosuje funkcję sigmoid, która wyprowadza liczbę z zakresu od 0 do 1.
- `Softmax`normalizuje wektor wejściowy do rozkładu prawdopodobieństwa.
- `GetOffset`mapuje elementy w danych wyjściowych modelu jednowymiarowego do odpowiedniej pozycji w dwukierunkowym `125 x 13 x 13` .
- `ExtractBoundingBoxes`wyodrębnia Wymiary pola ograniczenia przy użyciu `GetOffset` metody z danych wyjściowych modelu.
- `GetConfidence`Wyodrębnia wartość pewności, która określa, jak upewnić się, że model wykrył obiekt i używa funkcji, `Sigmoid` Aby przekształcić ją w wartość procentową.
- `MapBoundingBoxToCell`używa wymiarów pola ograniczenia i mapuje je na odpowiednią komórkę w obrazie.
- `ExtractClasses`wyodrębnia przewidywania klas dla pola ograniczenia z danych wyjściowych modelu przy użyciu `GetOffset` metody i włącza je do dystrybucji prawdopodobieństwa przy użyciu `Softmax` metody.
- `GetTopResult`wybiera klasę z listy przewidywanych klas o największym prawdopodobieństwie.
- `IntersectionOverUnion`filtruje nakładające się pola ograniczające o mniejsze prawdopodobieństwa.

Dodaj kod dla wszystkich metod pomocników znajdujących się poniżej listy `classColors` .

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Po zdefiniowaniu wszystkich metod pomocnika czas na jego użycie będzie przetwarzać dane wyjściowe modelu.

Poniżej `IntersectionOverUnion` metody Utwórz `ParseOutputs` metodę, aby przetworzyć dane wyjściowe generowane przez model.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Utwórz listę do przechowywania pól ograniczenia i zdefiniuj zmienne wewnątrz `ParseOutputs` metody.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Każdy obraz jest podzielony na siatkę `13 x 13` komórek. Każda komórka zawiera pięć pól ograniczenia. Poniżej `boxes` zmiennej Dodaj kod, aby przetworzyć wszystkie pola w każdej z komórek.

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

Wewnątrz pętli wewnętrznej, Oblicz początkową pozycję bieżącego pola w danych wyjściowych modelu jednowymiarowego.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Bezpośrednio poniżej, użyj metody, `ExtractBoundingBoxDimensions` Aby uzyskać wymiary bieżącego pola ograniczenia.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Następnie użyj metody, `GetConfidence` Aby uzyskać pewność dla bieżącego pola ograniczenia.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Następnie użyj `MapBoundingBoxToCell` metody, aby zamapować bieżące pole ograniczenia do bieżącej komórki, która jest przetwarzana.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Przed przeprowadzeniem dalszych operacji przetwarzania Sprawdź, czy wartość ufności jest większa niż podana próg. W przeciwnym razie przetwórz następne pole ograniczenia.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

W przeciwnym razie Kontynuuj przetwarzanie danych wyjściowych. Następnym krokiem jest uzyskanie rozkładu prawdopodobieństwa dla przewidzianych klas dla bieżącego pola ograniczenia przy użyciu `ExtractClasses` metody.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Następnie użyj metody, `GetTopResult` Aby uzyskać wartość i indeks klasy z największym prawdopodobieństwem dla bieżącego pola i obliczyć jego wynik.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

Użyj `topScore` do raz, aby zachować tylko te pola graniczne, które przekraczają określony próg.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Na koniec Jeśli bieżące pole ograniczenia przekracza wartość progową, Utwórz nowy `BoundingBox` obiekt i dodaj go do `boxes` listy.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Po przetworzeniu wszystkich komórek w obrazie Zwróć `boxes` listę. Dodaj następującą instrukcję return poniżej instrukcji Outer-większości dla pętli w `ParseOutputs` metodzie.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Filtrowanie nakładających się pól

Teraz, gdy wszystkie wysoce niegwarantowane pola powiązane zostały wyodrębnione z danych wyjściowych modelu, należy wykonać dodatkowe filtrowanie, aby usunąć nakładające się obrazy. Dodaj metodę o nazwie `FilterBoundingBoxes` poniżej `ParseOutputs` metody:

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

Wewnątrz `FilterBoundingBoxes` metody Zacznij od utworzenia tablicy równej rozmiarowi wykrytych pól i oznaczeniu wszystkich miejsc jako aktywnych lub gotowych do przetworzenia.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Następnie posortuj listę zawierającą pola ograniczenia w kolejności malejącej na podstawie pewności.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Następnie utwórz listę w celu przechowywania przefiltrowanych wyników.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Rozpocznij przetwarzanie każdego pola ograniczenia przez iterację każdego z pól ograniczenia.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Wewnątrz tej pętli for Sprawdź, czy bieżące pole ograniczenia można przetworzyć.

```csharp
if (isActiveBoxes[i])
{

}
```

Jeśli tak, Dodaj pole ograniczenia do listy wyników. Jeśli wyniki przekroczą określony limit pól do wyodrębnienia, należy przerwać pętlę. Dodaj następujący kod wewnątrz instrukcji if.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

W przeciwnym razie Spójrz na sąsiednie pola ograniczające. Dodaj następujący kod poniżej pola wyboru limitu.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

Podobnie jak w przypadku pierwszego pola, Jeśli sąsiadujące pole jest aktywne lub gotowe do przetworzenia, użyj `IntersectionOverUnion` metody, aby sprawdzić, czy pierwsze pole i drugie pole przekracza określoną wartość progową. Dodaj następujący kod do wewnętrznej pętli for.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Poza wewnętrzną pętlą dla pętli, która sprawdza sąsiadujące pola graniczne, sprawdź, czy istnieją wszystkie pozostałe pola ograniczające do przetworzenia. W przeciwnym razie Przerwij z zewnętrznej pętli for.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Na koniec, poza początkową pętlą for `FilterBoundingBoxes` , zwraca wyniki:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Świetnie! Teraz czas na użycie tego kodu wraz z modelem oceniania.

## <a name="use-the-model-for-scoring"></a>Korzystanie z modelu oceniania

Podobnie jak w przypadku przetwarzania końcowego, należy wykonać kilka kroków. Aby to ułatwić, Dodaj klasę, która będzie zawierać logikę oceniania do projektu.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *OnnxModelScorer.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *OnnxModelScorer.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *OnnxModelScorer.cs*:

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    W `OnnxModelScorer` definicji klasy Dodaj następujące zmienne.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Bezpośrednio poniżej, Utwórz konstruktora dla `OnnxModelScorer` klasy, która będzie inicjować zdefiniowane wcześniej zmienne.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Po utworzeniu konstruktora należy zdefiniować kilka struktur zawierających zmienne powiązane z ustawieniami obrazu i modelu. Utwórz strukturę o nazwie, `ImageNetSettings` aby zawierała wysokość i szerokość jako dane wejściowe dla modelu.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Następnie należy utworzyć inną strukturę o nazwie, `TinyYoloModelSettings` która zawiera nazwy warstw wejściowych i wyjściowych modelu. Aby wizualizować nazwę warstw wejściowych i wyjściowych modelu, można użyć narzędzia, takiego jak [Netron](https://github.com/lutzroeder/netron).

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Następnie Utwórz pierwszy zestaw metod do użycia w celu oceny. Utwórz `LoadModel` metodę wewnątrz `OnnxModelScorer` klasy.

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Wewnątrz `LoadModel` metody Dodaj następujący kod do rejestrowania.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    Potoki ML.NET muszą znać schemat danych do działania, gdy [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) wywoływana jest metoda. W takim przypadku zostanie użyty proces podobny do szkoleń. Ponieważ jednak żadne rzeczywiste szkolenie nie jest wykonywane, można go użyć jako pustego [`IDataView`](xref:Microsoft.ML.IDataView) . Utwórz nowy [`IDataView`](xref:Microsoft.ML.IDataView) dla potoku z pustej listy.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Poniżej Zdefiniuj potoku. Potok będzie zawierać cztery przekształcenia.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)ładuje obraz jako mapę bitową.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)przeskaluje obraz do określonego rozmiaru (w tym przypadku `416 x 416` ).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)zmienia reprezentację obrazu z mapy bitowej na wektor numeryczny.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ładuje model ONNX i używa go do oceny dostarczonych danych.

    Zdefiniuj potok w `LoadModel` metodzie poniżej `data` zmiennej.

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Teraz czas na utworzenie wystąpienia modelu oceniania. Wywołaj [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metodę w potoku i zwróć ją na dalsze przetwarzanie.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Po załadowaniu modelu można go użyć do dokonania prognoz. Aby ułatwić ten proces, należy utworzyć metodę o nazwie `PredictDataUsingModel` poniżej `LoadModel` metody.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

W programie `PredictDataUsingModel` Dodaj następujący kod do rejestrowania.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody do oceny danych.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Wyodrębnij przewidywane prawdopodobieństwa i zwróć je do dodatkowego przetwarzania.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Teraz po skonfigurowaniu obu kroków Połącz je w jedną metodę. Poniżej `PredictDataUsingModel` metody Dodaj nową metodę o nazwie `Score` .

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Prawie gotowe! Teraz czas, aby można było go używać.

## <a name="detect-objects"></a>Wykrywanie obiektów

Po zakończeniu wszystkich czynności konfiguracyjnych czas na wykrycie niektórych obiektów. Zacznij od dodania odwołań do scorer i analizatora w klasie *program.cs* .

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Wyniki modelu oceny i analizy

Wewnątrz `Main` metody klasy *program.cs* Dodaj instrukcję try-catch.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

`try`Rozpocznij wdrażanie logiki wykrywania obiektów wewnątrz bloku. Najpierw Załaduj dane do programu [`IDataView`](xref:Microsoft.ML.IDataView) .

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Następnie Utwórz wystąpienie `OnnxModelScorer` i użyj go do oceny załadowanych danych.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Teraz czas wykonywania kroku po przetworzeniu. Utwórz wystąpienie `YoloOutputParser` i użyj go do przetwarzania danych wyjściowych modelu.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Po przetworzeniu danych wyjściowych modelu czas na narysowanie pól związanych z obrazami.

### <a name="visualize-predictions"></a>Wizualizuj przewidywania

Po dokonaniu oceny przez model obrazów i danych wyjściowych pola ograniczenia muszą być rysowane na obrazie. Aby to zrobić, Dodaj metodę o nazwie `DrawBoundingBox` poniżej `GetAbsolutePath` metody w *program.cs*.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

Najpierw Załaduj obraz i uzyskaj wymiary wysokości i szerokości w `DrawBoundingBox` metodzie.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Następnie utwórz pętlę for-each, aby wykonać iterację każdego z pól powiązanych wykrytych przez model.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

Wewnątrz pętli for-each należy uzyskać wymiary powiązanego pola.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Ponieważ wymiary pola ograniczenia odpowiadają na dane wejściowe modelu `416 x 416` , Skaluj Wymiary pola ograniczenia w celu dopasowania do rzeczywistego rozmiaru obrazu.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Następnie zdefiniuj szablon dla tekstu, który będzie wyświetlany powyżej każdego pola ograniczenia. Tekst będzie zawierać klasę obiektu wewnątrz odpowiedniego pola ograniczenia, a także wiarygodność.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Aby rysować na obrazie, przekonwertuj go na [`Graphics`](xref:System.Drawing.Graphics) obiekt.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

W `using` bloku kodu Dostosuj [`Graphics`](xref:System.Drawing.Graphics) Ustawienia obiektu graficznego.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Poniżej Ustaw opcje czcionki i koloru dla pola tekst i granice.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Utwórz i Wypełnij prostokąt powyżej pola ograniczenia, aby zawierać tekst przy użyciu [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) metody. Pomoże to zwiększyć kontrast tekstu i poprawić czytelność.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Następnie należy narysować tekst i obwiednię obrazu przy użyciu [`DrawString`](xref:System.Drawing.Graphics.DrawString*) [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) metod i.

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

Poza pętlą for-each Dodaj kod, aby zapisać obrazy w `outputDirectory` .

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Aby uzyskać dodatkowe informacje o tym, że aplikacja przeprowadza prognozowanie zgodnie z oczekiwaniami w czasie wykonywania, Dodaj metodę o nazwie do `LogDetectedObjects` `DrawBoundingBox` metody w pliku *program.cs* , aby wyszukać wykryte obiekty do konsoli.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Teraz, gdy masz metody pomocnika do tworzenia opinii wizualnych na podstawie prognoz, Dodaj pętlę for, aby wykonać iterację każdego obrazu z wynikami.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

Wewnątrz pętli for należy uzyskać nazwę pliku obrazu i powiązane z nim skojarzone pola.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Poniżej można używać `DrawBoundingBox` metody do rysowania pól ograniczenia na obrazie.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Na koniec użyj metody, `LogDetectedObjects` Aby wyprowadzić przewidywania do konsoli.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Po instrukcji try-catch Dodaj dodatkową logikę, aby wskazać, że proces jest wykonywany.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

To wszystko.

## <a name="results"></a>Wyniki

Po wykonaniu poprzednich kroków uruchom aplikację konsolową (Ctrl + F5). Wyniki powinny wyglądać podobnie do poniższych danych wyjściowych. Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.

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

Aby wyświetlić obrazy z polami obwiedni, przejdź do `assets/images/output/` katalogu. Poniżej znajduje się przykład z jednego z przetworzonych obrazów.

![Przykładowy przetworzony obraz pokoju rekomendowanych lokali](./media/object-detection-onnx/dinning-room-table-chairs.png)

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego na potrzeby wykrywania obiektów przez ponowne użycie wstępnie nauczonego `ONNX` modelu w ml.NET.

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) .

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się, co ONNX i jak działa z ML.NET
> - Zrozumienie modelu
> - Ponownie Użyj wstępnie nauczonego modelu
> - Wykrywanie obiektów z załadowanym modelem

Zapoznaj się z przykładem repozytorium Machine Learning Samples w witrynie GitHub, aby poznać próbkę wykrywania rozwiniętych obiektów.
> [!div class="nextstepaction"]
> [dotnet/machinelearning — przykłady repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
