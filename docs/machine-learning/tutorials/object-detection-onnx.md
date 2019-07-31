---
title: 'Samouczek: Wykrywanie obiektów przy użyciu głębokiej nauki z ONNX i ML.NET'
description: W tym samouczku przedstawiono sposób użycia wstępnie przeszkolonego modelu uczenia głębokiego ONNX w ML.NET do wykrywania obiektów w obrazach.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/31/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: acfff6d409a56e7676c7d38296ecc2085fa131ea
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68672137"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="26bf2-103">Samouczek: Wykrywanie obiektów przy użyciu ONNX w ML.NET</span><span class="sxs-lookup"><span data-stu-id="26bf2-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="26bf2-104">Dowiedz się, jak używać wstępnie przeszkolonego modelu ONNX w programie ML.NET do wykrywania obiektów w obrazach.</span><span class="sxs-lookup"><span data-stu-id="26bf2-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="26bf2-105">Uczenie modelu wykrywania obiektów od podstaw wymaga ustawienia milionów parametrów, dużej ilości danych szkoleniowych i szerokiej ilości zasobów obliczeniowych (setki godzin procesora GPU).</span><span class="sxs-lookup"><span data-stu-id="26bf2-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="26bf2-106">Korzystanie z wstępnie nauczonego modelu umożliwia podwyższenie poziomu procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="26bf2-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="26bf2-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="26bf2-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="26bf2-108">Understand the problem</span></span>
> * <span data-ttu-id="26bf2-109">Dowiedz się, co ONNX i jak działa z ML.NET</span><span class="sxs-lookup"><span data-stu-id="26bf2-109">Learn what ONNX is and how it works with ML.NET</span></span>
> * <span data-ttu-id="26bf2-110">Zrozumienie modelu</span><span class="sxs-lookup"><span data-stu-id="26bf2-110">Understand the model</span></span>
> * <span data-ttu-id="26bf2-111">Ponownie Użyj wstępnie nauczonego modelu</span><span class="sxs-lookup"><span data-stu-id="26bf2-111">Reuse the pre-trained model</span></span>
> * <span data-ttu-id="26bf2-112">Wykrywanie obiektów z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="26bf2-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="26bf2-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="26bf2-113">Pre-requisites</span></span>

