---
title: 'Samouczek: automatyczna Inspekcja wizualizacji przy użyciu uczenia przenoszenia'
description: W tym samouczku pokazano, jak używać uczenia przeniesienia do uczenia modelu uczenia głębokiego TensorFlow w ML.NET przy użyciu interfejsu API wykrywania obrazów do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niepękniętych.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/25/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b8aec80134188811eb80ad1394e5a64d65a3c6f0
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961988"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="0aacf-103">Samouczek: automatyczne Inspekcja wizualizacji przy użyciu uczenia transferowego za pomocą interfejsu API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="0aacf-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="0aacf-104">Dowiedz się, jak uczenie niestandardowego modelu uczenia głębokiego przy użyciu uczenia transferu, przedTensorFlowego modelu i interfejsu API klasyfikacji obrazów ML.NET do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niepękniętych.</span><span class="sxs-lookup"><span data-stu-id="0aacf-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

> [!NOTE]
> <span data-ttu-id="0aacf-105">W tym samouczku jest stosowana wersja zapoznawcza interfejsu API klasyfikacji obrazów ML.NET.</span><span class="sxs-lookup"><span data-stu-id="0aacf-105">This tutorial uses a preview version of the ML.NET Image Classification API.</span></span>

<span data-ttu-id="0aacf-106">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0aacf-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0aacf-107">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="0aacf-107">Understand the problem</span></span>
> - <span data-ttu-id="0aacf-108">Dowiedz się więcej o interfejsie API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="0aacf-108">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="0aacf-109">Omówienie modelu przedniego</span><span class="sxs-lookup"><span data-stu-id="0aacf-109">Understand the pretrained model</span></span>
> - <span data-ttu-id="0aacf-110">Korzystanie z uczenia transferowego do uczenia niestandardowego modelu klasyfikacji obrazów TensorFlow</span><span class="sxs-lookup"><span data-stu-id="0aacf-110">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="0aacf-111">Klasyfikowanie obrazów przy użyciu modelu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="0aacf-111">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0aacf-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0aacf-112">Prerequisites</span></span>

- <span data-ttu-id="0aacf-113">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0aacf-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="0aacf-114">Omówienie przykładu szkoleniowego dotyczącego przenoszenia klasyfikacji obrazów</span><span class="sxs-lookup"><span data-stu-id="0aacf-114">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="0aacf-115">Ten przykład to aplikacja C# konsolowa platformy .NET Core, która klasyfikuje obrazy przy użyciu preszkolenego modelu TensorFlow uczenia głębokiego.</span><span class="sxs-lookup"><span data-stu-id="0aacf-115">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="0aacf-116">Kod dla tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="0aacf-116">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="0aacf-117">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="0aacf-117">Understand the problem</span></span>

<span data-ttu-id="0aacf-118">Klasyfikacja obrazu jest problemem z obsługą komputera.</span><span class="sxs-lookup"><span data-stu-id="0aacf-118">Image classification is a computer vision problem.</span></span> <span data-ttu-id="0aacf-119">Klasyfikacja obrazu pobiera obraz jako dane wejściowe i klasyfikuje go do wskazanej klasy.</span><span class="sxs-lookup"><span data-stu-id="0aacf-119">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="0aacf-120">Niektóre scenariusze, w których klasyfikacja obrazów jest przydatna:</span><span class="sxs-lookup"><span data-stu-id="0aacf-120">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="0aacf-121">Rozpoznawanie twarzy</span><span class="sxs-lookup"><span data-stu-id="0aacf-121">Facial recognition</span></span>
- <span data-ttu-id="0aacf-122">Wykrywanie rozpoznawania emocji</span><span class="sxs-lookup"><span data-stu-id="0aacf-122">Emotion detection</span></span>
- <span data-ttu-id="0aacf-123">Diagnoza medyczna</span><span class="sxs-lookup"><span data-stu-id="0aacf-123">Medical diagnosis</span></span>
- <span data-ttu-id="0aacf-124">Wykrywanie punktu orientacyjnego</span><span class="sxs-lookup"><span data-stu-id="0aacf-124">Landmark detection</span></span>

<span data-ttu-id="0aacf-125">W tym samouczku przedstawiono niestandardowy model klasyfikacji obrazów służący do przeprowadzania zautomatyzowanej inspekcji wizualizacji w celu identyfikowania struktur, które są uszkodzone przez pęknięcia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-125">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="0aacf-126">Interfejs API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="0aacf-126">ML.NET Image Classification API</span></span>

<span data-ttu-id="0aacf-127">ML.NET zapewnia różne sposoby wykonywania klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-127">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="0aacf-128">W tym samouczku zastosowana jest nauka transferu przy użyciu interfejsu API klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-128">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="0aacf-129">Interfejs API klasyfikacji obrazów korzysta z [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), biblioteki niskiego poziomu, która zapewnia C# powiązania z interfejsem API C++ TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="0aacf-129">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="0aacf-130">Co to jest uczenie transferu?</span><span class="sxs-lookup"><span data-stu-id="0aacf-130">What is transfer learning?</span></span>

