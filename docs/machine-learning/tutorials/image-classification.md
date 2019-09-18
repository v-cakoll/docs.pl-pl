---
title: 'Samouczek: Ponowne uczenie klasyfikatora obrazu TensorFlow — uczenie transferu'
description: Dowiedz się, jak ponownie przeprowadzić uczenie modelu TensorFlow klasyfikacji obrazów przy użyciu uczenia transferowego i ML.NET. Oryginalny model został przeszkolony do klasyfikowania poszczególnych obrazów. Po przeprowadzeniu ponownego uczenia nowy model organizuje obrazy w szerokich kategoriach.
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e069abe44b77b1dc31b78ecec1971ccc73f2e012
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054077"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="f4d2c-105">Samouczek: Ponowne uczenie klasyfikatora obrazu TensorFlow z uczeniem transferu i ML.NET</span><span class="sxs-lookup"><span data-stu-id="f4d2c-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="f4d2c-106">Dowiedz się, jak ponownie przeprowadzić uczenie modelu TensorFlow klasyfikacji obrazów przy użyciu uczenia transferowego i ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="f4d2c-107">Oryginalny model został przeszkolony do klasyfikowania poszczególnych obrazów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="f4d2c-108">Po przeprowadzeniu ponownego uczenia nowy model organizuje obrazy w szerokich kategoriach.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="f4d2c-109">Uczenie modelu [klasyfikacji obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od podstaw wymaga ustawienia milionów parametrów, moc z etykietami danych szkoleniowych i ogromną ilość zasobów obliczeniowych (setki godzin procesora GPU).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="f4d2c-110">Chociaż nie jest tak wydajny, jak uczenie modelu niestandardowego od podstaw, uczenie przenoszenia pozwala na podjęcie tego procesu przez pracę z tysiącami obrazów i milionów obrazów z etykietami, a następnie szybko utworzyć dostosowany model (w ciągu godziny na maszynie bez PROCESOR GPU).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="f4d2c-111">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f4d2c-112">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="f4d2c-112">Understand the problem</span></span>
> * <span data-ttu-id="f4d2c-113">Ponowne użycie i dostosowanie modelu wstępnie przeszkolonego</span><span class="sxs-lookup"><span data-stu-id="f4d2c-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="f4d2c-114">Klasyfikowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="f4d2c-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="f4d2c-115">Co to jest uczenie transferu?</span><span class="sxs-lookup"><span data-stu-id="f4d2c-115">What is transfer learning?</span></span>

<span data-ttu-id="f4d2c-116">Co zrobić, jeśli możesz użyć wcześniej przeszkolonego modelu, aby rozwiązać podobny problem i przeszkolić wszystkie lub niektóre warstwy tego modelu w celu rozwiązania problemu?</span><span class="sxs-lookup"><span data-stu-id="f4d2c-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="f4d2c-117">Ta technika ponownego wykorzystania części już przeszkolonego modelu w celu utworzenia nowego modelu jest znana jako [nauka transferu](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="f4d2c-118">Przykład klasyfikacji obrazów — Omówienie</span><span class="sxs-lookup"><span data-stu-id="f4d2c-118">Image classification sample overview</span></span>

<span data-ttu-id="f4d2c-119">Przykładem jest Aplikacja konsolowa, która używa ML.NET do tworzenia klasyfikatora obrazu przez ponowne użycie wstępnie przeszkolonego modelu do klasyfikowania obrazów z niewielką ilością danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="f4d2c-120">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="f4d2c-121">Należy pamiętać, że domyślnie konfiguracja projektu .NET dla tego samouczka dotyczy platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4d2c-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f4d2c-122">Prerequisites</span></span>

* <span data-ttu-id="f4d2c-123">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="f4d2c-124">Pakiet NuGet Microsoft.ML 1.0.0</span><span class="sxs-lookup"><span data-stu-id="f4d2c-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="f4d2c-125">Pakiet NuGet Microsoft. ML. ImageAnalytics 1.0.0</span><span class="sxs-lookup"><span data-stu-id="f4d2c-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="f4d2c-126">Pakiet NuGet Microsoft. ML. TensorFlow 0.12.0</span><span class="sxs-lookup"><span data-stu-id="f4d2c-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="f4d2c-127">Katalog zasobów samouczka. Plik ZIP</span><span class="sxs-lookup"><span data-stu-id="f4d2c-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="f4d2c-128">Model uczenia maszynowego InceptionV1</span><span class="sxs-lookup"><span data-stu-id="f4d2c-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="f4d2c-129">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="f4d2c-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="f4d2c-130">[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzbiór Machine Learning, które są obszarami revolutionizing, takimi jak przetwarzanie obrazów i rozpoznawanie mowy.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="f4d2c-131">Modele uczenia głębokiego są przeszkolone przy użyciu dużych zestawów [danych z etykietami](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych](https://en.wikipedia.org/wiki/Artificial_neural_network) , które zawierają wiele warstw szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="f4d2c-132">Uczenie głębokie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-132">Deep learning:</span></span>

* <span data-ttu-id="f4d2c-133">Wykonuje lepsze zadania, takie jak przetwarzanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="f4d2c-134">Dobrze sprawdza się w przypadku dużych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="f4d2c-135">Klasyfikacja obrazu to typowe zadanie Machine Learning, które pozwala nam na automatyczne klasyfikowanie obrazów do wielu kategorii, takich jak:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="f4d2c-136">Wykrywanie ludzkiej twarz w obrazie.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="f4d2c-137">Wykrywanie kotów a psy.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="f4d2c-138">Lub tak jak w przypadku następujących obrazów określających, czy obraz jest (n) jedzeniem, Zabawka lub urządzeniem:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="f4d2c-139">![obraz przedstawiający obraz przedstawiający zdjęcie z obrazu Pizza Teddy](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![![](./media/image-classification/220px-Pepperoni_pizza.jpg)
](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="f4d2c-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="f4d2c-140">Powyższe obrazy należą do Wikimedia Commons Attribution i są przypisywane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="f4d2c-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="f4d2c-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="f4d2c-142">"119px-Nalle_-_a_small_brown_teddy_bear. jpg" przez [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) — własne grafy, CC przez-sa 2,0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="f4d2c-143">"193px-Broodrooster. jpg" według [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) — zadania własne, CC według-sa 3,0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="f4d2c-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="f4d2c-144">Nauka transferu obejmuje kilka strategii, takich jak ponowne *uczenie wszystkich warstw* i przedniej *warstwy*.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="f4d2c-145">Ten samouczek wyjaśnia i pokazuje, jak używać *przedostatniej strategii warstwy*.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="f4d2c-146">Przedstawiona *strategia warstwy* ponownie używa modelu, który jest już wstępnie przeszkolony do rozwiązywania określonego problemu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="f4d2c-147">Następnie strategia ponownie przeprowadzi przeszkolenie ostatniej warstwy tego modelu w celu rozwiązania nowego problemu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="f4d2c-148">Użycie wstępnie nauczonego modelu w ramach nowego modelu spowoduje znaczne oszczędności czasu i zasobów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="f4d2c-149">Model klasyfikacji obrazów ponownie używa [modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), który jest popularnym modelem rozpoznawania obrazu przeszkolonym na `ImageNet` zestawie danych, gdzie model TensorFlow próbuje klasyfikować całe obrazy do tysięcy klas, takich jak "parasol", "Jersey" i " Zmywarka ".</span><span class="sxs-lookup"><span data-stu-id="f4d2c-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="f4d2c-150">Może być sklasyfikowany jako [głębokiej sieci neuronowych splotowych](https://en.wikipedia.org/wiki/Convolutional_neural_network) , dzięki czemu można uzyskać odpowiednią wydajność w przypadku zadań rozpoznawania wizualnego, dopasowanie lub przekroczenie wydajności ludzkich w niektórych domenach. `Inception v1 model`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-150">The `Inception v1 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="f4d2c-151">Model/algorytm został opracowany przez wielu badaczy i w oparciu o oryginalny papier: ["Rozmyślisz architekturę rozpoczęcia dla przetwarzanie obrazów" według Szegedy. wsp.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="f4d2c-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="f4d2c-152">Ponieważ program został już wstępnie przeszkolony na tysiącach różnych obrazów, zawiera [funkcje obrazu](https://en.wikipedia.org/wiki/Feature_(computer_vision)) niezbędne do identyfikacji obrazu. `Inception model`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="f4d2c-153">Niższe warstwy funkcji obrazu rozpoznają proste funkcje (takie jak krawędzie), a wyższe warstwy rozpoznają bardziej złożone funkcje (takie jak kształty).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="f4d2c-154">Warstwa końcowa jest przeszkolone względem znacznie mniejszego zestawu danych, ponieważ zaczynasz od wstępnie nauczonego modelu, który już rozumie sposób klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="f4d2c-155">Ponieważ model pozwala na klasyfikowanie więcej niż dwóch kategorii, jest to przykład [klasyfikatora wieloklasowego](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="f4d2c-156">`TensorFlow`jest popularnym zestawem narzędzi uczenia głębokiego i uczenia maszynowego, który umożliwia uczenie rozległych sieci neuronowych (i ogólnych obliczeń `transformer` liczbowych), i jest zaimplementowany w ml.NET.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="f4d2c-157">Ten samouczek służy do ponownego użycia programu `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="f4d2c-158">Jak pokazano na poniższym diagramie, należy dodać odwołanie do pakietów NuGet ML.NET w aplikacjach .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="f4d2c-159">W obszarze okładek ml.NET obejmuje i odwołuje się do `TensorFlow` biblioteki natywnej, która umożliwia pisanie kodu ładującego istniejący plik `TensorFlow` modelu wyszkolonego do oceny.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Diagram TensorFlow transformacji ML.NET](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="f4d2c-161">Program `Inception model` jest szkolony do klasyfikowania obrazów do tysięcy kategorii, ale należy sklasyfikować obrazy w mniejszym zestawie kategorii i tylko te kategorie.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="f4d2c-162">Wprowadź część elementu `transfer learning`. `transfer`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="f4d2c-163">Można przenieść `Inception model`możliwość rozpoznawania i klasyfikowania obrazów do nowych, ograniczonej kategorii klasyfikatora niestandardowego obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="f4d2c-164">Zamierzasz ponownie przeprowadzić przeszkolenie ostatniej warstwy tego modelu przy użyciu zestawu trzech kategorii:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="f4d2c-165">Żywność</span><span class="sxs-lookup"><span data-stu-id="f4d2c-165">Food</span></span>
* <span data-ttu-id="f4d2c-166">Zabawki</span><span class="sxs-lookup"><span data-stu-id="f4d2c-166">Toy</span></span>
* <span data-ttu-id="f4d2c-167">Wprowadzony</span><span class="sxs-lookup"><span data-stu-id="f4d2c-167">Appliance</span></span>

<span data-ttu-id="f4d2c-168">Warstwa używa [algorytmu regresji logistycznej](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) w celu wyszukania odpowiedniej kategorii tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="f4d2c-169">Ten algorytm klasyfikuje przy użyciu prawdopodobieństwa, aby określić odpowiedź, dając jedną wartość do właściwej kategorii i wartość zerową innym.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="f4d2c-170">DataSet</span><span class="sxs-lookup"><span data-stu-id="f4d2c-170">DataSet</span></span>

<span data-ttu-id="f4d2c-171">Istnieją dwa źródła danych: `.tsv` plik i pliki obrazów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="f4d2c-172">Plik zawiera dwie kolumny: pierwszy jest zdefiniowany jako `ImagePath` , a drugi jest `Label` odpowiadający obrazowi. `tags.tsv`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="f4d2c-173">Następujący przykładowy plik nie ma wiersza nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-173">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="f4d2c-174">Obrazy szkoleniowe i testowe znajdują się w folderach zasobów, które zostaną pobrane w pliku zip.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="f4d2c-175">Te obrazy należą do Wikimedia Commons Attribution.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="f4d2c-176">*[Wikimedia Commons Attribution](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych nośników.*</span><span class="sxs-lookup"><span data-stu-id="f4d2c-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="f4d2c-177">Pobrano 10:48, 17 października 2018 z:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="f4d2c-178">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="f4d2c-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="f4d2c-179">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="f4d2c-179">Create a project</span></span>

1. <span data-ttu-id="f4d2c-180">Utwórz **aplikację konsolową .NET Core** o nazwie "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="f4d2c-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="f4d2c-181">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f4d2c-182">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f4d2c-183">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="f4d2c-184">Kliknij listę rozwijaną **wersja** , wybierz pakiet **1.0.0** z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="f4d2c-185">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="f4d2c-186">Powtórz te kroki dla **Microsoft. ml. ImageAnalytics v 1.0.0** i **Microsoft. ml. TensorFlow v 0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="f4d2c-187">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="f4d2c-187">Prepare your data</span></span>

1. <span data-ttu-id="f4d2c-188">Pobierz [plik zip katalogu zasobów projektu](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="f4d2c-189">Skopiuj katalog do katalogu projektu *TransferLearningTF.* `assets`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="f4d2c-190">Ten katalog i jego podkatalogi zawierają pliki danych i obsługi (z wyjątkiem modelu, który zostanie pobrany i dodany w następnym kroku), co jest potrzebne w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="f4d2c-191">Pobierz [model rozpoczęcia](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="f4d2c-192">Skopiuj zawartość `inception5h` katalogu w sposób niespakowany do katalogu projektu `assets\inputs-train\inception` *TransferLearningTF* .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="f4d2c-193">Ten katalog zawiera model i dodatkowe pliki pomocnicze, które są odpowiednie dla tego samouczka, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Zawartość katalogu początkowej](./media/image-classification/inception-files.png)

5. <span data-ttu-id="f4d2c-195">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu zasobów i podkatalogach i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="f4d2c-196">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f4d2c-197">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="f4d2c-197">Create classes and define paths</span></span>

<span data-ttu-id="f4d2c-198">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="f4d2c-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="f4d2c-199">Utwórz pola globalne, aby przechowywać ścieżki do różnych elementów zawartości, oraz zmienne globalne dla `LabelTokey`,`ImageReal`i `PredictedLabelValue`:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="f4d2c-200">`_assetsPath`ma ścieżkę do zasobów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="f4d2c-201">`_trainTagsTsv`ma ścieżkę do pliku TSV tagów danych obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="f4d2c-202">`_predictTagsTsv`ma ścieżkę do pliku TSV ze znacznikami danych obrazu predykcyjnego.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="f4d2c-203">`_trainImagesFolder`ma ścieżkę do obrazów używanych do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="f4d2c-204">`_predictImagesFolder`ma ścieżkę do obrazów, które mają być klasyfikowane przez szkolony model.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="f4d2c-205">`_inceptionPb`ma ścieżkę do wstępnie przeszkolonego modelu, który ma zostać ponownie użyty w celu ponownego nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="f4d2c-206">`_inputImageClassifierZip`ma ścieżkę, z której jest ładowany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="f4d2c-207">`_outputImageClassifierZip`ma ścieżkę, w której jest zapisywany model szkolony.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="f4d2c-208">`LabelTokey``Label` jest wartością zamapowana na klucz.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="f4d2c-209">`ImageReal`jest kolumną zawierającą przewidywaną wartość obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="f4d2c-210">`PredictedLabelValue`jest kolumną zawierającą przewidywaną wartość etykiety.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="f4d2c-211">Dodaj następujący kod do wiersza bezpośrednio powyżej `Main` metody, aby określić te ścieżki i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="f4d2c-212">Utwórz klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="f4d2c-213">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="f4d2c-214">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="f4d2c-215">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="f4d2c-216">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f4d2c-217">Plik *ImageData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f4d2c-218">Dodaj następującą `using` instrukcję na początku *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="f4d2c-219">Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageData` klasy do pliku *ImageData.cs* :</span><span class="sxs-lookup"><span data-stu-id="f4d2c-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="f4d2c-220">`ImageData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="f4d2c-221">`ImagePath`zawiera nazwę pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="f4d2c-222">`Label`zawiera wartość etykiety obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="f4d2c-223">Dodaj nową klasę do projektu dla `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="f4d2c-224">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="f4d2c-225">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="f4d2c-226">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f4d2c-227">Plik *ImagePrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="f4d2c-228">`System.Collections.Generic` Usuń obie `System.Text` iteinstrukcjew`using` górnej części *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="f4d2c-229">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma `ImagePrediction` klasę, do pliku *ImagePrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="f4d2c-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="f4d2c-230">`ImagePrediction`jest klasą przewidywania obrazów i ma następujące pola:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="f4d2c-231">`Score`zawiera procent zaufania dla danej klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="f4d2c-232">`PredictedLabelValue`zawiera wartość dla etykiety klasyfikacji predykcyjnej obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="f4d2c-233">`ImagePrediction`jest klasą używaną do przewidywania po przeszkoleniu modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="f4d2c-234">Ma `string` (`ImagePath`) dla ścieżki obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="f4d2c-235">`Label` Służy do ponownego użycia i ponownej nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="f4d2c-236">`PredictedLabelValue` Jest używany podczas przewidywania i oceny.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="f4d2c-237">W celu dokonania oceny dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model są używane.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="f4d2c-238">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f4d2c-239">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f4d2c-240">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="f4d2c-240">Initialize variables in Main</span></span>

<span data-ttu-id="f4d2c-241">`MLContext`Zainicjuj `mlContext` zmienną z nowym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="f4d2c-242">Zamień wiersz na następujący kod `Main` w metodzie: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="f4d2c-243">Tworzenie struktury dla domyślnych parametrów</span><span class="sxs-lookup"><span data-stu-id="f4d2c-243">Create a struct for default parameters</span></span>

<span data-ttu-id="f4d2c-244">Model rozpoczęcia zawiera kilka domyślnych parametrów, które należy przekazać.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="f4d2c-245">Utwórz strukturę służącą do mapowania domyślnych wartości parametrów na przyjazne nazwy o następującym kodzie, zaraz po `Main()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="f4d2c-246">Utwórz metodę narzędzia do wyświetlania</span><span class="sxs-lookup"><span data-stu-id="f4d2c-246">Create a display utility method</span></span>

<span data-ttu-id="f4d2c-247">Ponieważ wyświetlasz dane obrazu i powiązane przewidywania więcej niż raz, Utwórz metodę narzędzia do wyświetlania, aby obsłużyć wyświetlanie obrazu i wyników przewidywania.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="f4d2c-248">`DisplayResults()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="f4d2c-249">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-249">Displays the predicted results.</span></span>

<span data-ttu-id="f4d2c-250">Utwórz metodę, tuż po strukturze, przy użyciu następującego kodu: `InceptionSettings` `DisplayResults()`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="f4d2c-251">Metoda wypełniana `ImagePath`wrazzprzewidywanymi polami.`ImagePrediction` `Transform()`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="f4d2c-252">W miarę postępów procesu ML.NET każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="f4d2c-253">`DisplayResults()` Metoda zostanie wywołana przy użyciu dwóch metod klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="f4d2c-254">Tworzenie metody narzędziowej pliku. tsv</span><span class="sxs-lookup"><span data-stu-id="f4d2c-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="f4d2c-255">`ReadFromTsv()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="f4d2c-256">Odczytuje plik danych `tags.tsv` obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="f4d2c-257">Dodaje ścieżkę pliku do nazwy pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="f4d2c-258">Ładuje dane pliku do obiektu IEnumerable`ImageData` .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="f4d2c-259">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `PairAndDisplayResults()` `ReadFromTsv()`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="f4d2c-260">Poniższy kod analizuje `tags.tsv` plik, aby dodać ścieżkę pliku do nazwy pliku obrazu `ImagePath` dla właściwości `Label` i załadować `ImageData` ją oraz do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="f4d2c-261">Dodaj ją jako pierwszy wiersz `ReadFromTsv()` metody.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="f4d2c-262">Do wyświetlania wyników przewidywania potrzebna jest w pełni kwalifikowana ścieżka do pliku.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="f4d2c-263">Istnieją trzy podstawowe koncepcje w ML.NET: [Dane](../resources/glossary.md#data), [Transformatory](../resources/glossary.md#transformer)i [szacowania](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="f4d2c-264">Ponowne użycie i dostrajanie modelu wstępnie przeszkolonego</span><span class="sxs-lookup"><span data-stu-id="f4d2c-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="f4d2c-265">Dodaj następujące wywołanie do `ReuseAndTuneInceptionModel()`metody jako następny wiersz kodu `Main()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="f4d2c-266">`ReuseAndTuneInceptionModel()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="f4d2c-267">Ładuje dane</span><span class="sxs-lookup"><span data-stu-id="f4d2c-267">Loads the data</span></span>
* <span data-ttu-id="f4d2c-268">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="f4d2c-269">Ocenia model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="f4d2c-270">Dostraja (reciągia) model.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="f4d2c-271">Wyświetla wyniki modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-271">Displays model results.</span></span>
* <span data-ttu-id="f4d2c-272">Oblicza model.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-272">Evaluates the model.</span></span>
* <span data-ttu-id="f4d2c-273">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-273">Returns the model.</span></span>

<span data-ttu-id="f4d2c-274">Utwórz metodę, tuż `InceptionSettings` po `DisplayResults()` strukturze i tuż przed metodą, używając następującego kodu: `ReuseAndTuneInceptionModel()`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="f4d2c-275">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="f4d2c-275">Load the data</span></span>

<span data-ttu-id="f4d2c-276">Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f4d2c-277">`IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="f4d2c-278">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="f4d2c-279">Załaduj dane przy użyciu `MLContext.Data.LoadFromTextFile` otoki.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="f4d2c-280">Dodaj następujący kod w następnym wierszu `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="f4d2c-281">Wyodrębnij funkcje i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="f4d2c-281">Extract Features and transform the data</span></span>

<span data-ttu-id="f4d2c-282">Wstępne przetwarzanie i czyszczenie danych to ważne zadania, które wystąpiły, zanim zestaw danych jest efektywnie używany do uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="f4d2c-283">Korzystanie z danych bez wykonywania zadań modelowania może dawać mylące wyniki.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="f4d2c-284">Algorytmy uczenia maszynowego rozumieją dane [featurized](../resources/glossary.md#feature) i podczas pracy z sieciami głębokiej neuronowych należy dostosować obrazy do formatu oczekiwanego przez sieć.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="f4d2c-285">Ten format jest [wektorem liczbowym](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="f4d2c-286">Po przeprowadzeniu szkolenia i oceny należy przewidzieć wartości kolumn **etykiet** .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="f4d2c-287">Gdy korzystasz z wstępnie przeszkolonego modelu, Mapuj pola do nowego modelu przy użyciu metody [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="f4d2c-288">Ta metoda `Label` przekształca w kolumnę typu liczbowego (`LabelTokey`) i dodaje ją jako nową kolumnę DataSet:  Nadaj mu nazwę, ponieważ spowoduje to również dodanie do niego Trainer. `estimator`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="f4d2c-289">Dodaj następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="f4d2c-290">Szacowania do przetwarzania obrazów używa wstępnie przeszkolonego featurizers [sieci neuronowych (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) do wyodrębniania funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="f4d2c-291">W przypadku głębokiej sieci neuronowych można dostosować obrazy do oczekiwanego formatu sieci.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="f4d2c-292">Jest to powód użycia kilku przekształceń obrazu w celu uzyskania danych obrazu w oczekiwanej postaci modelu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="f4d2c-293">Obrazy `LoadImages`transformacji są ładowane w pamięci jako typ mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="f4d2c-294">`ResizeImages` Transformacja zmienia rozmiar obrazów, ponieważ wstępnie szkolony model ma zdefiniowaną szerokość i wysokość obrazu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="f4d2c-295">`ExtractPixels` Transformacja wyodrębnia piksele z obrazów wejściowych i konwertuje je na wektor liczbowy.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="f4d2c-296">Dodaj te przekształcenia obrazu jako kolejne wiersze kodu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="f4d2c-297">Jest to wygodna metoda `TensorFlow` umożliwiająca załadowanie modelu, a następnie utworzenie `TensorFlowEstimator` elementu using `ScoreTensorFlowModel`. `LoadTensorFlowModel`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="f4d2c-298">Wyodrębnione dane wyjściowe `Inception model`(funkcje `softmax2_pre_activation`obrazu) i oceniają zestaw danych przy użyciu wstępnie nauczonego `TensorFlow` modelu. `ScoreTensorFlowModel`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="f4d2c-299">`softmax2_pre_activation`ułatwia modelowi określenie, do której klasy należą obrazy.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="f4d2c-300">`softmax2_pre_activation`Zwraca prawdopodobieństwo dla każdej z kategorii obrazu, a wszystkie te prawdopodobieństwo muszą mieć wartość 1.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="f4d2c-301">Przyjęto założenie, że obraz będzie należeć tylko do jednej kategorii, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="f4d2c-302">Class</span><span class="sxs-lookup"><span data-stu-id="f4d2c-302">Class</span></span>         | <span data-ttu-id="f4d2c-303">Rozkład</span><span class="sxs-lookup"><span data-stu-id="f4d2c-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="f4d2c-304">0,001</span><span class="sxs-lookup"><span data-stu-id="f4d2c-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="f4d2c-305">0,95</span><span class="sxs-lookup"><span data-stu-id="f4d2c-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="f4d2c-306">0,06</span><span class="sxs-lookup"><span data-stu-id="f4d2c-306">0.06</span></span>         |

<span data-ttu-id="f4d2c-307">`TensorFlowTransform` Dołącz`estimator` do z następującym wierszem kodu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="f4d2c-308">Wybierz algorytm szkoleniowy</span><span class="sxs-lookup"><span data-stu-id="f4d2c-308">Choose a training algorithm</span></span>

<span data-ttu-id="f4d2c-309">Aby dodać algorytm szkoleniowy, wywołaj `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` metodę otoki.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="f4d2c-310">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) jest dołączany do `estimator` i akceptuje funkcje obrazu rozpoczęcia `Label` (`softmax2_pre_activation`) i parametry wejściowe, aby poznać dane historyczne.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="f4d2c-311">Dodaj Trainer przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="f4d2c-312">Należy również zmapować `predictedlabel` `predictedlabelvalue`do:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="f4d2c-313">`Fit()` Metoda pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="f4d2c-314">Dopasuj model do zestawu danych szkoleniowych i zwróć przeszkolony model, dodając następujący element jako następny wiersz kodu w `ReuseAndTuneInceptionModel()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="f4d2c-315">Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) udostępnia prognozy dla wielu podanych danych wejściowych dla testu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="f4d2c-316">Przekształć `ReuseAndTuneInceptionModel()`dane, dodając następujący kod do: `Training`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="f4d2c-317">Przekształć dane obrazu i przeprowadź prognozowanie `DataViews` do pary o jednoznacznie określonym typie `IEnumerables` , aby umożliwić wyświetlanie.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="f4d2c-318">`MLContext.CreateEnumerable()` Użyj metody, aby to zrobić, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="f4d2c-319">Dodaj następujący kod, aby wyświetlić dane i przewidywania jako kolejne wiersze `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-319">Add the following code to display your data and predictions as the next lines in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="f4d2c-320">Po wybraniu zestawu prognoz Metoda [szacowania ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :</span><span class="sxs-lookup"><span data-stu-id="f4d2c-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="f4d2c-321">Ocenia model (porównuje wartości przewidywane z rzeczywistym zestawem danych `Labels`).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="f4d2c-322">Zwraca metryki wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="f4d2c-323">Dodaj następujący kod do `ReuseAndTuneInceptionModel()` metody w następnym wierszu:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="f4d2c-324">Następujące metryki są oceniane pod kątem klasyfikacji obrazów:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="f4d2c-325">`Log-loss`-Zobacz [utrata dzienników](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="f4d2c-326">Utrata dziennika powinna być jak najbliżej zera.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="f4d2c-327">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-327">`Per class Log-loss`.</span></span> <span data-ttu-id="f4d2c-328">Dla każdej klasy Dziennik ma być zbliżony do zera, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="f4d2c-329">Użyj poniższego kodu, aby wyświetlić metryki, Udostępnij wyniki, a następnie wykonaj na nich czynności:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="f4d2c-330">Dodaj następujący kod, aby zwrócić przeszkolony model jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="f4d2c-331">Klasyfikowanie obrazów z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="f4d2c-331">Classify images with a loaded model</span></span>

<span data-ttu-id="f4d2c-332">Dodaj następujące wywołanie do `ClassifyImages()` metody jako następny wiersz kodu `Main` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="f4d2c-333">`ClassifyImages()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="f4d2c-334">Odczytywan. Plik TSV do `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="f4d2c-335">Przewiduje klasyfikacje obrazów na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="f4d2c-336">Utwórz metodę, tuż `ReuseAndTuneInceptionModel()` po `PairAndDisplayResults()` metodzie i tuż przed metodą, używając następującego kodu: `ClassifyImages()`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="f4d2c-337">Najpierw Wywołaj `ReadFromTsv()` metodę, aby `IEnumerable<ImageData>` utworzyć klasę, która zawiera w pełni kwalifikowaną ścieżkę dla każdej `ImagePath`z nich.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="f4d2c-338">Ta ścieżka pliku jest potrzebna do sparowania danych i wyników przewidywania.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="f4d2c-339">Należy również przekonwertować klasę `IEnumerable<ImageData>` `IDataView` na wartość, która będzie używana do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="f4d2c-340">Dodaj następujący kod jako następne dwa wiersze w `ClassifyImages()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="f4d2c-341">Podobnie jak w przypadku danych obrazu szkoleniowego, przewidywana jest kategoria danych obrazu testowego przy użyciu metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) modelu.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="f4d2c-342">`ClassifyImages()` Dodaj następujący kod do metody prognoz i `predictions` `IDataView` Przekształć element `IEnumerable` na na potrzeby parowania i Display:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="f4d2c-343">Aby sparować i wyświetlić dane obrazu testu i przewidywania, Dodaj następujący kod, aby wywołać `DisplayResults()` metodę wcześniej utworzoną jako następny wiersz `ClassifyImages()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="f4d2c-344">Klasyfikowanie pojedynczego obrazu z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="f4d2c-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="f4d2c-345">Dodaj następujące wywołanie do `ClassifySingleImage()` metody jako następny wiersz kodu `Main` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="f4d2c-346">`ClassifySingleImage()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="f4d2c-347">`ImageData` Ładuje wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="f4d2c-348">Przewiduje klasyfikację obrazów na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="f4d2c-349">Utwórz metodę, tuż `ClassifyImages()` po `PairAndDisplayResults()` metodzie i tuż przed metodą, używając następującego kodu: `ClassifySingleImage()`</span><span class="sxs-lookup"><span data-stu-id="f4d2c-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="f4d2c-350">Najpierw Utwórz `ImageData` klasę, która zawiera w pełni kwalifikowaną ścieżkę i nazwę pliku obrazu dla jednego `ImagePath`z nich.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="f4d2c-351">Dodaj następujący kod jako następny wiersz w `ClassifySingleImage()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="f4d2c-352">[Klasa PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który wykonuje prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="f4d2c-353">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczej kolumny danych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="f4d2c-354">Przekaż `imageData` do, `PredictionEngine` aby przewidzieć kategorię obrazu, dodając następujący kod do `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="f4d2c-355">Wyświetl wynik przewidywania jako następny wiersz kodu w `ClassifySingleImage()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="f4d2c-356">Wyniki</span><span class="sxs-lookup"><span data-stu-id="f4d2c-356">Results</span></span>

<span data-ttu-id="f4d2c-357">Po wykonaniu poprzednich kroków uruchom aplikację konsolową (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="f4d2c-358">Wyniki powinny wyglądać podobnie do poniższych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="f4d2c-359">Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="f4d2c-360">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="f4d2c-360">Congratulations!</span></span> <span data-ttu-id="f4d2c-361">Pomyślnie skompilowano model uczenia maszynowego na potrzeby klasyfikacji obrazów przez ponowne użycie wstępnie nauczonego `TensorFlow` modelu w ml.NET.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="f4d2c-362">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="f4d2c-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="f4d2c-363">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f4d2c-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f4d2c-364">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="f4d2c-364">Understand the problem</span></span>
> * <span data-ttu-id="f4d2c-365">Ponowne użycie i dostosowanie modelu wstępnie przeszkolonego</span><span class="sxs-lookup"><span data-stu-id="f4d2c-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="f4d2c-366">Klasyfikowanie obrazów z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="f4d2c-366">Classify images with a loaded model</span></span>

<span data-ttu-id="f4d2c-367">Zapoznaj się z przykładem Machine Learning przykładowe repozytorium GitHub, aby poznać rozszerzoną próbkę klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f4d2c-368">dotnet/machinelearning — przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="f4d2c-368">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