- <span data-ttu-id="26bf2-114">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26bf2-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="26bf2-115">Pakiet NuGet Microsoft.ML</span><span class="sxs-lookup"><span data-stu-id="26bf2-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="26bf2-116">Pakiet NuGet Microsoft. ML. ImageAnalytics</span><span class="sxs-lookup"><span data-stu-id="26bf2-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="26bf2-117">Pakiet NuGet Microsoft. ML. OnnxTransformer</span><span class="sxs-lookup"><span data-stu-id="26bf2-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="26bf2-118">Mały model wstępnie przeszkolony YOLOv2</span><span class="sxs-lookup"><span data-stu-id="26bf2-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/tiny_yolov2)
- <span data-ttu-id="26bf2-119">[Netron](https://github.com/lutzroeder/netron) obowiązkowe</span><span class="sxs-lookup"><span data-stu-id="26bf2-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="26bf2-120">Przykład wykrywania obiektów ONNX</span><span class="sxs-lookup"><span data-stu-id="26bf2-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="26bf2-121">Ten przykład służy do tworzenia aplikacji konsolowej .NET Core, która wykrywa obiekty w obrazie przy użyciu wstępnie nauczonego modelu ONNX uczenia głębokiego.</span><span class="sxs-lookup"><span data-stu-id="26bf2-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="26bf2-122">Kod dla tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="26bf2-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="26bf2-123">Co to jest wykrywanie obiektów?</span><span class="sxs-lookup"><span data-stu-id="26bf2-123">What is object detection?</span></span>

<span data-ttu-id="26bf2-124">Wykrywanie obiektów to problem z obsługą komputera.</span><span class="sxs-lookup"><span data-stu-id="26bf2-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="26bf2-125">Chociaż ściśle powiązane z klasyfikacją obrazów, wykrywanie obiektów wykonuje klasyfikację obrazów na bardziej szczegółowym poziomie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="26bf2-126">Wykrywanie obiektów zarówno lokalizuje _, jak i_ klasyfikuje jednostki w obrazach.</span><span class="sxs-lookup"><span data-stu-id="26bf2-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="26bf2-127">Użyj wykrywania obiektów, gdy obrazy zawierają wiele obiektów różnych typów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-127">Use object detection when images contain multiple objects of different types.</span></span>

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="26bf2-128">Niektóre przypadki użycia dotyczące wykrywania obiektów obejmują:</span><span class="sxs-lookup"><span data-stu-id="26bf2-128">Some use cases for object detection include:</span></span>

- <span data-ttu-id="26bf2-129">Samochody samoobsługowe</span><span class="sxs-lookup"><span data-stu-id="26bf2-129">Self-Driving Cars</span></span>
- <span data-ttu-id="26bf2-130">Atrybut</span><span class="sxs-lookup"><span data-stu-id="26bf2-130">Robotics</span></span>
- <span data-ttu-id="26bf2-131">wykrywanie twarzy</span><span class="sxs-lookup"><span data-stu-id="26bf2-131">Face Detection</span></span>
- <span data-ttu-id="26bf2-132">Bezpieczeństwo w miejscu pracy</span><span class="sxs-lookup"><span data-stu-id="26bf2-132">Workplace Safety</span></span>
- <span data-ttu-id="26bf2-133">Zliczanie obiektów</span><span class="sxs-lookup"><span data-stu-id="26bf2-133">Object Counting</span></span>
- <span data-ttu-id="26bf2-134">Rozpoznawanie działań</span><span class="sxs-lookup"><span data-stu-id="26bf2-134">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="26bf2-135">Wybierz model uczenia głębokiego</span><span class="sxs-lookup"><span data-stu-id="26bf2-135">Select a deep learning model</span></span>

<span data-ttu-id="26bf2-136">Uczenie głębokie to podzestaw uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="26bf2-136">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="26bf2-137">Aby szkolić modele uczenia głębokiego, wymagane są duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-137">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="26bf2-138">Wzorce w danych są reprezentowane przez serię warstw.</span><span class="sxs-lookup"><span data-stu-id="26bf2-138">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="26bf2-139">Relacje w danych są kodowane jako połączenia między warstwami zawierającymi wagi.</span><span class="sxs-lookup"><span data-stu-id="26bf2-139">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="26bf2-140">Im wyższa waga, tym silniejszy jest związek.</span><span class="sxs-lookup"><span data-stu-id="26bf2-140">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="26bf2-141">Zbiorczo te serie warstw i połączeń są nazywane sztucznymi sieciami neuronowych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-141">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="26bf2-142">Im więcej warstw w sieci, tym "głębiej" jest to, że jest to sieć głębokiej neuronowych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-142">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span> 

<span data-ttu-id="26bf2-143">Istnieją różne typy sieci neuronowych, najczęściej występujące wielowarstwowe Perceptron (MLP), Splotowych neuronowych Network (CNN) i Recurrent neuronowych Network (RNN).</span><span class="sxs-lookup"><span data-stu-id="26bf2-143">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="26bf2-144">Najbardziej podstawowa jest MLP, która mapuje zestaw danych wejściowych na zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="26bf2-144">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="26bf2-145">Ta sieć neuronowych jest dobra, gdy dane nie zawierają składnika przestrzennego ani czasu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-145">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="26bf2-146">CNN wykorzystuje warstwy splotowych do przetwarzania informacji przestrzennych zawartych w danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-146">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="26bf2-147">Dobrym przypadkiem użycia dla CNNs jest przetwarzanie obrazu w celu wykrycia obecności funkcji w regionie obrazu (na przykład jest to nos na środku obrazu?).</span><span class="sxs-lookup"><span data-stu-id="26bf2-147">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="26bf2-148">Na koniec RNN zezwolić na trwałość stanu lub pamięci jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="26bf2-148">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="26bf2-149">RNN są używane do analizy szeregów czasowych, gdzie ważne jest porządkowanie sekwencyjne i kontekst zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="26bf2-149">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span> 

### <a name="understand-the-model"></a><span data-ttu-id="26bf2-150">Zrozumienie modelu</span><span class="sxs-lookup"><span data-stu-id="26bf2-150">Understand the model</span></span>

<span data-ttu-id="26bf2-151">Wykrywanie obiektów to zadanie przetwarzania obrazu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-151">Object detection is an image processing task.</span></span> <span data-ttu-id="26bf2-152">W związku z tym większość modeli uczenia głębokiego przeszkolonych w celu rozwiązania tego problemu jest CNNs.</span><span class="sxs-lookup"><span data-stu-id="26bf2-152">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="26bf2-153">Model używany w tym samouczku to mały model YOLOv2, bardziej zwarta wersja modelu YOLOv2 opisana w dokumencie: ["YOLO9000: Lepsza, szybsza i silniejsza — RedMon i Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="26bf2-153">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="26bf2-154">Niewielka YOLOv2 jest przeszkolony na zestawie danych LZO w języku Pascal i składa się z 15 warstw, które mogą przewidzieć 20 różnych klas obiektów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-154">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="26bf2-155">Ponieważ mała YOLOv2 to skrócona wersja oryginalnego modelu YOLOv2, kompromis między szybkością i dokładnością jest zwiększany.</span><span class="sxs-lookup"><span data-stu-id="26bf2-155">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="26bf2-156">Różne warstwy, które tworzą model, można wizualizować przy użyciu narzędzi, takich jak Netron.</span><span class="sxs-lookup"><span data-stu-id="26bf2-156">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="26bf2-157">Sprawdzenie modelu spowoduje odwzorowanie połączeń między wszystkimi warstwami tworzącymi sieć neuronowych, gdzie każda warstwa będzie zawierać nazwę warstwy wraz z wymiarami odpowiednich operacji wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-157">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="26bf2-158">Struktury danych używane do opisywania wejścia i wyjścia modelu są znane jako dwuczęściowe.</span><span class="sxs-lookup"><span data-stu-id="26bf2-158">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="26bf2-159">Mogą być uważane za kontenery, które przechowują dane w N-wymiarach.</span><span class="sxs-lookup"><span data-stu-id="26bf2-159">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="26bf2-160">W przypadku bardzo niewielkich YOLOv2 Nazwa warstwy wejściowej jest `image` i oczekuje dwuwymiarowego wymiaru. `3 x 416 x 416`</span><span class="sxs-lookup"><span data-stu-id="26bf2-160">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="26bf2-161">Nazwa warstwy wyjściowej jest `grid` generowana w postaci dwuwymiarowego natężenia wymiarów. `125 x 13 x 13`</span><span class="sxs-lookup"><span data-stu-id="26bf2-161">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>  

![](./media/object-detection-onnx/netron-model-map.png)

<span data-ttu-id="26bf2-162">Model YOLO pobiera obraz `3(RGB) x 416px x 416px`.</span><span class="sxs-lookup"><span data-stu-id="26bf2-162">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="26bf2-163">Model przyjmuje dane wejściowe i przekazuje je za pomocą różnych warstw, aby utworzyć dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="26bf2-163">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="26bf2-164">Dane wyjściowe dzielą obraz wejściowy na `13 x 13` siatkę, z każdą komórką w siatce składającą się z `125` wartości.</span><span class="sxs-lookup"><span data-stu-id="26bf2-164">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span> 

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="26bf2-165">Co to jest model ONNX?</span><span class="sxs-lookup"><span data-stu-id="26bf2-165">What is an ONNX model?</span></span>

<span data-ttu-id="26bf2-166">Open neuronowych Network Exchange (ONNX) to format Open Source dla modeli AI.</span><span class="sxs-lookup"><span data-stu-id="26bf2-166">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="26bf2-167">ONNX obsługuje współdziałanie między strukturami.</span><span class="sxs-lookup"><span data-stu-id="26bf2-167">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="26bf2-168">Oznacza to, że możesz przeszkolić model w jednym z wielu popularnych platform uczenia maszynowego, takich jak PyTorch, przekonwertować go do formatu ONNX i korzystać z modelu ONNX w różnych strukturach, takich jak ML.NET.</span><span class="sxs-lookup"><span data-stu-id="26bf2-168">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="26bf2-169">Aby dowiedzieć się więcej, odwiedź witrynę [sieci Web ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="26bf2-169">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span> 

![](./media/object-detection-onnx/onnx-frameworks.png)

<span data-ttu-id="26bf2-170">Wstępnie szkolony model YOLOv2 jest przechowywany w formacie ONNX, szeregowaną reprezentacją warstw i wyznanie wzorców tych warstw.</span><span class="sxs-lookup"><span data-stu-id="26bf2-170">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="26bf2-171">W programie ml.NET współdziałanie z usługą ONNX jest [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) realizowane [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) przy użyciu pakietów NuGet i.</span><span class="sxs-lookup"><span data-stu-id="26bf2-171">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="26bf2-172">[`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) Pakiet zawiera serię przekształceń, która pobiera obraz i koduje go na wartości liczbowe, które mogą być używane jako dane wejściowe do modelu lub potoku szkoleniowego.</span><span class="sxs-lookup"><span data-stu-id="26bf2-172">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a model or training pipeline.</span></span> <span data-ttu-id="26bf2-173">[`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) Pakiet wykorzystuje środowisko uruchomieniowe ONNX w celu załadowania modelu ONNX i używania go do prognozowania na podstawie dostarczonego danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-173">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span> 

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="26bf2-174">Konfigurowanie projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="26bf2-174">Set up the .NET Core project</span></span>

<span data-ttu-id="26bf2-175">Teraz, gdy masz ogólne informacje o tym, co ONNX się i jak mała YOLOv2 działa, to czas na skompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26bf2-175">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="26bf2-176">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="26bf2-176">Create a console application</span></span>

1. <span data-ttu-id="26bf2-177">Utwórz **aplikację konsolową .NET Core** o nazwie "ObjectDetection".</span><span class="sxs-lookup"><span data-stu-id="26bf2-177">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="26bf2-178">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="26bf2-178">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="26bf2-179">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-179">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> 
    - <span data-ttu-id="26bf2-180">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-180">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> 
    - <span data-ttu-id="26bf2-181">Wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="26bf2-181">Select the **Install** button.</span></span> 
    - <span data-ttu-id="26bf2-182">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-182">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> 
    - <span data-ttu-id="26bf2-183">Powtórz te kroki dla **Microsoft. ml. ImageAnalytics** i **Microsoft. ml. OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-183">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="26bf2-184">Przygotowywanie danych i wstępnie szkolony model</span><span class="sxs-lookup"><span data-stu-id="26bf2-184">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="26bf2-185">Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="26bf2-185">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="26bf2-186">Skopiuj katalog do katalogu projektu *ObjectDetection.* `assets`</span><span class="sxs-lookup"><span data-stu-id="26bf2-186">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="26bf2-187">Ten katalog i jego podkatalogi zawierają pliki obrazów (z wyjątkiem niewielkiego modelu YOLOv2, który zostanie pobrany i dodany w następnym kroku), co jest potrzebne w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="26bf2-187">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="26bf2-188">Pobierz [mały model YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [modelu ONNX zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="26bf2-188">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="26bf2-189">Otwórz wiersz polecenia i wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="26bf2-189">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz 
    ```

1. <span data-ttu-id="26bf2-190">Skopiuj wyodrębniony `model.onnx` plik z katalogu do katalogu `assets\Model` projektu ObjectDetection, a następnie zmień jego nazwę na. `TinyYolo2_model.onnx`</span><span class="sxs-lookup"><span data-stu-id="26bf2-190">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="26bf2-191">Ten katalog zawiera model wymagany dla tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="26bf2-191">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="26bf2-192">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu zasobów i podkatalogach i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-192">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="26bf2-193">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-193">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="26bf2-194">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="26bf2-194">Create classes and define paths</span></span>

<span data-ttu-id="26bf2-195">Otwórz plik *program.cs* i Dodaj następujące dodatkowe `using` instrukcje na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="26bf2-195">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L9)]

<span data-ttu-id="26bf2-196">Następnie zdefiniuj ścieżki różnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-196">Next, define the paths of the various assets.</span></span> 

1. <span data-ttu-id="26bf2-197">Najpierw Dodaj `GetAbsolutePath` metodę `Main` poniżej metody w `Program` klasie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-197">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span> 

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="26bf2-198">Następnie wewnątrz `Main` metody Utwórz pola do przechowywania lokalizacji zasobów:</span><span class="sxs-lookup"><span data-stu-id="26bf2-198">Then, inside the `Main` method, create fields to store the location of your assets:</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="26bf2-199">Dodaj nowy katalog do projektu w celu przechowywania danych wejściowych i klas przewidywania.</span><span class="sxs-lookup"><span data-stu-id="26bf2-199">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="26bf2-200">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="26bf2-201">Gdy nowy folder pojawi się w Eksplorator rozwiązań, nadaj mu nazwę "struktury datastructures".</span><span class="sxs-lookup"><span data-stu-id="26bf2-201">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="26bf2-202">Utwórz klasę danych wejściowych w nowo utworzonym katalogu *struktury* danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-202">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="26bf2-203">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy *katalog struktury* datastructures, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-203">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="26bf2-204">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="26bf2-204">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="26bf2-205">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="26bf2-205">Then, select the **Add** button.</span></span>
     
    <span data-ttu-id="26bf2-206">Plik *ImageNetData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-206">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="26bf2-207">Dodaj następującą `using` instrukcję na początku *ImageNetData.cs*:</span><span class="sxs-lookup"><span data-stu-id="26bf2-207">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="26bf2-208">Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageNetData` klasy do pliku *ImageNetData.cs* :</span><span class="sxs-lookup"><span data-stu-id="26bf2-208">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>
    
    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="26bf2-209">`ImageNetData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="26bf2-209">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="26bf2-210">`ImagePath`zawiera ścieżkę, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="26bf2-210">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="26bf2-211">`Label`zawiera nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="26bf2-211">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="26bf2-212">Ponadto program `ImageNetData` zawiera metodę `ReadFromFile` , która ładuje wiele plików `imageFolder` obrazu przechowywanych w `ImageNetData` określonej ścieżce i zwraca je jako kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-212">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="26bf2-213">Utwórz klasę predykcyjną w katalogu *struktury* danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-213">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="26bf2-214">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy *katalog struktury* datastructures, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-214">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="26bf2-215">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="26bf2-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="26bf2-216">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="26bf2-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="26bf2-217">Plik *ImageNetPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-217">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="26bf2-218">Dodaj następującą `using` instrukcję na początku *ImageNetPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="26bf2-218">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="26bf2-219">Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageNetPrediction` klasy do pliku *ImageNetPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="26bf2-219">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="26bf2-220">`ImageNetPrediction`jest klasą przewidywania i ma następujące `float[]` pole:</span><span class="sxs-lookup"><span data-stu-id="26bf2-220">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="26bf2-221">`PredictedLabel`zawiera wymiary, wynik obiektu i prawdopodobieństwa zajęć dla każdego z pól, które zostały wykryte w obrazie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-221">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="26bf2-222">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="26bf2-222">Initialize variables in Main</span></span>

<span data-ttu-id="26bf2-223">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-223">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="26bf2-224">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="26bf2-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="26bf2-225">`Main` `outputFolder` `MLContext` Zainicjuj zmiennąznowymwystąpieniemprogramu,dodającnastępującywierszdometodyprogram.csponiżejpola.`mlContext`</span><span class="sxs-lookup"><span data-stu-id="26bf2-225">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

### <a name="add-helper-methods"></a><span data-ttu-id="26bf2-226">Dodawanie metod pomocnika</span><span class="sxs-lookup"><span data-stu-id="26bf2-226">Add Helper Methods</span></span>

<span data-ttu-id="26bf2-227">Po przeprowadzeniu prognozy, często nazywanej ocenianiem i przetworzeniu danych wyjściowych, pola ograniczenia muszą być rysowane na obrazie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-227">After the model has made a prediction, commonly referred to as scoring, and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="26bf2-228">Aby to zrobić, Dodaj metodę o nazwie `DrawBoundingBox` do `GetAbsolutePath` metody insode of *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="26bf2-228">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method insode of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="26bf2-229">Najpierw Załaduj obraz i uzyskaj wymiary wysokości i szerokości w `DrawBoundingBox` metodzie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-229">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="26bf2-230">Następnie utwórz pętlę for-each, aby wykonać iterację każdego z pól powiązanych wykrytych przez model.</span><span class="sxs-lookup"><span data-stu-id="26bf2-230">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="26bf2-231">Wewnątrz pętli for-each należy uzyskać wymiary powiązanego pola.</span><span class="sxs-lookup"><span data-stu-id="26bf2-231">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="26bf2-232">Ponieważ wymiary pola ograniczenia odpowiadają na dane wejściowe `416 x 416`modelu, Skaluj Wymiary pola ograniczenia w celu dopasowania do rzeczywistego rozmiaru obrazu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-232">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="26bf2-233">Następnie zdefiniuj szablon dla tekstu, który będzie apear powyżej każdego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-233">Then, define a template for text that will apear above each bounding box.</span></span> <span data-ttu-id="26bf2-234">Tekst będzie zawierać klasę obiektu wewnątrz odpowiedniego pola ograniczenia, a także wiarygodność.</span><span class="sxs-lookup"><span data-stu-id="26bf2-234">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="26bf2-235">Aby rysować na obrazie, przekonwertuj go na [`Graphics`](xref:System.Drawing.Graphics) obiekt.</span><span class="sxs-lookup"><span data-stu-id="26bf2-235">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{
    
}
```

<span data-ttu-id="26bf2-236">[`Graphics`](xref:System.Drawing.Graphics) W bloku `using` kodu Dostosuj ustawienia obiektu graficznego.</span><span class="sxs-lookup"><span data-stu-id="26bf2-236">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="26bf2-237">Poniżej Ustaw opcje czcionki i koloru dla pola tekst i granice.</span><span class="sxs-lookup"><span data-stu-id="26bf2-237">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="26bf2-238">Utwórz i Wypełnij prostokąt powyżej pola ograniczenia, aby zawierać tekst przy użyciu [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) metody.</span><span class="sxs-lookup"><span data-stu-id="26bf2-238">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="26bf2-239">Pomoże to zwiększyć kontrast tekstu i poprawić czytelność.</span><span class="sxs-lookup"><span data-stu-id="26bf2-239">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="26bf2-240">Następnie należy narysować tekst i obwiednię obrazu przy użyciu [`DrawString`](xref:System.Drawing.Graphics.DrawString*) metod i. [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*)</span><span class="sxs-lookup"><span data-stu-id="26bf2-240">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="26bf2-241">Poza pętlą for-each Dodaj kod, aby zapisać obrazy w `outputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="26bf2-241">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="26bf2-242">Aby uzyskać dodatkowe informacje o tym, że aplikacja przeprowadza prognozowanie zgodnie z oczekiwaniami w czasie wykonywania, `LogDetectedObjects` Dodaj metodę `DrawBoundingBox` wywołana poniżej metody w pliku *program.cs* , aby wypróbować wykryte obiekty do konsoli.</span><span class="sxs-lookup"><span data-stu-id="26bf2-242">To get additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOuptuts](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="26bf2-243">Obie te metody będą przydatne, gdy model wygenerował dane wyjściowe i zostały przetworzone.</span><span class="sxs-lookup"><span data-stu-id="26bf2-243">Both of these methods will be useful when the model has produced outputs and those have been processed.</span></span> <span data-ttu-id="26bf2-244">Najpierw Utwórz funkcję do przetwarzania danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-244">First though, create the functionality to process the model outputs.</span></span>

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="26bf2-245">Tworzenie analizatora danych wyjściowych modelu po procesie</span><span class="sxs-lookup"><span data-stu-id="26bf2-245">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="26bf2-246">Model segmentuje obraz w `13 x 13` siatce, gdzie każda komórka siatki ma wartość. `32px x 32px`</span><span class="sxs-lookup"><span data-stu-id="26bf2-246">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="26bf2-247">Każda komórka siatki zawiera 5 potencjalnych pól związanych z obiektem.</span><span class="sxs-lookup"><span data-stu-id="26bf2-247">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="26bf2-248">Pole ograniczenia ma 25 elementów:</span><span class="sxs-lookup"><span data-stu-id="26bf2-248">A bounding box has  25 elements:</span></span>

![](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="26bf2-249">`x`Pozycja x środka pola ograniczenia względem komórki siatki, z którą jest skojarzona.</span><span class="sxs-lookup"><span data-stu-id="26bf2-249">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="26bf2-250">`y`Pozycja y środka pola ograniczenia względem komórki siatki, z którą jest skojarzona.</span><span class="sxs-lookup"><span data-stu-id="26bf2-250">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="26bf2-251">`w`Szerokość pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-251">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="26bf2-252">`h`Wysokość pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-252">`h` the height of the bounding box.</span></span> 
- <span data-ttu-id="26bf2-253">`o`wartość ufności, która istnieje w polu ograniczenia, znana także jako wynik Abjectness.</span><span class="sxs-lookup"><span data-stu-id="26bf2-253">`o` the confidence value that an object exists within the bounding box, also known as Abjectness score.</span></span>
- <span data-ttu-id="26bf2-254">`p1-p20`prawdopodobieństwa klasy dla każdej z 20 klas przewidywanych przez model.</span><span class="sxs-lookup"><span data-stu-id="26bf2-254">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="26bf2-255">Łącznie 25 elementów opisujących każde z 5 pól ograniczenia tworzą elementy 125 zawarte w każdej komórce siatki.</span><span class="sxs-lookup"><span data-stu-id="26bf2-255">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="26bf2-256">Dane wyjściowe generowane przez wstępnie szkolony model ONNX są tablicą zmiennoprzecinkową o długości `21125`reprezentującą elementy Dwupunktowe z wymiarami. `125 x 13 x 13`</span><span class="sxs-lookup"><span data-stu-id="26bf2-256">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="26bf2-257">Aby przekształcić przewidywania wygenerowane przez model na dwuczęściowy, wymagana jest część pracy wykonywanej po przetworzeniu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-257">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="26bf2-258">W tym celu należy utworzyć zestaw klas, aby ułatwić analizowanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-258">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="26bf2-259">Dodaj nowy katalog do projektu, aby zorganizować zestaw klas parsera.</span><span class="sxs-lookup"><span data-stu-id="26bf2-259">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="26bf2-260">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-260">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="26bf2-261">Gdy nowy folder pojawi się w Eksplorator rozwiązań, nadaj mu nazwę "YoloParser".</span><span class="sxs-lookup"><span data-stu-id="26bf2-261">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="26bf2-262">Tworzenie pól ograniczenia i wymiarów</span><span class="sxs-lookup"><span data-stu-id="26bf2-262">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="26bf2-263">Dane wyjściowe przez model zawierają współrzędne i wymiary pól ograniczenia obiektów w obrazie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-263">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="26bf2-264">Utwórz klasę bazową dla wymiarów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-264">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="26bf2-265">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-265">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="26bf2-266">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="26bf2-266">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="26bf2-267">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="26bf2-267">Then, select the **Add** button.</span></span>

    <span data-ttu-id="26bf2-268">Plik *DimensionsBase.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-268">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="26bf2-269">Usuń wszystkie `using` instrukcje i istniejącą definicję klasy.</span><span class="sxs-lookup"><span data-stu-id="26bf2-269">Remove all `using` statements and existing class definition.</span></span> 

    <span data-ttu-id="26bf2-270">Dodaj następujący kod dla `DimensionsBase` klasy do pliku *DimensionsBase.cs* :</span><span class="sxs-lookup"><span data-stu-id="26bf2-270">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="26bf2-271">`DimensionsBase`ma następujące `float` pola:</span><span class="sxs-lookup"><span data-stu-id="26bf2-271">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="26bf2-272">`X`zawiera położenie obiektu wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="26bf2-272">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="26bf2-273">`Y`zawiera położenie obiektu wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="26bf2-273">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="26bf2-274">`Height`zawiera wysokość obiektu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-274">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="26bf2-275">`Width`zawiera szerokość obiektu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-275">`Width` contains the width of the object.</span></span>

<span data-ttu-id="26bf2-276">Następnie Utwórz klasę dla pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-276">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="26bf2-277">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-277">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="26bf2-278">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="26bf2-278">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="26bf2-279">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="26bf2-279">Then, select the **Add** button.</span></span>

    <span data-ttu-id="26bf2-280">Plik *YoloBoundingBox.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-280">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="26bf2-281">Dodaj następującą `using` instrukcję na początku *YoloBoundingBox.cs*:</span><span class="sxs-lookup"><span data-stu-id="26bf2-281">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="26bf2-282">Tuż powyżej istniejącej definicji klasy Dodaj nową definicję klasy o nazwie `BoundingBoxDimensions` , która dziedziczy `DimensionsBase` z klasy, aby zawierała wymiary odpowiedniego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-282">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="26bf2-283">Usuń istniejącą `YoloBoundingBox` definicję klasy i Dodaj następujący kod `YoloBoundingBox` dla klasy do pliku *YoloBoundingBox.cs* :</span><span class="sxs-lookup"><span data-stu-id="26bf2-283">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]
    
    <span data-ttu-id="26bf2-284">`YoloBoundingBox`ma następujące pola:</span><span class="sxs-lookup"><span data-stu-id="26bf2-284">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="26bf2-285">`Dimensions`zawiera wymiary powiązanego pola.</span><span class="sxs-lookup"><span data-stu-id="26bf2-285">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="26bf2-286">`Label`zawiera klasę obiektu wykryty w polu ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-286">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="26bf2-287">`Confidence`zawiera zaufanie do klasy.</span><span class="sxs-lookup"><span data-stu-id="26bf2-287">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="26bf2-288">`Rect`zawiera reprezentację prostokąta wymiarów powiązanego pola.</span><span class="sxs-lookup"><span data-stu-id="26bf2-288">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="26bf2-289">`BoxColor`zawiera kolor skojarzony z odpowiednią klasą używaną do rysowania na obrazie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-289">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="26bf2-290">Tworzenie analizatora</span><span class="sxs-lookup"><span data-stu-id="26bf2-290">Create the parser</span></span>

<span data-ttu-id="26bf2-291">Teraz, gdy tworzone są klasy wymiarów i pól powiązanych, czas na utworzenie analizatora.</span><span class="sxs-lookup"><span data-stu-id="26bf2-291">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="26bf2-292">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-292">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="26bf2-293">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="26bf2-293">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="26bf2-294">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="26bf2-294">Then, select the **Add** button.</span></span>

    <span data-ttu-id="26bf2-295">Plik *YoloOutputParser.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-295">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="26bf2-296">Dodaj następującą `using` instrukcję na początku *YoloOutputParser.cs*:</span><span class="sxs-lookup"><span data-stu-id="26bf2-296">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="26bf2-297">Wewnątrz istniejącej `YoloOutputParser` definicji klasy Dodaj zagnieżdżoną klasę, która zawiera wymiary każdej komórki w obrazie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-297">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="26bf2-298">Dodaj następujący kod dla `CellDimensions` klasy, która dziedziczy `DimensionsBase` z klasy `YoloOutputParser` w górnej części definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="26bf2-298">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="26bf2-299">Wewnątrz definicji `YoloOutputParser` klasy Dodaj następujące stałe i pola.</span><span class="sxs-lookup"><span data-stu-id="26bf2-299">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]    

    - <span data-ttu-id="26bf2-300">`ROW_COUNT`to liczba wierszy w siatce, do których jest podzielona ilustracja.</span><span class="sxs-lookup"><span data-stu-id="26bf2-300">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="26bf2-301">`COL_COUNT`jest liczbą kolumn w siatce, w której jest podzielony obraz.</span><span class="sxs-lookup"><span data-stu-id="26bf2-301">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="26bf2-302">`CHANNEL_COUNT`to całkowita liczba wartości zawartych w jednej komórce siatki.</span><span class="sxs-lookup"><span data-stu-id="26bf2-302">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="26bf2-303">`BOXES_PER_CELL`jest liczbą pól ograniczenia w komórce,</span><span class="sxs-lookup"><span data-stu-id="26bf2-303">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="26bf2-304">`BOX_INFO_FEATURE_COUNT`to liczba funkcji zawartych w polu (x, y, wysokość, Szerokość, pewność).</span><span class="sxs-lookup"><span data-stu-id="26bf2-304">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="26bf2-305">`CLASS_COUNT`to liczba prognoz klas zawartych w każdym polu ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-305">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="26bf2-306">`CELL_WIDTH`jest szerokością jednej komórki w siatce obrazu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-306">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="26bf2-307">`CELL_HEIGHT`to wysokość jednej komórki w siatce obrazu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-307">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="26bf2-308">`channelStride`jest pozycją początkową bieżącej komórki siatki.</span><span class="sxs-lookup"><span data-stu-id="26bf2-308">`channelStride` is the starting position of the current cell in the grid.</span></span>


    <span data-ttu-id="26bf2-309">Gdy model ocenia obraz, dzieli `416px x 416px`dane wejściowe na siatkę komórek o `13 x 13`rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="26bf2-309">When the model scores an image, it divides the `416px x 416px`input into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="26bf2-310">Każda komórka zawiera `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="26bf2-310">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="26bf2-311">W każdej komórce istnieją 5 pól, które zawierają 5 funkcji (x, y, Szerokość, wysokość, pewność).</span><span class="sxs-lookup"><span data-stu-id="26bf2-311">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="26bf2-312">Ponadto każde pole ograniczenia zawiera prawdopodobieństwo dla każdej klasy, która w tym przypadku jest równa 20.</span><span class="sxs-lookup"><span data-stu-id="26bf2-312">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="26bf2-313">W związku z tym każda komórka zawiera 125 fragmenty informacji (5 funkcji + 20 prawdopodobieństwa dotyczącej klasy).</span><span class="sxs-lookup"><span data-stu-id="26bf2-313">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span> 

<span data-ttu-id="26bf2-314">Utwórz listę kotwic poniżej `channelStride` dla wszystkich 5 pól ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="26bf2-314">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]   

<span data-ttu-id="26bf2-315">Kotwice to wstępnie zdefiniowany stosunek wysokości i szerokości pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-315">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="26bf2-316">Większość obiektów lub klas wykrywanych przez model ma podobne wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="26bf2-316">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="26bf2-317">Jest to przydatne, gdy chodzi o tworzenie pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-317">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="26bf2-318">Zamiast przewidywania pól powiązanych, obliczane są przesunięcie ze wstępnie zdefiniowanych wymiarów w związku z tym redukcja obliczeń wymaganych do przewidywania pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-318">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="26bf2-319">Zazwyczaj te współczynniki zakotwiczenia są obliczane na podstawie używanego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-319">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="26bf2-320">W tym przypadku, ponieważ zestaw danych jest znany i wartości zostały wstępnie obliczone, kotwice mogą być zakodowane na stałe.</span><span class="sxs-lookup"><span data-stu-id="26bf2-320">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="26bf2-321">Następnie zdefiniuj etykiety lub klasy, które będą przewidywalne przez model.</span><span class="sxs-lookup"><span data-stu-id="26bf2-321">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="26bf2-322">Ten model przewiduje 20 klas, które są podzbiorem całkowitej liczby klas przewidywanych przez oryginalny model YOLOv2.</span><span class="sxs-lookup"><span data-stu-id="26bf2-322">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="26bf2-323">Dodaj listę etykiet poniżej `anchors`.</span><span class="sxs-lookup"><span data-stu-id="26bf2-323">Add your list of labels below the `anchors`.</span></span> 

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="26bf2-324">Istnieją kolory skojarzone z każdą z klas.</span><span class="sxs-lookup"><span data-stu-id="26bf2-324">There are colors associated with each of the classes.</span></span> <span data-ttu-id="26bf2-325">Przypisz kolory klasy poniżej `labels`:</span><span class="sxs-lookup"><span data-stu-id="26bf2-325">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="26bf2-326">Tworzenie funkcji pomocnika</span><span class="sxs-lookup"><span data-stu-id="26bf2-326">Create helper functions</span></span>

<span data-ttu-id="26bf2-327">Etap przetwarzania końcowego obejmuje szereg kroków.</span><span class="sxs-lookup"><span data-stu-id="26bf2-327">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="26bf2-328">Aby pomóc w tym, można zastosować kilka metod pomocnika.</span><span class="sxs-lookup"><span data-stu-id="26bf2-328">To help with that, several helper methods can be employed.</span></span> 

<span data-ttu-id="26bf2-329">Metody pomocnika używane przez parser są następujące:</span><span class="sxs-lookup"><span data-stu-id="26bf2-329">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="26bf2-330">`Sigmoid`stosuje funkcję sigmoid, która wyprowadza liczbę z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="26bf2-330">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="26bf2-331">`Softmax`normalizuje wektor wejściowy do rozkładu prawdopodobieństwa.</span><span class="sxs-lookup"><span data-stu-id="26bf2-331">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="26bf2-332">`GetOffset`mapuje elementy w danych wyjściowych modelu jednowymiarowego do odpowiedniej pozycji w `125 x 13 x 13` dwukierunkowym.</span><span class="sxs-lookup"><span data-stu-id="26bf2-332">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="26bf2-333">`ExtractBoundingBoxes`wyodrębnia Wymiary pola ograniczenia przy użyciu `GetOffset` metody z danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-333">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="26bf2-334">`GetConfidence`Wyodrębnia wartość pewności, która określa, jak upewnić się, że model wykrył obiekt i używa `Sigmoid` funkcji, aby przekształcić ją w wartość procentową.</span><span class="sxs-lookup"><span data-stu-id="26bf2-334">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="26bf2-335">`MapBoundingBoxToCell`używa wymiarów pola ograniczenia i mapuje je na odpowiednią komórkę w obrazie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-335">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="26bf2-336">`ExtractClasses`wyodrębnia przewidywania klas dla pola ograniczenia z danych wyjściowych modelu przy użyciu `GetOffset` metody i włącza je do dystrybucji prawdopodobieństwa `Softmax` przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="26bf2-336">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="26bf2-337">`GetTopResult`wybiera klasę z listy przewidywanych klas o największym prawdopodobieństwie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-337">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="26bf2-338">`IntersectionOverUnion`filtruje nakładające się pola ograniczające o mniejsze prawdopodobieństwa.</span><span class="sxs-lookup"><span data-stu-id="26bf2-338">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="26bf2-339">Dodaj kod dla wszystkich metod pomocników znajdujących się poniżej listy `classColors`.</span><span class="sxs-lookup"><span data-stu-id="26bf2-339">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="26bf2-340">Po zdefiniowaniu wszystkich metod pomocnika czas na jego użycie będzie przetwarzać dane wyjściowe modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-340">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="26bf2-341">`IntersectionOverUnion` Poniżej metody`ParseOutputs` Utwórz metodę, aby przetworzyć dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="26bf2-341">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```
    
<span data-ttu-id="26bf2-342">Utwórz listę do przechowywania pól ograniczenia i zdefiniuj zmienne wewnątrz `ParseOutputs` metody.</span><span class="sxs-lookup"><span data-stu-id="26bf2-342">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="26bf2-343">Każdy obraz jest podzielony na siatkę `13 x 13` komórek.</span><span class="sxs-lookup"><span data-stu-id="26bf2-343">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="26bf2-344">Każda komórka zawiera pięć pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-344">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="26bf2-345">`boxes` Poniżej zmiennej Dodaj kod, aby przetworzyć wszystkie pola w każdej z komórek.</span><span class="sxs-lookup"><span data-stu-id="26bf2-345">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

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

<span data-ttu-id="26bf2-346">Wewnątrz pętli wewnętrznej, Oblicz początkową pozycję bieżącego pola w danych wyjściowych modelu jednowymiarowego.</span><span class="sxs-lookup"><span data-stu-id="26bf2-346">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="26bf2-347">Bezpośrednio poniżej, użyj `ExtractBoundingBoxDimensions` metody, aby uzyskać wymiary bieżącego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-347">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="26bf2-348">Następnie użyj `GetConfidence` metody, aby uzyskać pewność dla bieżącego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-348">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="26bf2-349">Następnie użyj `MapBoundingBoxToCell` metody, aby zamapować bieżące pole ograniczenia do bieżącej komórki, która jest przetwarzana.</span><span class="sxs-lookup"><span data-stu-id="26bf2-349">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="26bf2-350">Przed przeprowadzeniem dalszych operacji przetwarzania Sprawdź, czy wartość ufności jest większa niż podana próg.</span><span class="sxs-lookup"><span data-stu-id="26bf2-350">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="26bf2-351">W przeciwnym razie przetwórz następne pole ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-351">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="26bf2-352">W przeciwnym razie Kontynuuj przetwarzanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-352">Otherwise, continue processing the output.</span></span> <span data-ttu-id="26bf2-353">Następnym krokiem jest uzyskanie rozkładu prawdopodobieństwa dla przewidzianych klas dla bieżącego pola ograniczenia przy użyciu `ExtractClasses` metody.</span><span class="sxs-lookup"><span data-stu-id="26bf2-353">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="26bf2-354">Następnie użyj `GetTopResult` metody, aby uzyskać wartość i indeks klasy z największym prawdopodobieństwem dla bieżącego pola i obliczyć jego wynik.</span><span class="sxs-lookup"><span data-stu-id="26bf2-354">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="26bf2-355">`topScore` Użyj do raz, aby zachować tylko te pola graniczne, które przekraczają określony próg.</span><span class="sxs-lookup"><span data-stu-id="26bf2-355">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="26bf2-356">Na koniec Jeśli bieżące pole ograniczenia przekracza wartość progową, Utwórz nowy `BoundingBox` obiekt i dodaj go `boxes` do listy.</span><span class="sxs-lookup"><span data-stu-id="26bf2-356">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="26bf2-357">Po przetworzeniu wszystkich komórek w obrazie Zwróć `boxes` listę.</span><span class="sxs-lookup"><span data-stu-id="26bf2-357">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="26bf2-358">Dodaj następującą instrukcję return poniżej instrukcji Outer-większości dla pętli w `ParseOutputs` metodzie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-358">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="26bf2-359">Filtrowanie nakładających się pól</span><span class="sxs-lookup"><span data-stu-id="26bf2-359">Filter overlapping boxes</span></span>

<span data-ttu-id="26bf2-360">Teraz, gdy wszystkie wysoce niegwarantowane pola powiązane zostały wyodrębnione z danych wyjściowych modelu, należy wykonać dodatkowe filtrowanie, aby usunąć nakładające się obrazy.</span><span class="sxs-lookup"><span data-stu-id="26bf2-360">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="26bf2-361">Dodaj metodę o nazwie `FilterBoundingBoxes` `ParseOutputs` poniżej metody:</span><span class="sxs-lookup"><span data-stu-id="26bf2-361">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="26bf2-362">`FilterBoundingBoxes` Wewnątrz metody Zacznij od utworzenia tablicy równej rozmiarowi wykrytych pól i oznaczeniu wszystkich miejsc jako aktywnych lub gotowych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-362">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="26bf2-363">Następnie posortuj listę zawierającą pola ograniczenia w kolejności malejącej na podstawie pewności.</span><span class="sxs-lookup"><span data-stu-id="26bf2-363">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="26bf2-364">Następnie utwórz listę w celu przechowywania przefiltrowanych wyników.</span><span class="sxs-lookup"><span data-stu-id="26bf2-364">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="26bf2-365">Rozpocznij przetwarzanie każdego pola ograniczenia przez iterację każdego z pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-365">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="26bf2-366">Wewnątrz tej pętli for Sprawdź, czy bieżące pole ograniczenia można przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="26bf2-366">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{
    
}
```

<span data-ttu-id="26bf2-367">Jeśli tak, Dodaj pole ograniczenia do listy wyników.</span><span class="sxs-lookup"><span data-stu-id="26bf2-367">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="26bf2-368">Jeśli wyniki przekraczają określony limit pól do wyodrębnienia, należy przerwać pętlę.</span><span class="sxs-lookup"><span data-stu-id="26bf2-368">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="26bf2-369">Dodaj następujący kod wewnątrz instrukcji if.</span><span class="sxs-lookup"><span data-stu-id="26bf2-369">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="26bf2-370">W przeciwnym razie Spójrz na sąsiednie pola ograniczające.</span><span class="sxs-lookup"><span data-stu-id="26bf2-370">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="26bf2-371">Dodaj następujący kod poniżej pola wyboru limitu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-371">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="26bf2-372">Podobnie jak w przypadku pierwszego pola, Jeśli sąsiadujące pole jest aktywne lub gotowe do przetworzenia, `IntersectionOverUnion` Użyj metody, aby sprawdzić, czy pierwsze pole i drugie pole przekracza określoną wartość progową.</span><span class="sxs-lookup"><span data-stu-id="26bf2-372">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="26bf2-373">Dodaj następujący kod do wewnętrznej, najbardziej używanej pętli for.</span><span class="sxs-lookup"><span data-stu-id="26bf2-373">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="26bf2-374">Poza wewnętrzną pętlą dla pętli, która sprawdza sąsiadujące pola graniczne, sprawdź, czy istnieją wszystkie pozostałe pola ograniczające do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-374">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="26bf2-375">W przeciwnym razie Przerwij z zewnętrznej pętli for.</span><span class="sxs-lookup"><span data-stu-id="26bf2-375">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="26bf2-376">Na koniec, poza początkową pętlą `FilterBoundingBoxes` for, zwraca wyniki:</span><span class="sxs-lookup"><span data-stu-id="26bf2-376">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="26bf2-377">Znakomity!</span><span class="sxs-lookup"><span data-stu-id="26bf2-377">Great!</span></span> <span data-ttu-id="26bf2-378">Teraz czas na użycie tego kodu wraz z modelem oceniania.</span><span class="sxs-lookup"><span data-stu-id="26bf2-378">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="26bf2-379">Korzystanie z modelu oceniania</span><span class="sxs-lookup"><span data-stu-id="26bf2-379">Use the model for scoring</span></span>

<span data-ttu-id="26bf2-380">Podobnie jak w przypadku przetwarzania końcowego, należy wykonać kilka kroków.</span><span class="sxs-lookup"><span data-stu-id="26bf2-380">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="26bf2-381">Aby to ułatwić, Dodaj klasę, która będzie zawierać logikę oceniania do projektu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-381">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="26bf2-382">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="26bf2-382">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="26bf2-383">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="26bf2-383">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="26bf2-384">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="26bf2-384">Then, select the **Add** button.</span></span>

    <span data-ttu-id="26bf2-385">Plik *OnnxModelScorer.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-385">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="26bf2-386">Dodaj następującą `using` instrukcję na początku *OnnxModelScorer.cs*:</span><span class="sxs-lookup"><span data-stu-id="26bf2-386">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="26bf2-387">W definicji `OnnxModelScorer` klasy Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="26bf2-387">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="26bf2-388">Bezpośrednio poniżej, Utwórz konstruktora dla `OnnxModelScorer` klasy, która będzie inicjować zdefiniowane wcześniej zmienne.</span><span class="sxs-lookup"><span data-stu-id="26bf2-388">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="26bf2-389">Po utworzeniu konstruktora należy zdefiniować kilka struktur zawierających zmienne powiązane z ustawieniami obrazu i modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-389">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="26bf2-390">Utwórz strukturę o nazwie `ImageNetSettings` , aby zawierała wysokość i szerokość jako dane wejściowe dla modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-390">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="26bf2-391">Następnie należy utworzyć inną strukturę o nazwie `TinyYoloModelSettings` , która zawiera nazwy warstw wejściowych i wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-391">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="26bf2-392">Aby wizualizować nazwę warstw wejściowych i wyjściowych modelu, można użyć narzędzia, takiego jak [Netron](https://github.com/lutzroeder/netron).</span><span class="sxs-lookup"><span data-stu-id="26bf2-392">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="26bf2-393">Następnie Utwórz pierwszy zestaw metod do użycia w celu oceny.</span><span class="sxs-lookup"><span data-stu-id="26bf2-393">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="26bf2-394">Utwórz metodę wewnątrz `OnnxModelScorer`klasy. `LoadModel`</span><span class="sxs-lookup"><span data-stu-id="26bf2-394">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="26bf2-395">`LoadModel` Wewnątrz metody Dodaj następujący kod do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="26bf2-395">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="26bf2-396">Potoki ml.NET zazwyczaj oczekują, że dane będą działać [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) przy wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="26bf2-396">ML.NET pipelines typically expect data to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="26bf2-397">W takim przypadku zostanie użyty proces podobny do szkoleń.</span><span class="sxs-lookup"><span data-stu-id="26bf2-397">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="26bf2-398">Ponieważ jednak żadne rzeczywiste szkolenie nie jest wykonywane, można go użyć jako pustego [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="26bf2-398">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="26bf2-399">Utwórz nowy [`IDataView`](xref:Microsoft.ML.IDataView) dla potoku z pustej listy.</span><span class="sxs-lookup"><span data-stu-id="26bf2-399">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]    

    <span data-ttu-id="26bf2-400">Poniżej Zdefiniuj potoku.</span><span class="sxs-lookup"><span data-stu-id="26bf2-400">Below that, define the pipeline.</span></span> <span data-ttu-id="26bf2-401">Potok będzie zawierać cztery przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="26bf2-401">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="26bf2-402">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)ładuje obraz jako mapę bitową.</span><span class="sxs-lookup"><span data-stu-id="26bf2-402">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="26bf2-403">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)przeskaluje obraz do określonego rozmiaru (w tym przypadku `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="26bf2-403">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="26bf2-404">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)zmienia reprezentację obrazu z mapy bitowej na wektor numeryczny.</span><span class="sxs-lookup"><span data-stu-id="26bf2-404">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="26bf2-405">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ładuje model ONNX i używa go do oceny dostarczonych danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-405">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="26bf2-406">Zdefiniuj potok w `LoadModel` metodzie `data` poniżej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="26bf2-406">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="26bf2-407">Teraz czas na utworzenie wystąpienia modelu oceniania.</span><span class="sxs-lookup"><span data-stu-id="26bf2-407">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="26bf2-408">Wywołaj [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metodę w potoku i zwróć ją na dalsze przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-408">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="26bf2-409">Po załadowaniu modelu można go użyć do dokonania prognoz.</span><span class="sxs-lookup"><span data-stu-id="26bf2-409">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="26bf2-410">Aby ułatwić ten proces, należy utworzyć metodę o `PredictDataUsingModel` nazwie `LoadModel` poniżej metody.</span><span class="sxs-lookup"><span data-stu-id="26bf2-410">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="26bf2-411">`PredictDataUsingModel`W programie Dodaj następujący kod do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="26bf2-411">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="26bf2-412">Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody do oceny danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-412">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="26bf2-413">Wyodrębnij przewidywane prawdopodobieństwa i zwróć je do dodatkowego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="26bf2-413">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="26bf2-414">Teraz po skonfigurowaniu obu kroków Połącz je w jedną metodę.</span><span class="sxs-lookup"><span data-stu-id="26bf2-414">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="26bf2-415">Poniżej metody Dodaj nową metodę o nazwie `Score`. `PredictDataUsingModel`</span><span class="sxs-lookup"><span data-stu-id="26bf2-415">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="26bf2-416">Prawie gotowe!</span><span class="sxs-lookup"><span data-stu-id="26bf2-416">Almost there!</span></span> <span data-ttu-id="26bf2-417">Teraz czas, aby można było go używać.</span><span class="sxs-lookup"><span data-stu-id="26bf2-417">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="26bf2-418">Wykryj obiekty</span><span class="sxs-lookup"><span data-stu-id="26bf2-418">Detect objects</span></span>

