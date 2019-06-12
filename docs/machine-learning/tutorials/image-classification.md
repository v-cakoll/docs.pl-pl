---
title: 'Samouczek: Klasyfikator obraz TensorFlow ponownego próbkowania - transferu uczenia'
description: Dowiedz się, jak ponowne szkolenie modelu TensorFlow Klasyfikacja obrazów przy użyciu transferu uczenia i strukturze ML.NET. Oryginalny model został skonfigurowanych pod kątem klasyfikowania poszczególnych obrazów. Po ponownego trenowania, nowy model organizuje obrazów w ogólne kategorie.
ms.date: 06/12/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 2ad9e71f572cb694897fd12ecbb15da069afe338
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026083"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="86846-105">Samouczek: Ponowne szkolenie TensorFlow klasyfikatora obrazu przy użyciu transferu uczenia i strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="86846-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="86846-106">Dowiedz się, jak ponowne szkolenie modelu TensorFlow classificaton obrazu przy użyciu transferu uczenia i strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="86846-106">Learn how to retrain an image classificaton TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="86846-107">Oryginalny model został skonfigurowanych pod kątem klasyfikowania poszczególnych obrazów.</span><span class="sxs-lookup"><span data-stu-id="86846-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="86846-108">Po ponownego trenowania, nowy model organizuje obrazów w ogólne kategorie.</span><span class="sxs-lookup"><span data-stu-id="86846-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="86846-109">Szkolenie [Klasyfikacja obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelu od podstaw wymaga ustawienie miliony parametry ogromnej ilości danych szkoleniowych etykietami i dużych ilości zasobów obliczeniowych (setki procesorów GPU godzin).</span><span class="sxs-lookup"><span data-stu-id="86846-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="86846-110">Nie tak skuteczne, jak szkolenie modelu niestandardowego od podstaw, transfer uczenia umożliwia skrótów tego procesu poprzez współdziałanie z tysięcy obrazów, a miliony obrazy z etykietami i dość szybko utworzyć dostosowany model (w ciągu godziny na maszynie bez PROCESOR GPU).</span><span class="sxs-lookup"><span data-stu-id="86846-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="86846-111">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="86846-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="86846-112">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="86846-112">Understand the problem</span></span>
> * <span data-ttu-id="86846-113">Ponowne użycie i dostosowywanie wstępnie uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="86846-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="86846-114">Klasyfikowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="86846-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="86846-115">Co to jest uczenie transferu?</span><span class="sxs-lookup"><span data-stu-id="86846-115">What is transfer learning?</span></span>

<span data-ttu-id="86846-116">Co zrobić, jeśli można ponownie użyć modelu, który został już wstępnie przeszkolonych do rozwiązywania podobny problem i ponownie ucz wszystkie lub niektóre z warstw tego modelu, aby pomóc w rozwiązaniu problemu?</span><span class="sxs-lookup"><span data-stu-id="86846-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="86846-117">Ta technika ponownego wykorzystania część już trenowanego modelu, aby utworzyć nowy model jest znany jako [transferu learning](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="86846-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="86846-118">Omówienie przykładowych klasyfikacji obrazów</span><span class="sxs-lookup"><span data-stu-id="86846-118">Image classification sample overview</span></span>

<span data-ttu-id="86846-119">Próbka jest aplikacja konsolowa która używa strukturze ML.NET do tworzenia obrazu klasyfikatora na podstawie wstępnie uczonego modelu do klasyfikowania obrazów z małą ilością danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="86846-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="86846-120">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="86846-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="86846-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="86846-121">Prerequisites</span></span>

* <span data-ttu-id="86846-122">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="86846-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="86846-123">Pakiet Nuget Microsoft.ML 1.0.0</span><span class="sxs-lookup"><span data-stu-id="86846-123">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="86846-124">Pakiet Nuget Microsoft.ML.ImageAnalytics 1.0.0</span><span class="sxs-lookup"><span data-stu-id="86846-124">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="86846-125">Pakiet Nuget Microsoft.ML.TensorFlow 0.12.0</span><span class="sxs-lookup"><span data-stu-id="86846-125">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="86846-126">Katalog zasobów samouczka. Plik ZIP</span><span class="sxs-lookup"><span data-stu-id="86846-126">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="86846-127">Model uczenia maszynowego InceptionV3</span><span class="sxs-lookup"><span data-stu-id="86846-127">The InceptionV3 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="86846-128">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="86846-128">Select the appropriate machine learning task</span></span>

<span data-ttu-id="86846-129">[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzestaw funkcji usługi Machine Learning, która jest revolutionizing zagadnień, takich jak przetwarzanie obrazów i rozpoznawanie mowy.</span><span class="sxs-lookup"><span data-stu-id="86846-129">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="86846-130">Głębokiego uczenia, modele są uczone przy użyciu dużych zestawach [etykietą danych](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych](https://en.wikipedia.org/wiki/Artificial_neural_network) zawierające wiele warstw uczenia.</span><span class="sxs-lookup"><span data-stu-id="86846-130">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="86846-131">Uczenie głębokie:</span><span class="sxs-lookup"><span data-stu-id="86846-131">Deep learning:</span></span>

* <span data-ttu-id="86846-132">Działa lepiej, w niektórych zadań, takich jak przetwarzanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="86846-132">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="86846-133">Wykonuje również na olbrzymich ilościach danych kwoty.</span><span class="sxs-lookup"><span data-stu-id="86846-133">Performs well on huge data amounts.</span></span>

<span data-ttu-id="86846-134">Klasyfikacja obrazów jest typowym zadaniem usługi Machine Learning, która umożliwia nam automatycznego klasyfikowania obrazów do wielu kategorii, takich jak:</span><span class="sxs-lookup"><span data-stu-id="86846-134">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="86846-135">Wykrywanie ludzkich twarzy na obrazie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="86846-135">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="86846-136">Wykrywanie koty a psy.</span><span class="sxs-lookup"><span data-stu-id="86846-136">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="86846-137">Lub tak jak w następujących obrazów, określania, czy obraz jest strumieniowe żywności, zabawki lub urządzenie:</span><span class="sxs-lookup"><span data-stu-id="86846-137">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="86846-138">![Obraz pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![obrazu należy sobie zdawać sprawę Kubuś](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![tostera obrazu](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="86846-138">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="86846-139">Poprzednie obrazy należą do Wikimedia Commons i są określane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="86846-139">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="86846-140">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="86846-140">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="86846-141">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="86846-141">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="86846-142">"193px-Broodrooster.jpg" przez [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -własnej pracy, CC BY SA 3.0 https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="86846-142">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="86846-143">Transfer uczenia obejmuje kilka strategii, takie jak *Ponowne szkolenie wszystkie warstwy* i *przedostatni warstwy*.</span><span class="sxs-lookup"><span data-stu-id="86846-143">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="86846-144">W tym samouczku zostanie wyjaśnić oraz pokazano, jak używać *strategii przedostatni warstwy*.</span><span class="sxs-lookup"><span data-stu-id="86846-144">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="86846-145">*Strategii przedostatni warstwy* ponownie używa modelu, który jest już został wstępnie skonfigurowanych pod kątem rozwiązania konkretnego problemu.</span><span class="sxs-lookup"><span data-stu-id="86846-145">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="86846-146">Strategia retrains następnie ostatnią warstwą tego modelu, aby rozwiązać nowy problem.</span><span class="sxs-lookup"><span data-stu-id="86846-146">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="86846-147">Ponowne używanie wstępnie uczonego modelu w ramach nowego modelu zapisze znaczną ilość czasu i zasobów.</span><span class="sxs-lookup"><span data-stu-id="86846-147">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="86846-148">Model klasyfikacji obrazów ponownie używa [modelu powstania](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), model rozpoznawania popularnego obrazu skonfigurowanych pod kątem w `ImageNet` zestawu danych, gdzie próbuje klasyfikowania cały TensorFlow model obrazy na tysiąc klasy, takie jak " Ogólny","Jersey"i"Zmywarki".</span><span class="sxs-lookup"><span data-stu-id="86846-148">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="86846-149">`Inception v3 model` Mogą być klasyfikowane jako [głębokiego splotowe sieci neuronowe](https://en.wikipedia.org/wiki/Convolutional_neural_network) i mogą osiągnąć rozsądną wydajność na twardych visual zadań rozpoznawania, dopasowania lub przekroczenie ludzi wydajności w niektórych domen.</span><span class="sxs-lookup"><span data-stu-id="86846-149">The `Inception v3 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="86846-150">Model/algorytm został opracowany przez wielu pracowników naukowo-badawczych i oparta na oryginalny dokument: ["Przemyślenie architektury powstania dla przetwarzania obrazów" przez Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="86846-150">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="86846-151">Ponieważ `Inception model` została już wstępnie przeszkolonych na tysiącach różnych obrazów, zawiera on [obrazu funkcji](https://en.wikipedia.org/wiki/Feature_(computer_vision)) służące do identyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-151">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="86846-152">Niższych warstwach obrazu w funkcji rozpoznaje proste funkcje (na przykład krawędzie) i wyższe warstwy rozpoznaje bardziej złożonych funkcji (np. kształty).</span><span class="sxs-lookup"><span data-stu-id="86846-152">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="86846-153">Ostatnia warstwa jest uczony względem znacznie mniejszy zestaw danych, ponieważ trwa uruchamianie za pomocą uczonego modelu sprzed i już zrozumienie sposobu klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="86846-153">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="86846-154">Jako model umożliwia klasyfikowanie więcej niż dwie kategorie, jest to przykład [klasyfikatora wieloklasowej](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="86846-154">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="86846-155">`TensorFlow` Popularne uczenia głębokiego i zestaw narzędzi do usługi machine learning umożliwia szkolenia głębokich sieciach neuronowych (i ogólne obliczeń numerycznych), która jest implementowany jako `transformer` w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="86846-155">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="86846-156">W tym samouczku jest używana do ponownego użycia `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="86846-156">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="86846-157">Jak pokazano na poniższym diagramie, możesz dodać odwołania do pakietów NuGet w strukturze ML.NET w aplikacjach platformy .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86846-157">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="86846-158">Dzieje się w tle, strukturze ML.NET obejmuje i odwołuje się do macierzystych `TensorFlow` biblioteki, który pozwala napisać kod, który ładuje, istniejące skonfigurowanych pod kątem `TensorFlow` pliku modelu do oceniania.</span><span class="sxs-lookup"><span data-stu-id="86846-158">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Przekształcanie TensorFlow diagram Arch strukturze ML.NET](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="86846-160">`Inception model` Jest uczony do klasyfikowania obrazów do tysięcy kategorii, ale należy do klasyfikowania obrazów w mniejszy zestaw kategorii i tylko te kategorie.</span><span class="sxs-lookup"><span data-stu-id="86846-160">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="86846-161">Wprowadź `transfer` wchodzi w skład `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="86846-161">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="86846-162">W przypadku transferu `Inception model`firmy możliwość rozpoznaje i klasyfikowania obrazów do nowej kategorii ograniczone klasyfikatora obrazu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="86846-162">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="86846-163">Zamierzasz Ponowne szkolenie ostatnią warstwą modelu przy użyciu zestawu trzy kategorie:</span><span class="sxs-lookup"><span data-stu-id="86846-163">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="86846-164">Żywność</span><span class="sxs-lookup"><span data-stu-id="86846-164">Food</span></span>
* <span data-ttu-id="86846-165">Zabawki</span><span class="sxs-lookup"><span data-stu-id="86846-165">Toy</span></span>
* <span data-ttu-id="86846-166">Urządzenia</span><span class="sxs-lookup"><span data-stu-id="86846-166">Appliance</span></span>

<span data-ttu-id="86846-167">Korzysta z warstwą [algorytmu regresji logistycznej wielomian](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) możliwie jak najszybciej odnaleźć prawidłową kategorię.</span><span class="sxs-lookup"><span data-stu-id="86846-167">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="86846-168">Ten algorytm klasyfikuje przy użyciu prawdopodobieństwa, aby określić odpowiedzi, zapewniając jednej wartości do odpowiedniej kategorii i wartość zero do innych osób.</span><span class="sxs-lookup"><span data-stu-id="86846-168">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="86846-169">DataSet</span><span class="sxs-lookup"><span data-stu-id="86846-169">DataSet</span></span>

<span data-ttu-id="86846-170">Istnieją dwa źródła danych: `.tsv` plików i pliki obrazów.</span><span class="sxs-lookup"><span data-stu-id="86846-170">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="86846-171">`tags.tsv` Plik zawiera dwie kolumny: pierwszy z nich jest zdefiniowany jako `ImagePath` , a drugi jest `Label` odpowiadający obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-171">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="86846-172">Następujący przykład pliku nie ma wiersz nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="86846-172">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="86846-173">Szkolenia i testowania obrazów znajdują się w folderach zasoby, które, konieczne będzie pobranie w formie pliku zip.</span><span class="sxs-lookup"><span data-stu-id="86846-173">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="86846-174">Te obrazy należy do Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="86846-174">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="86846-175">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych nośników.*</span><span class="sxs-lookup"><span data-stu-id="86846-175">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="86846-176">Pobrane 10:48, 17 października 2018 r. od:</span><span class="sxs-lookup"><span data-stu-id="86846-176">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="86846-177">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="86846-177">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="86846-178">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="86846-178">Create a project</span></span>

1. <span data-ttu-id="86846-179">Tworzenie **aplikacji konsoli .NET Core** o nazwie "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="86846-179">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="86846-180">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="86846-180">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="86846-181">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="86846-181">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="86846-182">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="86846-182">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="86846-183">Kliknij pozycję **wersji** listę rozwijaną, wybierz opcję **1.0.0** pakietu na liście, a następnie wybierz pozycję **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="86846-183">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="86846-184">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="86846-184">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="86846-185">Powtórz te kroki dla **1.0.0 Microsoft.ML.ImageAnalytics** i **Microsoft.ML.TensorFlow v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="86846-185">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="86846-186">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="86846-186">Prepare your data</span></span>

1. <span data-ttu-id="86846-187">Pobierz [pliku zip projektu zasobów katalogu](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)i Rozpakuj go.</span><span class="sxs-lookup"><span data-stu-id="86846-187">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="86846-188">Kopiuj `assets` katalogu do usługi *TransferLearningTF* katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="86846-188">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="86846-189">Ten katalog i jego podkatalogach zawierać plików danych i pomocy technicznej (z wyjątkiem powstania modelu, który można pobrać i dodać w następnym kroku) potrzebne w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="86846-189">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="86846-190">Pobierz [modelu powstania](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i Rozpakuj go.</span><span class="sxs-lookup"><span data-stu-id="86846-190">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="86846-191">Skopiuj zawartość `inception5h` katalogu po prostu rozpakowano do Twojej *TransferLearningTF* projektu `assets\inputs-train\inception` katalogu.</span><span class="sxs-lookup"><span data-stu-id="86846-191">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="86846-192">Ten katalog zawiera model i dodatkowe pliki obsługi potrzebne w tym samouczku, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="86846-192">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Zawartość katalogu powstania](./media/image-classification/inception-files.png)

5. <span data-ttu-id="86846-194">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu zasobów i podkatalogi i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="86846-194">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="86846-195">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="86846-195">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="86846-196">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="86846-196">Create classes and define paths</span></span>

<span data-ttu-id="86846-197">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="86846-197">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="86846-198">Utwórz globalne pola do przechowywania ścieżek do różnych zasobów i zmiennych globalnych `LabelTokey`,`ImageReal`, i `PredictedLabelValue`:</span><span class="sxs-lookup"><span data-stu-id="86846-198">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="86846-199">`_assetsPath` zawiera ścieżkę do zasobów.</span><span class="sxs-lookup"><span data-stu-id="86846-199">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="86846-200">`_trainTagsTsv` ma ścieżkę do pliku tsv szkolenia obrazu danych tagów.</span><span class="sxs-lookup"><span data-stu-id="86846-200">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="86846-201">`_predictTagsTsv` ma ścieżkę do pliku tsv prognozowania obrazu danych tagów.</span><span class="sxs-lookup"><span data-stu-id="86846-201">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="86846-202">`_trainImagesFolder` zawiera ścieżkę do obrazów użytych do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-202">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="86846-203">`_predictImagesFolder` zawiera ścieżkę do obrazów do sklasyfikowania trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-203">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="86846-204">`_inceptionPb` zawiera ścieżkę do wstępnie przeszkolonych powstania modelu, który ma zostać ponownie użyte do Ponowne szkolenie modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-204">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="86846-205">`_inputImageClassifierZip` ma ścieżkę, gdzie uczony model jest ładowany z.</span><span class="sxs-lookup"><span data-stu-id="86846-205">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="86846-206">`_outputImageClassifierZip` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-206">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="86846-207">`LabelTokey` jest `Label` wartość mapowane z kluczem.</span><span class="sxs-lookup"><span data-stu-id="86846-207">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="86846-208">`ImageReal`  to kolumny zawierającej wartość przewidywane obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-208">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="86846-209">`PredictedLabelValue` to kolumny zawierającej wartość przewidywane etykiety.</span><span class="sxs-lookup"><span data-stu-id="86846-209">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="86846-210">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:</span><span class="sxs-lookup"><span data-stu-id="86846-210">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="86846-211">Utwórz niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="86846-211">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="86846-212">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="86846-212">Add a new class to your project:</span></span>

1. <span data-ttu-id="86846-213">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="86846-213">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="86846-214">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="86846-214">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="86846-215">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="86846-215">Then, select the **Add** button.</span></span>

    <span data-ttu-id="86846-216">*ImageData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="86846-216">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="86846-217">Dodaj następujący kod `using` instrukcji na górze *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="86846-217">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="86846-218">Usuń istniejącą definicję klasy i Dodaj następujący kod dla `ImageData` klasy *ImageData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="86846-218">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="86846-219">`ImageData` Klasa danych obrazu wejściowego i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="86846-219">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="86846-220">`ImagePath` zawiera nazwę pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-220">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="86846-221">`Label` zawiera wartość dla etykiety obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-221">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="86846-222">Dodaj nową klasę do projektu, aby `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="86846-222">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="86846-223">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="86846-223">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="86846-224">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="86846-224">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="86846-225">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="86846-225">Then, select the **Add** button.</span></span>

    <span data-ttu-id="86846-226">*ImagePrediction.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="86846-226">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="86846-227">Usuń oba `System.Collections.Generic` i `System.Text` `using` instrukcji na górze *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="86846-227">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="86846-228">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma `ImagePrediction` klasy do *ImagePrediction.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="86846-228">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="86846-229">`ImagePrediction` jest klasą prognozowania obrazu i zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="86846-229">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="86846-230">`Score` zawiera stopień ufności klasyfikacji danego obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-230">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="86846-231">`PredictedLabelValue` zawiera wartość etykiety klasyfikacji przewidywane obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-231">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="86846-232">`ImagePrediction` Klasa służy do prognozowania po wyszkoliła modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-232">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="86846-233">Ma ona `string` (`ImagePath`) dla ścieżki obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-233">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="86846-234">`Label` Służy do ponownego użycia i ponowne szkolenie modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-234">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="86846-235">`PredictedLabelValue` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="86846-235">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="86846-236">W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="86846-236">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="86846-237">[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-237">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="86846-238">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="86846-238">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="86846-239">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="86846-239">Initialize variables in Main</span></span>

<span data-ttu-id="86846-240">Inicjowanie `mlContext` zmiennej za pomocą nowego wystąpienia `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="86846-240">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="86846-241">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-241">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="86846-242">Tworzenie struktury dla parametrów domyślnych</span><span class="sxs-lookup"><span data-stu-id="86846-242">Create a struct for default parameters</span></span>

<span data-ttu-id="86846-243">Model powstania ma kilka domyślnych parametrów, które musisz przekazać.</span><span class="sxs-lookup"><span data-stu-id="86846-243">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="86846-244">Tworzenie struktury do mapowania wartości domyślne parametrów do przyjaznych nazw następującym kodem, zaraz po `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-244">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="86846-245">Utwórz metodę narzędzie wyświetlania</span><span class="sxs-lookup"><span data-stu-id="86846-245">Create a display utility method</span></span>

<span data-ttu-id="86846-246">Ponieważ więcej niż jeden raz będą wyświetlane dane obrazu i powiązane prognoz, należy utworzyć metody wyświetlania narzędzia do obsługi wyświetlania obrazów i przewidywania wyników.</span><span class="sxs-lookup"><span data-stu-id="86846-246">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="86846-247">`DisplayResults()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="86846-247">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="86846-248">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="86846-248">Displays the predicted results.</span></span>

<span data-ttu-id="86846-249">Tworzenie `DisplayResults()` metody tuż za `InceptionSettings` struktury, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-249">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="86846-250">`Transform()` Metoda wypełnione `ImagePath` w `ImagePrediction` oraz przewidywany pola.</span><span class="sxs-lookup"><span data-stu-id="86846-250">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="86846-251">W trakcie procesu strukturze ML.NET każdego składnika dodaje kolumny, a dzięki temu można łatwo wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="86846-251">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="86846-252">Wywołasz `DisplayResults()` metody w dwóch obraz metody klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="86846-252">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="86846-253">Utwórz metodę narzędzie plik tsv</span><span class="sxs-lookup"><span data-stu-id="86846-253">Create a .tsv file utility method</span></span>

<span data-ttu-id="86846-254">`ReadFromTsv()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="86846-254">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="86846-255">Odczytuje dane obrazu `tags.tsv` pliku.</span><span class="sxs-lookup"><span data-stu-id="86846-255">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="86846-256">Dodaje ścieżkę pliku do nazwy pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-256">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="86846-257">Ładuje dane plików do elementu IEnumerable`ImageData` obiektu.</span><span class="sxs-lookup"><span data-stu-id="86846-257">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="86846-258">Tworzenie `ReadFromTsv()` metody tuż za `PairAndDisplayResults()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-258">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="86846-259">Poniższy kod zostanie przetworzony za pośrednictwem `tags.tsv` plik, aby dodać ścieżkę pliku do nazwy pliku obrazu dla `ImagePath` właściwości, a następnie załaduj i `Label` do `ImageData` obiektu.</span><span class="sxs-lookup"><span data-stu-id="86846-259">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="86846-260">Dodaj ją jako pierwszy wiersz `ReadFromTsv()` metody.</span><span class="sxs-lookup"><span data-stu-id="86846-260">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="86846-261">Konieczne jest w pełni kwalifikowana ścieżka do wyświetlenia wyników przewidywań.</span><span class="sxs-lookup"><span data-stu-id="86846-261">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="86846-262">Istnieją trzy główne pojęcia w strukturze ML.NET: [Dane](../resources/glossary.md#data), [transformatory](../resources/glossary.md#transformer), i [aplikacjom](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="86846-262">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="86846-263">Ponowne użycie i dostosowywanie wstępnie uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="86846-263">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="86846-264">Dodaj następujące wywołanie do `ReuseAndTuneInceptionModel()`metodę jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-264">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="86846-265">`ReuseAndTuneInceptionModel()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="86846-265">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="86846-266">Służy do ładowania danych</span><span class="sxs-lookup"><span data-stu-id="86846-266">Loads the data</span></span>
* <span data-ttu-id="86846-267">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="86846-267">Extracts and transforms the data.</span></span>
* <span data-ttu-id="86846-268">Ocenia TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="86846-268">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="86846-269">Dostraja (retrains) modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-269">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="86846-270">Wyświetla wyniki modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-270">Displays model results.</span></span>
* <span data-ttu-id="86846-271">Oblicza modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-271">Evaluates the model.</span></span>
* <span data-ttu-id="86846-272">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-272">Returns the model.</span></span>

<span data-ttu-id="86846-273">Tworzenie `ReuseAndTuneInceptionModel()` metody tuż za `InceptionSettings` struktury i tuż przed `DisplayResults()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-273">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="86846-274">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="86846-274">Load the data</span></span>

<span data-ttu-id="86846-275">Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="86846-275">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="86846-276">`IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe).</span><span class="sxs-lookup"><span data-stu-id="86846-276">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="86846-277">Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="86846-277">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="86846-278">Ładowanie danych przy użyciu `MLContext.Data.LoadFromTextFile` otoki.</span><span class="sxs-lookup"><span data-stu-id="86846-278">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="86846-279">Dodaj następujący kod w następnym wierszu `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-279">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="86846-280">Wyodrębnianie funkcji i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="86846-280">Extract Features and transform the data</span></span>

<span data-ttu-id="86846-281">Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="86846-281">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="86846-282">Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.</span><span class="sxs-lookup"><span data-stu-id="86846-282">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="86846-283">Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) danych, a kiedy dotyczących głębokich sieciach neuronowych należy dostosować obrazy do formatu oczekiwanego przez sieć.</span><span class="sxs-lookup"><span data-stu-id="86846-283">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="86846-284">Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="86846-284">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="86846-285">Po uczenie i Ewaluacja Prognozowanie za pomocą **etykiety** wartości w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="86846-285">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="86846-286">Ponieważ używasz wstępnie przeszkolonych modelu mapowanie pól do nowego modelu za pomocą [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="86846-286">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="86846-287">Ta metoda przekształca `Label` do klucza typu liczbowego (`LabelTokey`) kolumny i dodaj ją jako nowe kolumny zestawu danych:  Nazwij to `estimator` jako trainer będzie również dodać do niego.</span><span class="sxs-lookup"><span data-stu-id="86846-287">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="86846-288">Dodaj kolejny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-288">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="86846-289">Obraz przetwarzania używa narzędzie do szacowania wstępnie przeszkolonych [głębokiego Network(DNN) neuronowych](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers do wyodrębnienia funkcji.</span><span class="sxs-lookup"><span data-stu-id="86846-289">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="86846-290">Podczas zajmowania się sieci neuronowej, można przystosować obrazy w formacie oczekiwanego sieci.</span><span class="sxs-lookup"><span data-stu-id="86846-290">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="86846-291">Jest to przyczyną kilku przekształcenia obraz umożliwia pobieranie danych obrazu do postaci oczekiwanej modelu:</span><span class="sxs-lookup"><span data-stu-id="86846-291">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="86846-292">`LoadImages`Przekształcanie obrazów są ładowane do pamięci jako typ mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="86846-292">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="86846-293">`ResizeImages` Przekształcenie zmieni rozmiar obrazów, zgodnie z wstępnie przeszkolonych model nie ma zdefiniowanych danych wejściowych szerokość i wysokość obrazu.</span><span class="sxs-lookup"><span data-stu-id="86846-293">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="86846-294">`ExtractPixels` Przekształcenie wyodrębnia pikseli z obrazy wejściowe i konwertuje je do wektora liczbowych.</span><span class="sxs-lookup"><span data-stu-id="86846-294">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="86846-295">Dodaj te przekształcenia obrazu jako następnej linii kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-295">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="86846-296">`LoadTensorFlowModel` Jest to wygodna metoda, która umożliwia `TensorFlow` modelu, należy załadować raz, a następnie tworzy `TensorFlowEstimator` przy użyciu `ScoreTensorFlowModel`.</span><span class="sxs-lookup"><span data-stu-id="86846-296">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="86846-297">`ScoreTensorFlowModel` Wyodrębnia określone dane wyjściowe ( `Inception model`firmy obrazu funkcji `softmax2_pre_activation`) i ocenia zestawu danych za pomocą wstępnie przeszkolonych `TensorFlow` modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-297">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="86846-298">`softmax2_pre_activation` ułatwia utrzymanie modelu o określenie, które klasy obrazów należy do.</span><span class="sxs-lookup"><span data-stu-id="86846-298">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="86846-299">`softmax2_pre_activation` Zwraca prawdopodobieństwo dla każdej z kategorii w przypadku obrazu i wszystkich tych prawdopodobieństw, należy dodać do 1.</span><span class="sxs-lookup"><span data-stu-id="86846-299">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="86846-300">Przyjęto założenie, że obraz będzie należał do tylko jednej kategorii, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="86846-300">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="86846-301">Class</span><span class="sxs-lookup"><span data-stu-id="86846-301">Class</span></span>         | <span data-ttu-id="86846-302">Prawdopodobieństwo</span><span class="sxs-lookup"><span data-stu-id="86846-302">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="86846-303">0.001</span><span class="sxs-lookup"><span data-stu-id="86846-303">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="86846-304">0.95</span><span class="sxs-lookup"><span data-stu-id="86846-304">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="86846-305">0,06</span><span class="sxs-lookup"><span data-stu-id="86846-305">0.06</span></span>         |

<span data-ttu-id="86846-306">Dołącz `TensorFlowTransform` do `estimator` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-306">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="86846-307">Wybieranie algorytmu szkolenia</span><span class="sxs-lookup"><span data-stu-id="86846-307">Choose a training algorithm</span></span>

<span data-ttu-id="86846-308">Aby dodać uczenie algorytmu, należy wywołać `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` metody otoki.</span><span class="sxs-lookup"><span data-stu-id="86846-308">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="86846-309">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) jest dołączany do `estimator` i akceptuje funkcji obraz powstania (`softmax2_pre_activation`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="86846-309">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="86846-310">Należy dodać instruktora następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="86846-310">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="86846-311">Musisz również zmapować `predictedlabel` do `predictedlabelvalue`:</span><span class="sxs-lookup"><span data-stu-id="86846-311">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="86846-312">`Fit()` Metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.</span><span class="sxs-lookup"><span data-stu-id="86846-312">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="86846-313">Dopasowania modelu do zestawu danych szkoleniowych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-313">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="86846-314">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda wykonuje prognozy dla wielu podać wiersze danych wejściowych zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="86846-314">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="86846-315">Przekształcanie `Training` danych przez dodanie poniższego kodu `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="86846-315">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="86846-316">Konwertuj obraz danych i prognozowania `DataViews` do silnie typizowanych `IEnumerables` parą do wyświetlenia łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="86846-316">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="86846-317">Użyj `MLContext.CreateEnumerable()` metodę, aby to zrobić, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-317">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="86846-318">Wywołaj `DisplayResults()` metodę w celu wyświetlenia danych i prognozy w następnym wierszu `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-318">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="86846-319">Po utworzeniu prognozowania ustawiona, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="86846-319">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="86846-320">Ocenia modelu (porównuje przewidywane wartości z rzeczywistych zestawu danych `Labels`).</span><span class="sxs-lookup"><span data-stu-id="86846-320">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="86846-321">Zwraca wartość metryki wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-321">Returns the model performance metrics.</span></span>

<span data-ttu-id="86846-322">Dodaj następujący kod do `ReuseAndTuneInceptionModel()` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="86846-322">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="86846-323">Następujące metryki są oceniane pod kątem Klasyfikacja obrazów:</span><span class="sxs-lookup"><span data-stu-id="86846-323">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="86846-324">`Log-loss` — zobacz [utraty dziennika](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="86846-324">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="86846-325">Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="86846-325">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="86846-326">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="86846-326">`Per class Log-loss`.</span></span> <span data-ttu-id="86846-327">Chcesz na klasy utraty dziennika być maksymalnie zbliżone do zera, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="86846-327">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="86846-328">Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:</span><span class="sxs-lookup"><span data-stu-id="86846-328">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="86846-329">Dodaj następujący kod, aby zwrócić uczonego modelu w postaci następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="86846-329">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="86846-330">Klasyfikowanie obrazów za pomocą załadować modelu</span><span class="sxs-lookup"><span data-stu-id="86846-330">Classify images with a loaded model</span></span>

<span data-ttu-id="86846-331">Dodaj następujące wywołanie do `ClassifyImages()` metodę jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-331">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="86846-332">`ClassifyImages()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="86846-332">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="86846-333">Odczytuje. Plik TSV do `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="86846-333">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="86846-334">Prognozuje klasyfikacji obrazów na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="86846-334">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="86846-335">Tworzenie `ClassifyImages()` metody tuż za `ReuseAndTuneInceptionModel()` metody i tuż przed `PairAndDisplayResults()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-335">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="86846-336">Po pierwsze wywołanie `ReadFromTsv()` metodę w celu utworzenia `IEnumerable<ImageData>` klasę, która zawiera w pełni kwalifikowana ścieżka dla każdego `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="86846-336">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="86846-337">Należy tę ścieżkę pliku, aby sparować wyniki danych i prognozowania.</span><span class="sxs-lookup"><span data-stu-id="86846-337">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="86846-338">Musisz też przekonwertować `IEnumerable<ImageData>` klasy `IDataView` używanego do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="86846-338">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="86846-339">Dodaj następujący kod jako następne dwa wiersze w `ClassifyImages()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-339">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="86846-340">Tak jak poprzednio w przypadku danych obrazu szkolenia, przewidywanie kategorii testów obraz dane za pomocą [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) przekazanego do metody w modelu.</span><span class="sxs-lookup"><span data-stu-id="86846-340">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="86846-341">Dodaj następujący kod do `ClassifyImages()` metodę dla prognoz i przekonwertować `predictions` `IDataView` do `IEnumerable` parowania i wyświetlania:</span><span class="sxs-lookup"><span data-stu-id="86846-341">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="86846-342">Sparuj i wyświetlanie danych obrazu testu i prognozy, Dodaj następujący kod do wywoływania `DisplayResults()` metoda wcześniej utworzony w następnym wierszu `ClassifyImages()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-342">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="86846-343">Klasyfikowanie pojedynczy obraz z modelem załadowany</span><span class="sxs-lookup"><span data-stu-id="86846-343">Classify a single image with a loaded model</span></span>

<span data-ttu-id="86846-344">Dodaj następujące wywołanie do `ClassifySingleImage()` metodę jako następnego wiersza kodu w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-344">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="86846-345">`ClassifySingleImage()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="86846-345">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="86846-346">Ładunki `ImageData` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="86846-346">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="86846-347">Prognozuje Klasyfikacja obrazów na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="86846-347">Predicts image classification based on test data.</span></span>

<span data-ttu-id="86846-348">Tworzenie `ClassifySingleImage()` metody tuż za `ClassifyImages()` metody i tuż przed `PairAndDisplayResults()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="86846-348">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="86846-349">Najpierw utwórz `ImageData` klasę, która zawiera pełną ścieżkę i obrazu nazwę pliku dla pojedynczego `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="86846-349">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="86846-350">Dodaj następujący kod jako dalej wiersze w `ClassifySingleImage()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-350">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="86846-351">[Klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, która wykonuje prognozy w pojedynczym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="86846-351">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="86846-352">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognozę na pojedynczej kolumny danych.</span><span class="sxs-lookup"><span data-stu-id="86846-352">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="86846-353">Przekaż `imageData` do `PredictionEngine` do prognozowania Kategoria obrazu, dodając następujący kod do `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="86846-353">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="86846-354">Wyświetl wyniki prognozowania jako następnego wiersza kodu w `ClassifySingleImage()` metody:</span><span class="sxs-lookup"><span data-stu-id="86846-354">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="86846-355">Wyniki</span><span class="sxs-lookup"><span data-stu-id="86846-355">Results</span></span>

<span data-ttu-id="86846-356">Po wykonaniu poprzednich kroków, uruchom aplikację konsoli (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="86846-356">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="86846-357">Wyniki powinny być podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="86846-357">Your results should be similar to the following output.</span></span>  <span data-ttu-id="86846-358">Może zostać wyświetlony, ostrzeżenia i przetwarzanie komunikatów, ale te komunikaty zostały usunięte z następujące wyniki dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="86846-358">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="86846-359">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="86846-359">Congratulations!</span></span> <span data-ttu-id="86846-360">Teraz pomyślnie dołączeniu model uczenia maszynowego klasyfikacji obrazów na podstawie wstępnie przeszkolonych `TensorFlow` model w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="86846-360">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="86846-361">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="86846-361">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="86846-362">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="86846-362">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="86846-363">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="86846-363">Understand the problem</span></span>
> * <span data-ttu-id="86846-364">Ponowne użycie i dostosowywanie wstępnie uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="86846-364">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="86846-365">Klasyfikowanie obrazów za pomocą załadować modelu</span><span class="sxs-lookup"><span data-stu-id="86846-365">Classify images with a loaded model</span></span>

<span data-ttu-id="86846-366">Zapoznaj się z repozytorium GitHub przykładów uczenia maszynowego można eksplorować przykładową klasyfikacji obrazów rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="86846-366">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="86846-367">repozytorium GitHub machinelearning-DotNet-samples</span><span class="sxs-lookup"><span data-stu-id="86846-367">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