<span data-ttu-id="0aacf-131">Nauka przenoszenia dotyczy wiedzy uzyskanej w wyniku rozwiązywania jednego problemu z innym powiązanym problemem.</span><span class="sxs-lookup"><span data-stu-id="0aacf-131">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="0aacf-132">Uczenie modelu uczenia głębokiego od podstaw wymaga ustawienia kilku parametrów, dużej ilości danych szkoleniowych z etykietą i ogromnej ilości zasobów obliczeniowych (setki godzin procesora GPU).</span><span class="sxs-lookup"><span data-stu-id="0aacf-132">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="0aacf-133">Przy użyciu wstępnie przemieszczonego modelu wraz z uczeniem transferu można przystąpić do tworzenia skrótów do procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-133">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span> 

## <a name="training-process"></a><span data-ttu-id="0aacf-134">Proces uczenia</span><span class="sxs-lookup"><span data-stu-id="0aacf-134">Training process</span></span>

<span data-ttu-id="0aacf-135">Interfejs API klasyfikacji obrazów uruchamia proces szkolenia, ładując wstępnie przeszkolony model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="0aacf-135">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="0aacf-136">Proces uczenia składa się z dwóch kroków:</span><span class="sxs-lookup"><span data-stu-id="0aacf-136">The training process consists of two steps:</span></span>

1. <span data-ttu-id="0aacf-137">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="0aacf-137">Bottleneck phase</span></span>
2. <span data-ttu-id="0aacf-138">Faza szkoleniowa</span><span class="sxs-lookup"><span data-stu-id="0aacf-138">Training phase</span></span>