<span data-ttu-id="26bf2-419">Po zakończeniu wszystkich czynności konfiguracyjnych czas na wykrycie niektórych obiektów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-419">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="26bf2-420">Wewnątrz metody klasy program.cs Dodaj instrukcję try-catch. `Main`</span><span class="sxs-lookup"><span data-stu-id="26bf2-420">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="26bf2-421">Rozpocznij wdrażanie logiki wykrywania obiektów wewnątrz bloku.`try`</span><span class="sxs-lookup"><span data-stu-id="26bf2-421">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="26bf2-422">Najpierw Załaduj dane do programu [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="26bf2-422">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="26bf2-423">Następnie Utwórz wystąpienie `OnnxModelScorer` i użyj go do oceny załadowanych danych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-423">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="26bf2-424">Teraz czas wykonywania kroku po przetworzeniu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-424">Now it's time for the post-processing step.</span></span> <span data-ttu-id="26bf2-425">Utwórz wystąpienie `YoloOutputParser` i użyj go do przetwarzania danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-425">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="26bf2-426">Po przetworzeniu danych wyjściowych modelu czas na narysowanie pól związanych z obrazami.</span><span class="sxs-lookup"><span data-stu-id="26bf2-426">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span> <span data-ttu-id="26bf2-427">Utwórz pętlę for, aby wykonać iterację każdego obrazu z wynikami.</span><span class="sxs-lookup"><span data-stu-id="26bf2-427">Create a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="26bf2-428">Wewnątrz pętli for należy uzyskać nazwę pliku obrazu i powiązane z nim skojarzone pola.</span><span class="sxs-lookup"><span data-stu-id="26bf2-428">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="26bf2-429">Poniżej można używać `DrawBoundingBox` metody do rysowania pól ograniczenia na obrazie.</span><span class="sxs-lookup"><span data-stu-id="26bf2-429">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="26bf2-430">Na koniec Dodaj kilka logiki rejestrowania za pomocą `LogDetectedObjects` metody.</span><span class="sxs-lookup"><span data-stu-id="26bf2-430">Lastly, add some logging logic with the `LogDetectedObjects` method.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]


