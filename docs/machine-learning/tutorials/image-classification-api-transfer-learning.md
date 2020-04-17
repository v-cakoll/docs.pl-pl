---
title: 'Samouczek: Automatyczna kontrola wzrokowa przy użyciu uczenia się transferu'
description: W tym samouczku pokazano, jak używać uczenia transferu do uczenia modelu uczenia głębokiego TensorFlow w ML.NET przy użyciu interfejsu API wykrywania obrazu do klasyfikowania obrazów powierzchni betonowych jako pękniętych lub nie pękniętych.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a050d7673f7ef00cf11d959d04e709222cb2be8f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607561"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="fcb33-103">Samouczek: Zautomatyzowana kontrola wzrokowa za pomocą uczenia się transferu za pomocą interfejsu API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="fcb33-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="fcb33-104">Dowiedz się, jak szkolić niestandardowy model uczenia głębokiego przy użyciu funkcji uczenia transferowego, wstępnie przeszkolonego modelu TensorFlow i interfejsu API klasyfikacji obrazów ML.NET, aby klasyfikować obrazy powierzchni betonowych jako popękane lub nieskładkowane.</span><span class="sxs-lookup"><span data-stu-id="fcb33-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="fcb33-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="fcb33-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="fcb33-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="fcb33-106">Understand the problem</span></span>
> - <span data-ttu-id="fcb33-107">Dowiedz się więcej o ML.NET interfejsie API klasyfikacji obrazów</span><span class="sxs-lookup"><span data-stu-id="fcb33-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="fcb33-108">Opis wstępnie przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="fcb33-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="fcb33-109">Szkolenie niestandardowego modelu klasyfikacji obrazów TensorFlow za pomocą funkcji transferu</span><span class="sxs-lookup"><span data-stu-id="fcb33-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="fcb33-110">Klasyfikowanie obrazów za pomocą modelu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="fcb33-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fcb33-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fcb33-111">Prerequisites</span></span>

- <span data-ttu-id="fcb33-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".</span><span class="sxs-lookup"><span data-stu-id="fcb33-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="fcb33-113">Omówienie przykładu uczenia się transferu klasyfikacji obrazów</span><span class="sxs-lookup"><span data-stu-id="fcb33-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="fcb33-114">Ten przykład jest C# .NET Core aplikacji konsoli, która klasyfikuje obrazy przy użyciu wstępnie przeszkolonego modelu uczenia głębokiego TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="fcb33-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="fcb33-115">Kod dla tego przykładu można znaleźć na [repozytorium dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="fcb33-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="fcb33-116">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="fcb33-116">Understand the problem</span></span>

<span data-ttu-id="fcb33-117">Klasyfikacja obrazów jest problemem widzenia komputerowego.</span><span class="sxs-lookup"><span data-stu-id="fcb33-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="fcb33-118">Klasyfikacja obrazów przyjmuje obraz jako dane wejściowe i kategoryzuje go do określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="fcb33-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="fcb33-119">Oto kilka scenariuszy, w których przydatna jest klasyfikacja obrazów:</span><span class="sxs-lookup"><span data-stu-id="fcb33-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="fcb33-120">Rozpoznawanie twarzy</span><span class="sxs-lookup"><span data-stu-id="fcb33-120">Facial recognition</span></span>
- <span data-ttu-id="fcb33-121">Wykrywanie emocji</span><span class="sxs-lookup"><span data-stu-id="fcb33-121">Emotion detection</span></span>
- <span data-ttu-id="fcb33-122">Diagnoza medyczna</span><span class="sxs-lookup"><span data-stu-id="fcb33-122">Medical diagnosis</span></span>
- <span data-ttu-id="fcb33-123">Wykrywanie punktów orientacyjnych</span><span class="sxs-lookup"><span data-stu-id="fcb33-123">Landmark detection</span></span>

<span data-ttu-id="fcb33-124">W tym samouczku trenuje niestandardowy model klasyfikacji obrazów do automatycznego sprawdzania pokładów mostów w celu zidentyfikowania struktur uszkodzonych przez pęknięcia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="fcb33-125">Interfejs API klasyfikacji ML.NET obrazów</span><span class="sxs-lookup"><span data-stu-id="fcb33-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="fcb33-126">ML.NET zapewnia różne sposoby wykonywania klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="fcb33-127">Ten samouczek dotyczy uczenia się transferu przy użyciu interfejsu API klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="fcb33-128">Interfejs API klasyfikacji obrazów korzysta z [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), biblioteki niskiego poziomu, która udostępnia powiązania C# dla interfejsu API TensorFlow C++.</span><span class="sxs-lookup"><span data-stu-id="fcb33-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="fcb33-129">Co to jest uczenie się transferu?</span><span class="sxs-lookup"><span data-stu-id="fcb33-129">What is transfer learning?</span></span>