![Kroki szkoleniowe](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="0aacf-140">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="0aacf-140">Bottleneck phase</span></span>

<span data-ttu-id="0aacf-141">W fazie wąskiego gardła zestaw obrazów szkoleniowych jest ładowany, a wartości pikseli są używane jako dane wejściowe lub funkcje dla zamrożonych warstw modelu przedniego.</span><span class="sxs-lookup"><span data-stu-id="0aacf-141">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="0aacf-142">Zablokowane warstwy obejmują wszystkie warstwy w sieci neuronowych do przedstawionej warstwy, nieformalnie znanej jako warstwa wąskiego gardła.</span><span class="sxs-lookup"><span data-stu-id="0aacf-142">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="0aacf-143">Te warstwy są określane jako zamrożone, ponieważ na tych warstwach nie ma żadnego szkolenia i operacje są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="0aacf-143">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="0aacf-144">Jest to zamrożone warstwy, w których są obliczane wzorce niższego poziomu, które pomagają w odróżnieniu od różnych klas.</span><span class="sxs-lookup"><span data-stu-id="0aacf-144">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="0aacf-145">Im większa liczba warstw, tym większa intensywnie jest ten krok.</span><span class="sxs-lookup"><span data-stu-id="0aacf-145">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="0aacf-146">Na szczęście, ponieważ jest to jednorazowe obliczenie, wyniki mogą być buforowane i używane w późniejszym czasie podczas eksperymentowania z innymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="0aacf-146">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="0aacf-147">Faza szkoleniowa</span><span class="sxs-lookup"><span data-stu-id="0aacf-147">Training phase</span></span>

<span data-ttu-id="0aacf-148">Gdy obliczane są wartości wyjściowe z fazy wąskiego gardła, są one używane jako dane wejściowe do ponownego uczenia ostatniej warstwy modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-148">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="0aacf-149">Ten proces jest iteracyjny i uruchamiany przez liczbę razy określony przez parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-149">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="0aacf-150">W każdym przebiegu są oceniane straty i dokładność.</span><span class="sxs-lookup"><span data-stu-id="0aacf-150">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="0aacf-151">Następnie wprowadzane są odpowiednie zmiany w celu ulepszenia modelu, aby zminimalizować stratę i zmaksymalizować dokładność.</span><span class="sxs-lookup"><span data-stu-id="0aacf-151">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="0aacf-152">Po zakończeniu szkolenia dwa formaty modeli są wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="0aacf-152">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="0aacf-153">Jednym z nich jest wersja `.pb` modelu, a druga to `.zip` ML.NET zserializowaną wersję modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-153">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="0aacf-154">W przypadku pracy w środowiskach obsługiwanych przez ML.NET zaleca się użycie `.zip` wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-154">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="0aacf-155">Jednak w środowiskach, w których ML.NET nie jest obsługiwana, dostępna jest opcja korzystania z wersji `.pb`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-155">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="0aacf-156">Omówienie modelu przedniego</span><span class="sxs-lookup"><span data-stu-id="0aacf-156">Understand the pretrained model</span></span>

<span data-ttu-id="0aacf-157">Wstępnie przemieszczony model używany w tym samouczku to 101-warstwowy model sieci resztkowej (ResNet) w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="0aacf-157">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="0aacf-158">Oryginalny model jest przeszkolony do klasyfikowania obrazów do tysięcy kategorii.</span><span class="sxs-lookup"><span data-stu-id="0aacf-158">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="0aacf-159">Model przyjmuje jako dane wejściowe obraz o rozmiarze 224 x 224 i wyświetla prawdopodobieństwa klasy dla każdej klasy, w której jest szkolony.</span><span class="sxs-lookup"><span data-stu-id="0aacf-159">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="0aacf-160">Część tego modelu służy do uczenia nowego modelu przy użyciu obrazów niestandardowych w celu wprowadzania prognoz między dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="0aacf-160">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span> 

## <a name="create-console-application"></a><span data-ttu-id="0aacf-161">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="0aacf-161">Create console application</span></span>

<span data-ttu-id="0aacf-162">Teraz, gdy znasz już ogólną wiedzę o uczeniu przenoszenia i interfejsie API klasyfikacji obrazów, jest to czas na skompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-162">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="0aacf-163">Utwórz  **C# aplikację konsolową .NET Core** o nazwie "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="0aacf-163">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="0aacf-164">Zainstaluj pakiet NuGet **Microsoft.ml 1.4.0-preview2** :</span><span class="sxs-lookup"><span data-stu-id="0aacf-164">Install the **Microsoft.ML 1.4.0-preview2** NuGet Package:</span></span>
    1. <span data-ttu-id="0aacf-165">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0aacf-165">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="0aacf-166">Wybierz pozycję "nuget.org" jako źródło pakietu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-166">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="0aacf-167">Wybierz kartę **przeglądanie** .</span><span class="sxs-lookup"><span data-stu-id="0aacf-167">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="0aacf-168">Zaznacz pole wyboru **Uwzględnij wersję wstępną** .</span><span class="sxs-lookup"><span data-stu-id="0aacf-168">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="0aacf-169">Wyszukaj **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="0aacf-169">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="0aacf-170">Wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="0aacf-170">Select the **Install** button.</span></span>
    1. <span data-ttu-id="0aacf-171">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-171">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="0aacf-172">Powtórz te kroki dla **Microsoft. ml. DNN 0.16.0-preview2** i **Microsoft. ml. ImageAnalytics 1.4.0-preview2**.</span><span class="sxs-lookup"><span data-stu-id="0aacf-172">Repeat these steps for **Microsoft.ML.Dnn 0.16.0-preview2** and **Microsoft.ML.ImageAnalytics 1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0aacf-173">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="0aacf-173">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="0aacf-174">Zestawy danych dla tego samouczka pochodzą z Maguire, wytłoków; Dorafshan, Sattar; i Thomas, Robert J., "SDNET2018: zestaw danych obrazu dla konkretnych pęknięć dla aplikacji Machine Learning" (2018).</span><span class="sxs-lookup"><span data-stu-id="0aacf-174">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="0aacf-175">Przeglądaj wszystkie zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="0aacf-175">Browse all Datasets.</span></span> <span data-ttu-id="0aacf-176">Papier 48.</span><span class="sxs-lookup"><span data-stu-id="0aacf-176">Paper 48.</span></span> <span data-ttu-id="0aacf-177">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="0aacf-177">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="0aacf-178">SDNET2018 jest zestawem danych obrazu zawierającym adnotacje dla popękanych i niepękniętych struktur (talie mostków, ściany i Pavement).</span><span class="sxs-lookup"><span data-stu-id="0aacf-178">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span> 

![Przykłady dla talii mostka SDNET2018 DataSet](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="0aacf-180">Dane są zorganizowane w trzech podkatalogach:</span><span class="sxs-lookup"><span data-stu-id="0aacf-180">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="0aacf-181">D zawiera obrazy talii mostków</span><span class="sxs-lookup"><span data-stu-id="0aacf-181">D contains bridge deck images</span></span>
- <span data-ttu-id="0aacf-182">P zawiera obrazy Pavement</span><span class="sxs-lookup"><span data-stu-id="0aacf-182">P contains pavement images</span></span>
- <span data-ttu-id="0aacf-183">W zawiera obrazy ściany</span><span class="sxs-lookup"><span data-stu-id="0aacf-183">W contains wall images</span></span>

<span data-ttu-id="0aacf-184">Każdy z tych podkatalogów zawiera dwa dodatkowe podkatalogi z prefiksem:</span><span class="sxs-lookup"><span data-stu-id="0aacf-184">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="0aacf-185">C jest prefiksem używanym na potrzeby powierzchni pękniętych</span><span class="sxs-lookup"><span data-stu-id="0aacf-185">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="0aacf-186">U to prefiks używany dla niepękanych powierzchni</span><span class="sxs-lookup"><span data-stu-id="0aacf-186">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="0aacf-187">W tym samouczku używane są tylko obrazy talii mostków.</span><span class="sxs-lookup"><span data-stu-id="0aacf-187">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="0aacf-188">Pobierz [zestaw danych](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="0aacf-188">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="0aacf-189">Utwórz katalog o nazwie "Assets" w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="0aacf-189">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="0aacf-190">Skopiuj podkatalogi *CD* i *ud* z ostatnio odpakowanego katalogu do katalogu *zasobów* .</span><span class="sxs-lookup"><span data-stu-id="0aacf-190">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="0aacf-191">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="0aacf-191">Create input and output classes</span></span>

1. <span data-ttu-id="0aacf-192">Otwórz plik *program.cs* i Zastąp istniejące instrukcje `using` w górnej części pliku, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0aacf-192">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="0aacf-193">Poniżej klasy `Program` w *program.cs*Utwórz klasę o nazwie `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-193">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="0aacf-194">Ta klasa jest używana do reprezentowania początkowo załadowanych danych.</span><span class="sxs-lookup"><span data-stu-id="0aacf-194">This class is used to represent the initially loaded data.</span></span> 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    <span data-ttu-id="0aacf-195">`ImageData` zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="0aacf-195">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="0aacf-196">`ImagePath` to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-196">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="0aacf-197">`Label` to kategoria, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-197">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="0aacf-198">Jest to wartość do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-198">This is the value to predict.</span></span>

1. <span data-ttu-id="0aacf-199">Tworzenie klas danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="0aacf-199">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="0aacf-200">Poniżej klasy `ImageData` Zdefiniuj schemat danych wejściowych w nowej klasie o nazwie `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-200">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        <span data-ttu-id="0aacf-201">`ModelInput` zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="0aacf-201">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="0aacf-202">`ImagePath` to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-202">`ImagePath` is the fully qualified path where the image is stored.</span></span> 
        - <span data-ttu-id="0aacf-203">`Label` to kategoria, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-203">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="0aacf-204">Jest to wartość do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-204">This is the value to predict.</span></span>
        - <span data-ttu-id="0aacf-205">`Image` to `byte[]` reprezentacja obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-205">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="0aacf-206">Model oczekuje, że dane obrazu mają być tego typu dla szkolenia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-206">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="0aacf-207">`LabelAsKey` jest liczbową reprezentacją `Label`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-207">`LabelAsKey` is the numerical representation of the `Label`.</span></span> 

        <span data-ttu-id="0aacf-208">Tylko `Image` i `LabelAsKey` są używane do uczenia modelu i podejmowania prognoz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-208">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="0aacf-209">Właściwości `ImagePath` i `Label` są przechowywane dla wygody dostępu do oryginalnej nazwy i kategorii pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-209">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="0aacf-210">Następnie, poniżej klasy `ModelInput`, zdefiniuj schemat danych wyjściowych w nowej klasie o nazwie `ModelOutput`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-210">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span> 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        <span data-ttu-id="0aacf-211">`ModelOutput` zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="0aacf-211">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="0aacf-212">`ImagePath` to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-212">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="0aacf-213">`Label` jest oryginalną kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-213">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="0aacf-214">Jest to wartość do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-214">This is the value to predict.</span></span> 
        - <span data-ttu-id="0aacf-215">`PredictedLabel` jest wartością przewidywaną przez model.</span><span class="sxs-lookup"><span data-stu-id="0aacf-215">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="0aacf-216">Podobnie jak w przypadku `ModelInput`, tylko `PredictedLabel` jest wymagany do przeprowadzenia prognozowania, ponieważ zawiera prognozę dokonaną przez model.</span><span class="sxs-lookup"><span data-stu-id="0aacf-216">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="0aacf-217">Właściwości `ImagePath` i `Label` są zachowywane w celu ułatwienia dostępu do oryginalnej nazwy i kategorii pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-217">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="0aacf-218">Zdefiniuj ścieżki i zainicjuj zmienne</span><span class="sxs-lookup"><span data-stu-id="0aacf-218">Define paths and initialize variables</span></span>

1. <span data-ttu-id="0aacf-219">Wewnątrz metody `Main` Zdefiniuj lokalizację zasobów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-219">Inside the `Main` method, define the location of your assets.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L16)]

1. <span data-ttu-id="0aacf-220">Następnie zainicjuj zmienną `mlContext` z nowym wystąpieniem [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="0aacf-220">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

<span data-ttu-id="0aacf-221">Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie MLContext tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-221">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="0aacf-222">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0aacf-222">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="0aacf-223">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="0aacf-223">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="0aacf-224">Metoda tworzenia narzędzia do ładowania danych</span><span class="sxs-lookup"><span data-stu-id="0aacf-224">Create data loading utility method</span></span>

<span data-ttu-id="0aacf-225">Obrazy są przechowywane w dwóch podkatalogach.</span><span class="sxs-lookup"><span data-stu-id="0aacf-225">The images are stored in two subdirectories.</span></span> <span data-ttu-id="0aacf-226">Przed załadowaniem danych należy je sformatować w postaci listy obiektów `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-226">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="0aacf-227">W tym celu Utwórz metodę `LoadImagesFromDirectory` poniżej metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-227">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="0aacf-228">Wewnątrz `LoadImagesDirectory` Dodaj następujący kod, aby uzyskać wszystkie ścieżki plików z podkatalogów:</span><span class="sxs-lookup"><span data-stu-id="0aacf-228">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. <span data-ttu-id="0aacf-229">Następnie wykonaj iterację poszczególnych plików przy użyciu instrukcji `foreach`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-229">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="0aacf-230">W instrukcji `foreach` Sprawdź, czy rozszerzenia plików są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0aacf-230">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="0aacf-231">Interfejs API klasyfikacji obrazów obsługuje formaty JPEG i PNG.</span><span class="sxs-lookup"><span data-stu-id="0aacf-231">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. <span data-ttu-id="0aacf-232">Następnie Pobierz etykietę dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="0aacf-232">Then, get the label for the file.</span></span> <span data-ttu-id="0aacf-233">Jeśli parametr `useFolderNameAsLabel` ma wartość `true`, katalog nadrzędny, w którym zapisano plik, jest używany jako etykieta.</span><span class="sxs-lookup"><span data-stu-id="0aacf-233">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="0aacf-234">W przeciwnym razie oczekuje, że etykieta będzie prefiksem nazwy pliku lub samej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="0aacf-234">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. <span data-ttu-id="0aacf-235">Na koniec Utwórz nowe wystąpienie `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-235">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a><span data-ttu-id="0aacf-236">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="0aacf-236">Prepare the data</span></span>

1. <span data-ttu-id="0aacf-237">Z powrotem w metodzie `Main` Użyj metody `LoadFromDirectory`, aby uzyskać listę obrazów używanych do uczenia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-237">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. <span data-ttu-id="0aacf-238">Następnie załaduj obrazy do [`IDataView`](xref:Microsoft.ML.IDataView) przy użyciu metody [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="0aacf-238">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. <span data-ttu-id="0aacf-239">Dane są ładowane w kolejności, w której zostały odczytane z katalogów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-239">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="0aacf-240">Aby zrównoważyć dane, należy je losowo użyć metody [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .</span><span class="sxs-lookup"><span data-stu-id="0aacf-240">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. <span data-ttu-id="0aacf-241">Modele uczenia maszynowego oczekują danych wejściowych w formacie liczbowym.</span><span class="sxs-lookup"><span data-stu-id="0aacf-241">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="0aacf-242">W związku z tym, należy wykonać pewne czynności wstępne dotyczące danych przed szkoleniem.</span><span class="sxs-lookup"><span data-stu-id="0aacf-242">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="0aacf-243">Utwórz [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) , które składają się z [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) i [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transformacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-243">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transforms.</span></span> <span data-ttu-id="0aacf-244">`MapValueToKey` Transform przyjmuje wartość kategorii w kolumnie `Label`, konwertuje ją na wartość liczbową `KeyType` i zapisuje ją w nowej kolumnie o nazwie `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-244">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="0aacf-245">`LoadImages` pobiera wartości z kolumny `ImagePath` wraz z parametrem `imageFolder` w celu załadowania obrazów do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-245">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span> <span data-ttu-id="0aacf-246">Ustawienie `useImageType` na `false` powoduje konwersję obrazów na `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-246">Setting the `useImageType` to `false` converts the images into a `byte[]`.</span></span> 

    [!code-csharp [DefinePreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L26-L33)]

1. <span data-ttu-id="0aacf-247">Użyj metody [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) , aby zastosować dane do `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) po którym następuje Metoda [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) , która zwraca [`IDataView`](xref:Microsoft.ML.IDataView) zawierający wstępnie przetworzone dane.</span><span class="sxs-lookup"><span data-stu-id="0aacf-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="0aacf-248">Aby szkolić model, ważne jest posiadanie zestawu danych szkoleniowych oraz zestawu danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="0aacf-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="0aacf-249">Model jest szkolony na zestawie szkoleniowym.</span><span class="sxs-lookup"><span data-stu-id="0aacf-249">The model is trained on the training set.</span></span> <span data-ttu-id="0aacf-250">Jak również przewidywania dotyczące niewidocznych danych są mierzone przez wydajność względem zestawu walidacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="0aacf-251">W oparciu o wyniki tej wydajności model dostosowuje się do tego, co pobrało w wysiłku, aby zwiększyć.</span><span class="sxs-lookup"><span data-stu-id="0aacf-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="0aacf-252">Zestaw walidacji może pochodzić z dzielenia oryginalnego zestawu danych lub z innego źródła, które zostało już przeznaczone do tego celu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="0aacf-253">W tym przypadku wstępnie przetworzony zestaw danych jest podzielony na szkolenia, walidację i zestawy testów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="0aacf-254">Powyższy przykład kodu wykonuje dwa podziały.</span><span class="sxs-lookup"><span data-stu-id="0aacf-254">The code sample above performs two splits.</span></span> <span data-ttu-id="0aacf-255">Po pierwsze przetworzone dane są podzielone i 70% jest używane do uczenia, podczas gdy pozostały 30% jest używany do walidacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="0aacf-256">Następnie zestaw walidacji 30% jest podzielona na weryfikację i zestawy testów, gdzie 90% jest używany do walidacji, a 10% jest używany do testowania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span> 

    <span data-ttu-id="0aacf-257">Aby myśleć o przeznaczeniu tych partycji danych, należy wziąć pod uwagę egzamin.</span><span class="sxs-lookup"><span data-stu-id="0aacf-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="0aacf-258">Podczas badania na egzaminie możesz przejrzeć notatki, książki lub inne zasoby, aby uzyskać opanujesz na temat koncepcji, które znajdują się na egzaminie.</span><span class="sxs-lookup"><span data-stu-id="0aacf-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="0aacf-259">Jest to zestaw pociągów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-259">This is what the train set is for.</span></span> <span data-ttu-id="0aacf-260">Następnie możesz skorzystać z egzaminu makiety, aby zweryfikować swoją wiedzę.</span><span class="sxs-lookup"><span data-stu-id="0aacf-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="0aacf-261">Jest to miejsce, w którym zestaw walidacji jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="0aacf-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="0aacf-262">Chcesz sprawdzić, czy masz dobre opanujesz koncepcji przed rozpoczęciem rzeczywistego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="0aacf-263">W oparciu o te wyniki należy zwrócić uwagę na to, co się stało lub które nie jest dobrze zrozumiałe i uwzględnić zmiany podczas przeglądania dla rzeczywistego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="0aacf-264">Na koniec przejęcie egzaminu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-264">Finally, you take the exam.</span></span> <span data-ttu-id="0aacf-265">Jest to zestaw testów używany przez.</span><span class="sxs-lookup"><span data-stu-id="0aacf-265">This is what the test set is used for.</span></span> <span data-ttu-id="0aacf-266">Nie widzisz już pytań dotyczących egzaminu i teraz korzystamy z tego, co uczysz się od szkoleń i weryfikacji, aby od razu zastosować swoją wiedzę do tego zadania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span> 

1. <span data-ttu-id="0aacf-267">Przypisz partycje ich odpowiednie wartości dla danych dotyczących pouczenia, sprawdzania poprawności i testowania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="0aacf-268">Definiowanie potoku szkoleniowego</span><span class="sxs-lookup"><span data-stu-id="0aacf-268">Define the training pipeline</span></span>

<span data-ttu-id="0aacf-269">Szkolenia modeli składają się z kilku kroków.</span><span class="sxs-lookup"><span data-stu-id="0aacf-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="0aacf-270">Najpierw interfejs API klasyfikacji obrazu jest używany do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="0aacf-271">Następnie kodowane etykiety w kolumnie `PredictedLabel` są konwertowane z powrotem na ich oryginalną wartość kategorii przy użyciu transformacji `MapKeyToValue`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span> 

1. <span data-ttu-id="0aacf-272">Zdefiniuj potok [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) szkolenia, który składa się z `mapLabelEstimator` i `ImageClassification` transformacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-272">Define the training [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline that consists of both the `mapLabelEstimator` and the `ImageClassification` transforms.</span></span>

    [!code-csharp [DefineTrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L58)]    

    <span data-ttu-id="0aacf-273">`ImageClassification` szacowania wykonuje kilka parametrów:</span><span class="sxs-lookup"><span data-stu-id="0aacf-273">The `ImageClassification` estimator takes in several parameters:</span></span>

    - <span data-ttu-id="0aacf-274">`featuresColumnName` to kolumna, która jest używana jako dane wejściowe dla modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-274">`featuresColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="0aacf-275">`labelColumnName` to kolumna, dla której ma zostać przewidywalna wartość.</span><span class="sxs-lookup"><span data-stu-id="0aacf-275">`labelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="0aacf-276">`arch` definiuje, które ze współmieszczonych architektur modelu są używane.</span><span class="sxs-lookup"><span data-stu-id="0aacf-276">`arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="0aacf-277">W tym samouczku jest stosowana 101-warstwowa odmiana modelu ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="0aacf-277">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="0aacf-278">`epoch` określa maksymalną liczbę iteracji w całym zestawie danych w ramach procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-278">`epoch` specifies the maximum number of iterations over the entire dataset throughout the training process.</span></span> <span data-ttu-id="0aacf-279">Im większa liczba, tym dłużej model pociąga za i potencjalnie lepszy model, który jest produkowany.</span><span class="sxs-lookup"><span data-stu-id="0aacf-279">The higher the number, the longer the model trains for and potentially the better model that is produced.</span></span>
    - <span data-ttu-id="0aacf-280">`batchSize` to liczba próbek do użycia w czasie na potrzeby szkoleń.</span><span class="sxs-lookup"><span data-stu-id="0aacf-280">`batchSize` is the number of samples to use at a time for training.</span></span> <span data-ttu-id="0aacf-281">Podczas jednej epoki do uczenia i aktualizacji modelu są używane wiele partii, które są równe batchSize.</span><span class="sxs-lookup"><span data-stu-id="0aacf-281">During one epoch, multiple batches equal to the batchSize are used to train and update the model.</span></span> <span data-ttu-id="0aacf-282">Im niższa wartość, tym mniejsza ilość pamięci wymaganej podczas przetwarzania każdej partii.</span><span class="sxs-lookup"><span data-stu-id="0aacf-282">The lower the number, the less memory required when each batch is processed.</span></span>
    - <span data-ttu-id="0aacf-283">`testOnTrainSet` nakazuje modelowi pomiar wydajności względem zestawu szkoleniowego, gdy nie ma zestawu walidacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-283">`testOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="0aacf-284">`metricsCallback` wiąże funkcję w celu śledzenia postępu podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-284">`metricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="0aacf-285">`validationSet` jest [`IDataView`](xref:Microsoft.ML.IDataView) zawierający dane walidacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-285">`validationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="0aacf-286">`reuseTrainSetBottleneckCachedValues` informuje model, czy należy używać buforowanych wartości z fazy wąskich gardeł w kolejnych uruchomieniach.</span><span class="sxs-lookup"><span data-stu-id="0aacf-286">`reuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="0aacf-287">Faza wąskich gardeł to jednokrotne obliczenie przekazujące, które jest intensywnie czasochłonne podczas pierwszego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-287">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="0aacf-288">Jeśli dane szkoleniowe nie zmieniają się i chcesz eksperymentować przy użyciu innej liczby epok lub rozmiaru partii, użycie pamięci podręcznej znacznie zmniejsza ilość czasu wymaganego do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-288">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="0aacf-289">`reuseValidationSetBottleneckCachedValues` jest podobna do `reuseTrainSetBottleneckCachedValues` tylko wtedy, gdy jest to dla zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-289">`reuseValidationSetBottleneckCachedValues` is similar to `reuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="0aacf-290">`disableEarlyStopping` informuje ImageClassification szacowania o tym, czy ma być stosowana wczesna strategia zatrzymywania.</span><span class="sxs-lookup"><span data-stu-id="0aacf-290">`disableEarlyStopping` tells the ImageClassification estimator whether to employ an early stopping strategy.</span></span> <span data-ttu-id="0aacf-291">Ponieważ model wyszukuje optymalne wartości, które ułatwiają precyzyjne przewidywania podczas szkolenia, wydajność może się zwiększyć lub zmniejszyć.</span><span class="sxs-lookup"><span data-stu-id="0aacf-291">As the model searches for the optimal values that will help it make accurate predictions during training, performance may increase or decrease.</span></span> <span data-ttu-id="0aacf-292">Ostatecznie, jeśli model osiągnie ostatnią epokę, może się okazać, że wzorce, które uczyją się od szkoleń, są nieoptymalne.</span><span class="sxs-lookup"><span data-stu-id="0aacf-292">Ultimately, if the model reaches the last epoch, it may be the case that the patterns it learned from training are suboptimal.</span></span> <span data-ttu-id="0aacf-293">Wczesne zatrzymanie monitorów pozwala zmniejszyć wydajność i zatrzymać proces szkolenia w celu zachowania optymalnej wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-293">Early stopping monitors training for these drops in performance and stops the training process in an effort to preserve an optimal version of the model.</span></span>

1. <span data-ttu-id="0aacf-294">Użyj metody [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) , aby nauczyć model.</span><span class="sxs-lookup"><span data-stu-id="0aacf-294">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a><span data-ttu-id="0aacf-295">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="0aacf-295">Use the model</span></span>

<span data-ttu-id="0aacf-296">Teraz, gdy korzystasz z modelu, możesz go użyć do klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-296">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="0aacf-297">Poniżej metody `Main` Utwórz nową metodę narzędzia o nazwie `OutputPrediction`, aby wyświetlić informacje o prognozie w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-297">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a><span data-ttu-id="0aacf-298">Klasyfikowanie pojedynczego obrazu</span><span class="sxs-lookup"><span data-stu-id="0aacf-298">Classify a single image</span></span>

1. <span data-ttu-id="0aacf-299">Dodaj nową metodę o nazwie `ClassifySingleImage` poniżej metody `Main`, aby utworzyć i wyprowadzić prognozę pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-299">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="0aacf-300">Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wewnątrz metody `ClassifySingleImage`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-300">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="0aacf-301">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który pozwala na przekazywanie danych, a następnie wykonywanie prognozowania na jednym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-301">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. <span data-ttu-id="0aacf-302">Aby uzyskać dostęp do jednego wystąpienia `ModelInput`, przekonwertuj `data` [`IDataView`](xref:Microsoft.ML.IDataView) na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) przy użyciu metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) , a następnie Pobierz pierwsze obserwacje.</span><span class="sxs-lookup"><span data-stu-id="0aacf-302">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span> 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="0aacf-303">Użyj metody [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) do klasyfikowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-303">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="0aacf-304">Wyprowadzanie danych wyjściowych do konsoli za pomocą metody `OutputPrediction`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-304">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. <span data-ttu-id="0aacf-305">Wewnątrz metody `Main` Wywołaj `ClassifySingleImage` za pomocą zestawu testowego obrazów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-305">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a><span data-ttu-id="0aacf-306">Klasyfikowanie wielu obrazów</span><span class="sxs-lookup"><span data-stu-id="0aacf-306">Classify multiple images</span></span>

1. <span data-ttu-id="0aacf-307">Dodaj nową metodę o nazwie `ClassifyImages` poniżej metody `ClassifySingleImage`, aby wykonać i wyprowadzić wiele prognoz obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-307">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="0aacf-308">Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) zawierający przewidywania przy użyciu metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) .</span><span class="sxs-lookup"><span data-stu-id="0aacf-308">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="0aacf-309">Dodaj następujący kod w metodzie `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="0aacf-309">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. <span data-ttu-id="0aacf-310">Aby wykonać iterację prognoz, przekonwertuj [`IDataView`](xref:Microsoft.ML.IDataView) `predictionData` na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) przy użyciu metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) , a następnie Pobierz pierwsze 10 obserwacji.</span><span class="sxs-lookup"><span data-stu-id="0aacf-310">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="0aacf-311">Wykonaj iterację i wyprowadzaj oryginalne i przewidywane etykiety dla prognoz.</span><span class="sxs-lookup"><span data-stu-id="0aacf-311">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. <span data-ttu-id="0aacf-312">Na koniec w metodzie `Main` Wywołaj `ClassifyImages` przy użyciu zestawu testów obrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-312">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a><span data-ttu-id="0aacf-313">Uruchom aplikację</span><span class="sxs-lookup"><span data-stu-id="0aacf-313">Run the application</span></span>

<span data-ttu-id="0aacf-314">Uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="0aacf-314">Run your console app.</span></span> <span data-ttu-id="0aacf-315">Dane wyjściowe powinny być podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="0aacf-315">The output should be similar to that below.</span></span> <span data-ttu-id="0aacf-316">Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="0aacf-316">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="0aacf-317">W przypadku zwięzłości dane wyjściowe zostały zagęszczone.</span><span class="sxs-lookup"><span data-stu-id="0aacf-317">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="0aacf-318">**Faza wąskiego gardła**</span><span class="sxs-lookup"><span data-stu-id="0aacf-318">**Bottleneck phase**</span></span>

<span data-ttu-id="0aacf-319">Żadna wartość nie jest drukowana dla nazwy obrazu, ponieważ obrazy są ładowane jako `byte[]` w związku z tym nie istnieje nazwa obrazu do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="0aacf-319">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

<span data-ttu-id="0aacf-320">**Faza szkoleniowa**</span><span class="sxs-lookup"><span data-stu-id="0aacf-320">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="0aacf-321">**Klasyfikowanie obrazów wyjściowych**</span><span class="sxs-lookup"><span data-stu-id="0aacf-321">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="0aacf-322">Po Przeprowadź inspekcję obrazu *-220. jpg* można zobaczyć, że w rzeczywistości nie jest to pęknięcie.</span><span class="sxs-lookup"><span data-stu-id="0aacf-322">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span> 

![Obraz zestawu danych SDNET2018 służący do przewidywania](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="0aacf-324">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="0aacf-324">Congratulations!</span></span> <span data-ttu-id="0aacf-325">Pomyślnie skompilowano model uczenia głębokiego na potrzeby klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="0aacf-325">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="0aacf-326">Ulepszanie modelu</span><span class="sxs-lookup"><span data-stu-id="0aacf-326">Improve the model</span></span>

<span data-ttu-id="0aacf-327">Jeśli wyniki Twojego modelu nie są zadowalające, możesz spróbować zwiększyć jego wydajność, wykonując kilka następujących metod:</span><span class="sxs-lookup"><span data-stu-id="0aacf-327">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="0aacf-328">**Więcej danych**: więcej przykładów, z których uzyskuje się model, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="0aacf-328">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="0aacf-329">Pobierz pełny [zestaw danych SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) i użyj go do uczenia się.</span><span class="sxs-lookup"><span data-stu-id="0aacf-329">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span> 
- <span data-ttu-id="0aacf-330">**Rozszerzanie danych**: typową techniką dodawania odmiany do danych jest rozszerzanie danych przez pobranie obrazu i zastosowanie różnych transformacji (Obróć, przerzuć, Shift, Kadruj).</span><span class="sxs-lookup"><span data-stu-id="0aacf-330">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="0aacf-331">Spowoduje to dodanie bardziej zróżnicowanych przykładów dla modelu, z których można się uczyć.</span><span class="sxs-lookup"><span data-stu-id="0aacf-331">This adds more varied examples for the model to learn from.</span></span> 
- <span data-ttu-id="0aacf-332">**Uczenie się przez dłuższy czas**: im dłużej są nauczeni, tym bardziej dostrojony model.</span><span class="sxs-lookup"><span data-stu-id="0aacf-332">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="0aacf-333">Zwiększenie liczby epok może zwiększyć wydajność modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacf-333">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="0aacf-334">**Eksperymentowanie z parametrami funkcji Hyper-Parameters**: Oprócz parametrów używanych w tym samouczku, inne parametry można dostrajać w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="0aacf-334">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="0aacf-335">Zmiana stawki szkoleniowej, która określa wielkość aktualizacji dokonanych w modelu po każdej epoki, może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="0aacf-335">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="0aacf-336">**Użyj innej architektury modelu**: w zależności od tego, jak wyglądają Twoje dane, model, który najlepiej uczy się, że jego funkcje mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="0aacf-336">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="0aacf-337">Jeśli nie masz zadowalającej wydajności modelu, spróbuj zmienić architekturę.</span><span class="sxs-lookup"><span data-stu-id="0aacf-337">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0aacf-338">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="0aacf-338">Additional Resources</span></span>

- <span data-ttu-id="0aacf-339">[Uczenie głębokie a Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="0aacf-339">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0aacf-340">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0aacf-340">Next steps</span></span>

<span data-ttu-id="0aacf-341">W tym samouczku pokazano, jak utworzyć niestandardowy model uczenia głębokiego przy użyciu uczenia przeniesienia, premieszczony model klasyfikacji obrazu TensorFlow oraz interfejs API klasyfikacji obrazów ML.NET do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niesilnie.</span><span class="sxs-lookup"><span data-stu-id="0aacf-341">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="0aacf-342">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="0aacf-342">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0aacf-343">Wykrywanie obiektów</span><span class="sxs-lookup"><span data-stu-id="0aacf-343">Object Detection</span></span>](object-detection-onnx.md)