<span data-ttu-id="26bf2-431">Po instrukcji try-catch Dodaj dodatkową logikę, aby wskazać, że proces jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="26bf2-431">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="26bf2-432">To wszystko!</span><span class="sxs-lookup"><span data-stu-id="26bf2-432">That's it!</span></span> 

## <a name="results"></a><span data-ttu-id="26bf2-433">Wyniki</span><span class="sxs-lookup"><span data-stu-id="26bf2-433">Results</span></span> 

<span data-ttu-id="26bf2-434">Po wykonaniu poprzednich kroków uruchom aplikację konsolową (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="26bf2-434">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="26bf2-435">Wyniki powinny wyglądać podobnie do poniższych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="26bf2-435">Your results should be similar to the following output.</span></span> <span data-ttu-id="26bf2-436">Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="26bf2-436">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="26bf2-437">Aby wyświetlić obrazy z polami obwiedni, przejdź do `assets/images/output/` katalogu.</span><span class="sxs-lookup"><span data-stu-id="26bf2-437">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="26bf2-438">Poniżej znajduje się przykład z jednego z przetworzonych obrazów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-438">Below is a sample from one of the processed images.</span></span> 

![](./media/object-detection-onnx/image3.jpg)

<span data-ttu-id="26bf2-439">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="26bf2-439">Congratulations!</span></span> <span data-ttu-id="26bf2-440">Pomyślnie skompilowano model uczenia maszynowego na potrzeby wykrywania obiektów przez ponowne użycie wstępnie nauczonego `ONNX` modelu w ml.NET.</span><span class="sxs-lookup"><span data-stu-id="26bf2-440">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="26bf2-441">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) .</span><span class="sxs-lookup"><span data-stu-id="26bf2-441">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="26bf2-442">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="26bf2-442">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="26bf2-443">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="26bf2-443">Understand the problem</span></span>
> * <span data-ttu-id="26bf2-444">Dowiedz się, co ONNX i jak działa z ML.NET</span><span class="sxs-lookup"><span data-stu-id="26bf2-444">Learn what ONNX is and how it works with ML.NET</span></span>
> * <span data-ttu-id="26bf2-445">Zrozumienie modelu</span><span class="sxs-lookup"><span data-stu-id="26bf2-445">Understand the model</span></span>
> * <span data-ttu-id="26bf2-446">Ponownie Użyj wstępnie nauczonego modelu</span><span class="sxs-lookup"><span data-stu-id="26bf2-446">Reuse the pre-trained model</span></span>
> * <span data-ttu-id="26bf2-447">Wykrywanie obiektów z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="26bf2-447">Detect objects with a loaded model</span></span>

<span data-ttu-id="26bf2-448">Zapoznaj się z przykładem repozytorium Machine Learning Samples w witrynie GitHub, aby poznać próbkę wykrywania rozwiniętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="26bf2-448">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="26bf2-449">dotnet/machinelearning — przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="26bf2-449">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)