<span data-ttu-id="fcb33-130">Uczenie się transferowe wykorzystuje wiedzę zdobytą w związku z rozwiązaniem jednego problemu do innego związanego z nim problemu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="fcb33-131">Szkolenie modelu uczenia głębokiego od podstaw wymaga ustawienia kilku parametrów, dużej ilości oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu).</span><span class="sxs-lookup"><span data-stu-id="fcb33-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="fcb33-132">Korzystanie z wstępnie przeszkolonego modelu wraz z uczeniem się transferu pozwala na skróty procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="fcb33-133">Proces szkolenia</span><span class="sxs-lookup"><span data-stu-id="fcb33-133">Training process</span></span>

<span data-ttu-id="fcb33-134">Interfejs API klasyfikacji obrazów rozpoczyna proces szkolenia, ładując wstępnie przeszkolony model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="fcb33-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="fcb33-135">Proces szkolenia składa się z dwóch etapów:</span><span class="sxs-lookup"><span data-stu-id="fcb33-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="fcb33-136">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="fcb33-136">Bottleneck phase</span></span>
2. <span data-ttu-id="fcb33-137">Faza szkoleniowa</span><span class="sxs-lookup"><span data-stu-id="fcb33-137">Training phase</span></span>

![Etapy szkolenia](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="fcb33-139">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="fcb33-139">Bottleneck phase</span></span>

<span data-ttu-id="fcb33-140">Podczas fazy wąskiego gardła zestaw obrazów szkoleniowych jest ładowany, a wartości pikseli są używane jako dane wejściowe lub operacje dla zablokowanych warstw wstępnie przeszkolonego modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="fcb33-141">Zamrożone warstwy zawierają wszystkie warstwy w sieci neuronowej aż do przedostatniej warstwy, nieformalnie znanej jako warstwa wąskiego gardła.</span><span class="sxs-lookup"><span data-stu-id="fcb33-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="fcb33-142">Warstwy te są określane jako zamrożone, ponieważ nie będzie odbywać się szkolenie na tych warstwach, a operacje są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="fcb33-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="fcb33-143">To w tych warstwach zamrożone, gdzie wzorce niższego poziomu, które pomagają modelu rozróżniać różne klasy są obliczane.</span><span class="sxs-lookup"><span data-stu-id="fcb33-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="fcb33-144">Im większa liczba warstw, tym bardziej intensywny pod względem obliczeniowym ten krok.</span><span class="sxs-lookup"><span data-stu-id="fcb33-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="fcb33-145">Na szczęście, ponieważ jest to obliczenie jednorazowe, wyniki mogą być buforowane i używane w późniejszych działach podczas eksperymentowania z różnymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="fcb33-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="fcb33-146">Faza szkoleniowa</span><span class="sxs-lookup"><span data-stu-id="fcb33-146">Training phase</span></span>

<span data-ttu-id="fcb33-147">Po obliczeniu wartości wyjściowych z fazy wąskiego gardła są one używane jako dane wejściowe do ponownego przeszkolenia końcowej warstwy modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="fcb33-148">Ten proces jest iteracyjny i jest uruchamiany dla liczby razy określonej przez parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="fcb33-149">Podczas każdego przebiegu są oceniane straty i dokładności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="fcb33-150">Następnie dokonuje się odpowiednich korekt w celu ulepszenia modelu w celu zminimalizowania strat i maksymalizacji dokładności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="fcb33-151">Po zakończeniu szkolenia są wyprowadzane dwa formaty modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="fcb33-152">Jednym z nich `.pb` jest wersja modelu, a `.zip` druga jest ML.NET serializowaną wersją modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="fcb33-153">Podczas pracy w środowiskach obsługiwanych przez ML.NET, zaleca `.zip` się użycie wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="fcb33-154">Jednak w środowiskach, w których ML.NET nie jest obsługiwany, masz `.pb` możliwość korzystania z wersji.</span><span class="sxs-lookup"><span data-stu-id="fcb33-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="fcb33-155">Opis wstępnie przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="fcb33-155">Understand the pretrained model</span></span>

<span data-ttu-id="fcb33-156">Wstępnie przeszkolony model używany w tym samouczku jest 101-warstwowy wariant modelu residual network (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="fcb33-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="fcb33-157">Oryginalny model jest przeszkolony do klasyfikowania obrazów do tysiąca kategorii.</span><span class="sxs-lookup"><span data-stu-id="fcb33-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="fcb33-158">Model przyjmuje jako dane wejściowe obraz o rozmiarze 224 x 224 i wyprowadza prawdopodobieństwa klasy dla każdej z klas, na których jest przeszkolony.</span><span class="sxs-lookup"><span data-stu-id="fcb33-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="fcb33-159">Część tego modelu jest używana do szkolenia nowego modelu przy użyciu obrazów niestandardowych do prognozowania między dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="fcb33-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="fcb33-160">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="fcb33-160">Create console application</span></span>

<span data-ttu-id="fcb33-161">Teraz, gdy masz ogólne zrozumienie uczenia się transferu i interfejsu API klasyfikacji obrazów, nadszedł czas, aby utworzyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcb33-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="fcb33-162">Utwórz **aplikację konsoli .NET Core języka C#** o nazwie "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="fcb33-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="fcb33-163">Zainstaluj **pakiet NuGet Microsoft.ML** w wersji **1.4.0:**</span><span class="sxs-lookup"><span data-stu-id="fcb33-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="fcb33-164">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fcb33-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="fcb33-165">Wybierz "nuget.org" jako źródło pakietu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="fcb33-166">Wybierz kartę **Przeglądaj**.</span><span class="sxs-lookup"><span data-stu-id="fcb33-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="fcb33-167">Zaznacz pole wyboru **Dołącz wydanie wstępne.**</span><span class="sxs-lookup"><span data-stu-id="fcb33-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="fcb33-168">Wyszukaj **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="fcb33-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="fcb33-169">Wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="fcb33-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="fcb33-170">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="fcb33-171">Powtórz te kroki dla **pakietów Microsoft.ML.Vision** w wersji **1.4.0**, **SciSharp.TensorFlow.Redist** w wersji **1.15.0**i **Microsoft.ML.ImageAnalytics** w wersji **1.4.0** NuGet.</span><span class="sxs-lookup"><span data-stu-id="fcb33-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="fcb33-172">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="fcb33-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="fcb33-173">Zestawy danych dla tego samouczka są z Maguire, Marc; Dorafshan, Sattar; i Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span><span class="sxs-lookup"><span data-stu-id="fcb33-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="fcb33-174">Przeglądaj wszystkie zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="fcb33-174">Browse all Datasets.</span></span> <span data-ttu-id="fcb33-175">Papier 48.</span><span class="sxs-lookup"><span data-stu-id="fcb33-175">Paper 48.</span></span> <span data-ttu-id="fcb33-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="fcb33-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="fcb33-177">SDNET2018 to zestaw danych obrazu zawierający adnotacje dla pękniętych i niepękniętych konstrukcji betonowych (pokładów mostów, ścian i nawierzchni).</span><span class="sxs-lookup"><span data-stu-id="fcb33-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Próbki mostka zestawu danych SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="fcb33-179">Dane są zorganizowane w trzech podkatalogach:</span><span class="sxs-lookup"><span data-stu-id="fcb33-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="fcb33-180">D zawiera obrazy pokładu mostu</span><span class="sxs-lookup"><span data-stu-id="fcb33-180">D contains bridge deck images</span></span>
- <span data-ttu-id="fcb33-181">P zawiera obrazy nawierzchni</span><span class="sxs-lookup"><span data-stu-id="fcb33-181">P contains pavement images</span></span>
- <span data-ttu-id="fcb33-182">W zawiera obrazy ścienne</span><span class="sxs-lookup"><span data-stu-id="fcb33-182">W contains wall images</span></span>

<span data-ttu-id="fcb33-183">Każdy z tych podkatalogów zawiera dwa dodatkowe podkatalogi z prefiksem:</span><span class="sxs-lookup"><span data-stu-id="fcb33-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="fcb33-184">C jest prefiksem używanym do pękniętych powierzchni</span><span class="sxs-lookup"><span data-stu-id="fcb33-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="fcb33-185">U jest prefiksem używanym do powierzchni niespędowanych</span><span class="sxs-lookup"><span data-stu-id="fcb33-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="fcb33-186">W tym samouczku używane są tylko obrazy pokładu mostu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="fcb33-187">Pobierz [zestaw danych](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) i rozpaj.</span><span class="sxs-lookup"><span data-stu-id="fcb33-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="fcb33-188">Utwórz katalog o nazwie "zasoby" w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fcb33-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="fcb33-189">Skopiuj podkatalogi *dysków CD* i *UD* z ostatnio rozpakowanego katalogu do katalogu *zasobów.*</span><span class="sxs-lookup"><span data-stu-id="fcb33-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="fcb33-190">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="fcb33-190">Create input and output classes</span></span>

1. <span data-ttu-id="fcb33-191">Otwórz plik *Program.cs* i zastąp istniejące `using` instrukcje w górnej części pliku następującymi czynnościami:</span><span class="sxs-lookup"><span data-stu-id="fcb33-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="fcb33-192">Poniżej `Program` klasy w *Program.cs*, utwórz `ImageData`klasę o nazwie .</span><span class="sxs-lookup"><span data-stu-id="fcb33-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="fcb33-193">Ta klasa jest używana do reprezentowania początkowo załadowanych danych.</span><span class="sxs-lookup"><span data-stu-id="fcb33-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="fcb33-194">`ImageData`zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fcb33-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="fcb33-195">`ImagePath`jest w pełni kwalifikowaną ścieżką, w której obraz jest przechowywany.</span><span class="sxs-lookup"><span data-stu-id="fcb33-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="fcb33-196">`Label`jest kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="fcb33-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="fcb33-197">Jest to wartość do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-197">This is the value to predict.</span></span>

1. <span data-ttu-id="fcb33-198">Tworzenie klas dla danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="fcb33-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="fcb33-199">Poniżej `ImageData` klasy zdefiniuj schemat danych wejściowych `ModelInput`w nowej klasie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="fcb33-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="fcb33-200">`ModelInput`zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fcb33-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="fcb33-201">`Image`jest `byte[]` reprezentacją obrazu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-201">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="fcb33-202">Model oczekuje, że dane obrazu mają być tego typu do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-202">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="fcb33-203">`LabelAsKey`jest numeryczną reprezentacją `Label`pliku .</span><span class="sxs-lookup"><span data-stu-id="fcb33-203">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="fcb33-204">`ImagePath`jest w pełni kwalifikowaną ścieżką, w której obraz jest przechowywany.</span><span class="sxs-lookup"><span data-stu-id="fcb33-204">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="fcb33-205">`Label`jest kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="fcb33-205">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="fcb33-206">Jest to wartość do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-206">This is the value to predict.</span></span>

        <span data-ttu-id="fcb33-207">Tylko `Image` `LabelAsKey` i są używane do szkolenia modelu i przewidywań.</span><span class="sxs-lookup"><span data-stu-id="fcb33-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="fcb33-208">Właściwości `ImagePath` `Label` i właściwości są przechowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.</span><span class="sxs-lookup"><span data-stu-id="fcb33-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="fcb33-209">Następnie poniżej `ModelInput` klasy zdefiniuj schemat danych wyjściowych `ModelOutput`w nowej klasie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="fcb33-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="fcb33-210">`ModelOutput`zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fcb33-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="fcb33-211">`ImagePath`jest w pełni kwalifikowaną ścieżką, w której obraz jest przechowywany.</span><span class="sxs-lookup"><span data-stu-id="fcb33-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="fcb33-212">`Label`jest oryginalną kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="fcb33-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="fcb33-213">Jest to wartość do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-213">This is the value to predict.</span></span>
        - <span data-ttu-id="fcb33-214">`PredictedLabel`jest wartością przewidywaną przez model.</span><span class="sxs-lookup"><span data-stu-id="fcb33-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="fcb33-215">Podobne `ModelInput`do , `PredictedLabel` tylko jest wymagane do przewidywania, ponieważ zawiera przewidywanie przez model.</span><span class="sxs-lookup"><span data-stu-id="fcb33-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="fcb33-216">Właściwości `ImagePath` `Label` i właściwości są zachowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.</span><span class="sxs-lookup"><span data-stu-id="fcb33-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="fcb33-217">Tworzenie katalogu obszaru roboczego</span><span class="sxs-lookup"><span data-stu-id="fcb33-217">Create workspace directory</span></span>

<span data-ttu-id="fcb33-218">Gdy dane szkolenia i sprawdzania poprawności nie zmieniają się często, jest dobrą praktyką do buforowania obliczonych wartości wąskiego gardła dla dalszych przebiegów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="fcb33-219">W projekcie utwórz nowy katalog o nazwie *obszar roboczy* do `.pb` przechowywania obliczonych wartości wąskiego gardła i wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="fcb33-220">Definiowanie ścieżek i inicjowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="fcb33-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="fcb33-221">Wewnątrz `Main` metody należy zdefiniować lokalizację zasobów, obliczone wartości `.pb` wąskiego gardła i wersję modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="fcb33-222">Inicjuj zmienną `mlContext` za pomocą nowego wystąpienia [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="fcb33-222">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="fcb33-223">Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie mlContext tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fcb33-224">Jest podobny, koncepcyjnie, do `DBContext` w entity framework.</span><span class="sxs-lookup"><span data-stu-id="fcb33-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="fcb33-225">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="fcb33-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="fcb33-226">Tworzenie metody narzędzia ładowania danych</span><span class="sxs-lookup"><span data-stu-id="fcb33-226">Create data loading utility method</span></span>

<span data-ttu-id="fcb33-227">Obrazy są przechowywane w dwóch podkatalogach.</span><span class="sxs-lookup"><span data-stu-id="fcb33-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="fcb33-228">Przed załadowaniem danych należy sformatować ją `ImageData` na liście obiektów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="fcb33-229">Aby to zrobić, `LoadImagesFromDirectory` należy `Main` utworzyć metodę poniżej metody.</span><span class="sxs-lookup"><span data-stu-id="fcb33-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="fcb33-230">Wewnątrz `LoadImagesDirectory` dodaj następujący kod, aby uzyskać wszystkie ścieżki plików z podkatalogów:</span><span class="sxs-lookup"><span data-stu-id="fcb33-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="fcb33-231">Następnie iterować za pośrednictwem każdego `foreach` z plików za pomocą instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fcb33-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="fcb33-232">Wewnątrz `foreach` instrukcji sprawdź, czy rozszerzenia plików są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fcb33-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="fcb33-233">Interfejs API klasyfikacji obrazów obsługuje formaty JPEG i PNG.</span><span class="sxs-lookup"><span data-stu-id="fcb33-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="fcb33-234">Następnie pobierz etykietę pliku.</span><span class="sxs-lookup"><span data-stu-id="fcb33-234">Then, get the label for the file.</span></span> <span data-ttu-id="fcb33-235">Jeśli `useFolderNameAsLabel` parametr jest `true`ustawiony na , wówczas katalog nadrzędny, w którym zapisywany jest plik, jest używany jako etykieta.</span><span class="sxs-lookup"><span data-stu-id="fcb33-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="fcb33-236">W przeciwnym razie oczekuje, że etykieta będzie prefiksem nazwy pliku lub samej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="fcb33-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="fcb33-237">Na koniec utwórz nowe `ModelInput`wystąpienie .</span><span class="sxs-lookup"><span data-stu-id="fcb33-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="fcb33-238">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="fcb33-238">Prepare the data</span></span>

1. <span data-ttu-id="fcb33-239">Powrót w `Main` metodzie, `LoadFromDirectory` użyj metody narzędzia, aby uzyskać listę obrazów używanych do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="fcb33-240">Następnie należy załadować [`IDataView`](xref:Microsoft.ML.IDataView) obrazy [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) do metody przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="fcb33-241">Dane są ładowane w kolejności, w jakiej zostały odczytane z katalogów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="fcb33-242">Aby zrównoważyć dane, przetasuj ją za [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="fcb33-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="fcb33-243">Modele uczenia maszynowego oczekują, że dane wejściowe będą w formacie liczbowym.</span><span class="sxs-lookup"><span data-stu-id="fcb33-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="fcb33-244">W związku z tym niektóre wstępne przetwarzanie musi być wykonane na danych przed szkoleniem.</span><span class="sxs-lookup"><span data-stu-id="fcb33-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="fcb33-245">Tworzenie [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) składa się [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) z `LoadRawImageBytes` i przekształca.</span><span class="sxs-lookup"><span data-stu-id="fcb33-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="fcb33-246">Transformacja `MapValueToKey` przyjmuje wartość kategoryczną `Label` w kolumnie, konwertuje ją na `KeyType` wartość liczbową i przechowuje ją w nowej kolumnie o nazwie `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="fcb33-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="fcb33-247">Przyjmuje `LoadImages` wartości z `ImagePath` kolumny wraz `imageFolder` z parametrem, aby załadować obrazy do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="fcb33-248">Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby zastosować `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) dane do [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) następuje metoda, która zwraca [`IDataView`](xref:Microsoft.ML.IDataView) zawierające wstępnie przetworzone dane.</span><span class="sxs-lookup"><span data-stu-id="fcb33-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="fcb33-249">Aby uszkoliwać model, ważne jest, aby mieć zestaw danych szkoleniowych, a także zestaw danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="fcb33-250">Model jest szkolony na zestawie treningowym.</span><span class="sxs-lookup"><span data-stu-id="fcb33-250">The model is trained on the training set.</span></span> <span data-ttu-id="fcb33-251">Jak dobrze sprawia, że prognozy na niewidoczne dane jest mierzona przez wydajność względem zestawu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="fcb33-252">Na podstawie wyników tej wydajności, model wprowadza zmiany do tego, czego się nauczył w celu poprawy.</span><span class="sxs-lookup"><span data-stu-id="fcb33-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="fcb33-253">Zestaw sprawdzania poprawności może pochodzić z podziału oryginalnego zestawu danych lub z innego źródła, które zostało już odłożone w tym celu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="fcb33-254">W takim przypadku wstępnie przetworzony zestaw danych jest dzielony na zestawy szkoleniowe, sprawdzania poprawności i testów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="fcb33-255">Powyższy przykład kodu wykonuje dwa podziały.</span><span class="sxs-lookup"><span data-stu-id="fcb33-255">The code sample above performs two splits.</span></span> <span data-ttu-id="fcb33-256">Po pierwsze, wstępnie przetworzone dane są dzielone, a 70% jest używane do szkolenia, podczas gdy pozostałe 30% jest używane do sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="fcb33-257">Następnie zestaw sprawdzania poprawności 30% jest dalej podzielony na zestawy sprawdzania poprawności i testów, w których 90% jest używane do sprawdzania poprawności, a 10% jest używane do testowania.</span><span class="sxs-lookup"><span data-stu-id="fcb33-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="fcb33-258">Sposobem na zastanowienie się nad celem tych partycji danych jest zdawać egzamin.</span><span class="sxs-lookup"><span data-stu-id="fcb33-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="fcb33-259">Podczas studiowania do egzaminu, można przejrzeć notatki, książki, lub inne zasoby, aby zrozumieć pojęcia, które są na egzaminie.</span><span class="sxs-lookup"><span data-stu-id="fcb33-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="fcb33-260">Do tego służy zestaw pociągów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-260">This is what the train set is for.</span></span> <span data-ttu-id="fcb33-261">Następnie możesz zdać makietę egzaminu, aby potwierdzić swoją wiedzę.</span><span class="sxs-lookup"><span data-stu-id="fcb33-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="fcb33-262">W tym miejscu przydaje się zestaw sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="fcb33-263">Chcesz sprawdzić, czy masz dobre zrozumienie pojęć przed podjęciem rzeczywistego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="fcb33-264">Na podstawie tych wyników, wziąć pod uwagę, co się stało lub nie rozumie dobrze i włączyć zmiany, jak przejrzeć do prawdziwego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="fcb33-265">Wreszcie, można zdać egzamin.</span><span class="sxs-lookup"><span data-stu-id="fcb33-265">Finally, you take the exam.</span></span> <span data-ttu-id="fcb33-266">Jest to, co zestaw testów jest używany do.</span><span class="sxs-lookup"><span data-stu-id="fcb33-266">This is what the test set is used for.</span></span> <span data-ttu-id="fcb33-267">Nigdy nie widziałeś pytań, które są na egzaminie, a teraz korzystać z tego, czego nauczyłeś się od szkolenia i walidacji, aby zastosować swoją wiedzę do zadania pod ręką.</span><span class="sxs-lookup"><span data-stu-id="fcb33-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="fcb33-268">Przypisz partycje ich odpowiednie wartości dla pociągu, sprawdzania poprawności i danych testowych.</span><span class="sxs-lookup"><span data-stu-id="fcb33-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="fcb33-269">Definiowanie potoku szkolenia</span><span class="sxs-lookup"><span data-stu-id="fcb33-269">Define the training pipeline</span></span>

<span data-ttu-id="fcb33-270">Szkolenie modelowe składa się z kilku kroków.</span><span class="sxs-lookup"><span data-stu-id="fcb33-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="fcb33-271">Po pierwsze interfejs API klasyfikacji obrazów jest używany do szkolenia modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="fcb33-272">Następnie zakodowane etykiety w `PredictedLabel` kolumnie są konwertowane z powrotem `MapKeyToValue` do ich oryginalnej wartości kategorycznej przy użyciu transformacji.</span><span class="sxs-lookup"><span data-stu-id="fcb33-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="fcb33-273">Utwórz nową zmienną do przechowywania zestawu wymaganych `ImageClassificationTrainer`i opcjonalnych parametrów dla pliku .</span><span class="sxs-lookup"><span data-stu-id="fcb33-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="fcb33-274">Trwa `ImageClassificationTrainer` kilka parametrów opcjonalnych:</span><span class="sxs-lookup"><span data-stu-id="fcb33-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="fcb33-275">`FeatureColumnName`jest kolumną, która jest używana jako dane wejściowe dla modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="fcb33-276">`LabelColumnName`jest kolumną wartości do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="fcb33-277">`ValidationSet`[`IDataView`](xref:Microsoft.ML.IDataView) zawiera dane dotyczące sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="fcb33-278">`Arch`określa, które z wstępnie wyszkolonych architektur modelu do użycia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="fcb33-279">W tym samouczku użyto 101-warstwowego wariantu modelu ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="fcb33-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="fcb33-280">`MetricsCallback`wiąże funkcję do śledzenia postępu podczas treningu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="fcb33-281">`TestOnTrainSet`informuje model do pomiaru wydajności względem zestawu szkoleniowego, gdy nie ma zestawu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="fcb33-282">`ReuseTrainSetBottleneckCachedValues`informuje model, czy mają być używane wartości buforowane z fazy wąskiego gardła w kolejnych przebiegach.</span><span class="sxs-lookup"><span data-stu-id="fcb33-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="fcb33-283">Faza wąskiego gardła jest jednorazową przemijaczą obliczeniową, która jest intensywna obliczeniowo przy pierwszym wykonaniu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="fcb33-284">Jeśli dane szkoleniowe nie zmienią się i chcesz eksperymentować przy użyciu innej liczby epok lub rozmiaru partii, przy użyciu buforowanych wartości znacznie zmniejsza czas wymagany do szkolenia modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="fcb33-285">`ReuseValidationSetBottleneckCachedValues`jest podobny `ReuseTrainSetBottleneckCachedValues` tylko do tego, że w tym przypadku jest dla zestawu danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="fcb33-286">`WorkspacePath`definiuje katalog, w którym mają być przechowywane `.pb` obliczone wartości wąskiego gardła i wersja modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="fcb33-287">Zdefiniuj potok [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) szkolenia, który składa się zarówno z `mapLabelEstimator` . `ImageClassificationTrainer`i .</span><span class="sxs-lookup"><span data-stu-id="fcb33-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="fcb33-288">Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby trenować model.</span><span class="sxs-lookup"><span data-stu-id="fcb33-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="fcb33-289">Użyj modelu</span><span class="sxs-lookup"><span data-stu-id="fcb33-289">Use the model</span></span>

<span data-ttu-id="fcb33-290">Teraz, gdy przeszkoliłeś swój model, nadszedł czas, aby użyć go do klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="fcb33-291">Poniżej `Main` metody należy utworzyć nową `OutputPrediction` metodę narzędzia wywoływaną do wyświetlania informacji o przewidywaniu w konsoli.</span><span class="sxs-lookup"><span data-stu-id="fcb33-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="fcb33-292">Klasyfikowanie pojedynczego obrazu</span><span class="sxs-lookup"><span data-stu-id="fcb33-292">Classify a single image</span></span>

1. <span data-ttu-id="fcb33-293">Dodaj nową metodę `ClassifySingleImage` o `Main` nazwie poniżej metody, aby i wyjście przewidywania pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="fcb33-294">Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wewnątrz `ClassifySingleImage` metody.</span><span class="sxs-lookup"><span data-stu-id="fcb33-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="fcb33-295">Jest [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wygody interfejsu API, który pozwala przekazać, a następnie wykonać przewidywanie na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="fcb33-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="fcb33-296">Aby uzyskać `ModelInput` dostęp do `data` [`IDataView`](xref:Microsoft.ML.IDataView) pojedynczego [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) wystąpienia, przekonwertuj je na [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metodę, a następnie uzyskaj pierwszą obserwację.</span><span class="sxs-lookup"><span data-stu-id="fcb33-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="fcb33-297">Użyj [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) metody, aby sklasyfikować obraz.</span><span class="sxs-lookup"><span data-stu-id="fcb33-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="fcb33-298">Dane wyjściowe prognozowania `OutputPrediction` do konsoli z metody.</span><span class="sxs-lookup"><span data-stu-id="fcb33-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="fcb33-299">Wewnątrz `Main` metody wywołać `ClassifySingleImage` przy użyciu zestawu testów obrazów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="fcb33-300">Klasyfikowanie wielu obrazów</span><span class="sxs-lookup"><span data-stu-id="fcb33-300">Classify multiple images</span></span>

1. <span data-ttu-id="fcb33-301">Dodaj nową metodę `ClassifyImages` o `ClassifySingleImage` nazwie poniżej metody, aby i wyjście wielu prognoz obrazu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="fcb33-302">Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) zawierające prognoz przy użyciu [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody.</span><span class="sxs-lookup"><span data-stu-id="fcb33-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="fcb33-303">Dodaj następujący kod `ClassifyImages` wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="fcb33-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="fcb33-304">Aby iterować nad prognozami, przekonwertować `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) do [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) przy użyciu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody, a następnie uzyskać pierwsze 10 obserwacji.</span><span class="sxs-lookup"><span data-stu-id="fcb33-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="fcb33-305">Iteracji i danych oryginalnych i przewidywanych etykiet dla prognoz.</span><span class="sxs-lookup"><span data-stu-id="fcb33-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="fcb33-306">Na koniec wewnątrz `Main` metody `ClassifyImages` wywołać przy użyciu zestawu testów obrazów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="fcb33-307">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="fcb33-307">Run the application</span></span>

<span data-ttu-id="fcb33-308">Uruchom aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="fcb33-308">Run your console app.</span></span> <span data-ttu-id="fcb33-309">Dane wyjściowe powinny być podobne do poniższego.</span><span class="sxs-lookup"><span data-stu-id="fcb33-309">The output should be similar to that below.</span></span> <span data-ttu-id="fcb33-310">Możesz zobaczyć ostrzeżenia lub przetwarzania wiadomości, ale te komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="fcb33-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="fcb33-311">Dla zwięzłości, wyjście zostało skondensowane.</span><span class="sxs-lookup"><span data-stu-id="fcb33-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="fcb33-312">**Faza wąskiego gardła**</span><span class="sxs-lookup"><span data-stu-id="fcb33-312">**Bottleneck phase**</span></span>

<span data-ttu-id="fcb33-313">Żadna wartość nie jest drukowana dla nazwy `byte[]` obrazu, ponieważ obrazy są ładowane jako, w związku z tym nie ma nazwy obrazu do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="fcb33-314">**Faza szkoleniowa**</span><span class="sxs-lookup"><span data-stu-id="fcb33-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="fcb33-315">**Klasyfikowanie obrazów wyjściowych**</span><span class="sxs-lookup"><span data-stu-id="fcb33-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="fcb33-316">Po oględzinach obrazu *7001-220.jpg* widać, że w rzeczywistości nie jest pęknięty.</span><span class="sxs-lookup"><span data-stu-id="fcb33-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Obraz zestawu danych SDNET2018 używany do przewidywania](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="fcb33-318">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="fcb33-318">Congratulations!</span></span> <span data-ttu-id="fcb33-319">Teraz udało ci się zbudować model uczenia głębokiego do klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="fcb33-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="fcb33-320">Ulepszanie modelu</span><span class="sxs-lookup"><span data-stu-id="fcb33-320">Improve the model</span></span>

<span data-ttu-id="fcb33-321">Jeśli nie jesteś zadowolony z wyników modelu, możesz spróbować poprawić jego wydajność, próbując wykonać niektóre z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="fcb33-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="fcb33-322">**Więcej danych:** Im więcej przykładów model uczy się od, tym lepiej wykonuje.</span><span class="sxs-lookup"><span data-stu-id="fcb33-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="fcb33-323">Pobierz pełny [zestaw danych SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) i użyj go do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fcb33-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="fcb33-324">**Powiększynie danych: Powszechną**techniką dodawania różnorodności do danych jest powiększenie danych poprzez zrobienie obrazu i zastosowanie różnych przekształceń (obracanie, przerzucanie, przesuwanie, przycinanie).</span><span class="sxs-lookup"><span data-stu-id="fcb33-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="fcb33-325">To dodaje bardziej zróżnicowane przykłady dla modelu, aby dowiedzieć się od.</span><span class="sxs-lookup"><span data-stu-id="fcb33-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="fcb33-326">**Trenuj przez dłuższy czas**: Im dłużej trenujesz, tym bardziej dostrojony będzie model.</span><span class="sxs-lookup"><span data-stu-id="fcb33-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="fcb33-327">Zwiększenie liczby epok może poprawić wydajność modelu.</span><span class="sxs-lookup"><span data-stu-id="fcb33-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="fcb33-328">**Eksperymentuj z hiper-parametrami**: Oprócz parametrów użytych w tym samouczku, inne parametry mogą być dostrojone, aby potencjalnie poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="fcb33-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="fcb33-329">Zmiana szybkości uczenia się, która określa wielkość aktualizacji wprowadzonych do modelu po każdej epoce może poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="fcb33-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="fcb33-330">**Użyj innej architektury modelu:** W zależności od tego, jak wyglądają dane, model, który najlepiej może nauczyć się jego funkcji, może się różnić.</span><span class="sxs-lookup"><span data-stu-id="fcb33-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="fcb33-331">Jeśli nie jesteś zadowolony z wydajności modelu, spróbuj zmienić architekturę.</span><span class="sxs-lookup"><span data-stu-id="fcb33-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fcb33-332">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fcb33-332">Additional Resources</span></span>

- <span data-ttu-id="fcb33-333">[Uczenie głębokie a uczenie maszynowe](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="fcb33-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcb33-334">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fcb33-334">Next steps</span></span>

<span data-ttu-id="fcb33-335">W tym samouczku dowiesz się, jak utworzyć niestandardowy model uczenia głębokiego przy użyciu uczenia transferu, wstępnie przeszkolony model tensorflow klasyfikacji obrazów i ML.NET interfejsu API klasyfikacji obrazów, aby klasyfikować obrazy powierzchni betonowych jako pęknięte lub nieskładkowane.</span><span class="sxs-lookup"><span data-stu-id="fcb33-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="fcb33-336">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="fcb33-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fcb33-337">Wykrywanie obiektów</span><span class="sxs-lookup"><span data-stu-id="fcb33-337">Object Detection</span></span>](object-detection-onnx.md)
