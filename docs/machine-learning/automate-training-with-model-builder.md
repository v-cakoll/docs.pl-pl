---
title: Co to jest Model Builder i jak działa?
description: Jak używać ML.NET Model Builder do automatycznego uczenia modelu uczenia maszynowego
ms.date: 01/07/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: cff4601843ec9ca7201ea7dbdbfbcfa18f50e46e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399225"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="f49f8-103">Co to jest Model Builder i jak działa?</span><span class="sxs-lookup"><span data-stu-id="f49f8-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="f49f8-104">ML.NET Model Builder to intuicyjne graficzne rozszerzenie programu Visual Studio do tworzenia, uczenia i wdrażania niestandardowych modeli uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="f49f8-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="f49f8-105">Program Model Builder używa automatycznego uczenia maszynowego (AutoML) do eksplorowania różnych algorytmów i ustawień uczenia maszynowego, aby ułatwić znalezienie tego, który najlepiej pasuje do twojego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f49f8-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="f49f8-106">Nie potrzebujesz wiedzy o uczeniu maszynowym, aby korzystać z modelu Konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f49f8-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="f49f8-107">Wszystko, czego potrzebujesz, to niektóre dane i problem do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f49f8-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="f49f8-108">Konstruktor modeli generuje kod, aby dodać model do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="f49f8-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animacja interfejsu użytkownika rozszerzenia programu Model Builder Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="f49f8-110">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="f49f8-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="f49f8-111">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="f49f8-111">Scenarios</span></span>

<span data-ttu-id="f49f8-112">Można przynieść wiele różnych scenariuszy do konstruktora modeli, aby wygenerować model uczenia maszynowego dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f49f8-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="f49f8-113">Scenariusz jest opistypu przewidywania, które chcesz zrobić przy użyciu danych.</span><span class="sxs-lookup"><span data-stu-id="f49f8-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="f49f8-114">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f49f8-114">For example:</span></span>

- <span data-ttu-id="f49f8-115">przewidywanie przyszłej wielkości sprzedaży produktów na podstawie historycznych danych sprzedaży</span><span class="sxs-lookup"><span data-stu-id="f49f8-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="f49f8-116">klasyfikować nastroje jako pozytywne lub negatywne na podstawie opinii klientów</span><span class="sxs-lookup"><span data-stu-id="f49f8-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="f49f8-117">wykryć, czy transakcja bankowa jest oszukańcza</span><span class="sxs-lookup"><span data-stu-id="f49f8-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="f49f8-118">kierowanie problemów z opiniami klientów do właściwego zespołu w twojej firmie</span><span class="sxs-lookup"><span data-stu-id="f49f8-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="f49f8-119">Który scenariusz uczenia maszynowego jest dla mnie odpowiedni?</span><span class="sxs-lookup"><span data-stu-id="f49f8-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="f49f8-120">W Konstruktorze modeli należy wybrać scenariusz.</span><span class="sxs-lookup"><span data-stu-id="f49f8-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="f49f8-121">Typ scenariusza zależy od typu przewidywania, który próbujesz zrobić.</span><span class="sxs-lookup"><span data-stu-id="f49f8-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="f49f8-122">Przewidywanie kategorii (gdy istnieją tylko dwie kategorie)</span><span class="sxs-lookup"><span data-stu-id="f49f8-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="f49f8-123">Klasyfikacja binarna służy do kategoryzowania danych na dwie kategorie (tak/nie; pass/fail; true/false; positive/negative).</span><span class="sxs-lookup"><span data-stu-id="f49f8-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagram przedstawiający przykłady klasyfikacji binarnej, w tym wykrywanie oszustw, ograniczanie ryzyka i sprawdzanie aplikacji](media/binary-classification-examples.png)

<span data-ttu-id="f49f8-125">Analiza tonacji może służyć do przewidywania pozytywnych lub negatywnych nastrojów opinii klientów.</span><span class="sxs-lookup"><span data-stu-id="f49f8-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="f49f8-126">Jest to przykład zadania uczenia maszynowego klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="f49f8-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="f49f8-127">Jeśli scenariusz wymaga klasyfikacji na dwie kategorie, można użyć tego szablonu z własnym zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="f49f8-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="f49f8-128">Przewidywanie kategorii (gdy istnieją trzy lub więcej kategorii)</span><span class="sxs-lookup"><span data-stu-id="f49f8-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="f49f8-129">Klasyfikacja wieloklasowa może służyć do kategoryzowania danych na trzy lub więcej klas.</span><span class="sxs-lookup"><span data-stu-id="f49f8-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Przykłady klasyfikacji wieloklasowej, w tym klasyfikacji dokumentów i produktów, routingu biletów pomocy technicznej i priorytetyzacji problemów klienta](media/multiclass-classification-examples.png)

<span data-ttu-id="f49f8-131">Klasyfikacja problemów może służyć do kategoryzowania opinii klientów (na przykład w usłudze GitHub) problemów przy użyciu tytułu i opisu problemu.</span><span class="sxs-lookup"><span data-stu-id="f49f8-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="f49f8-132">Jest to przykład wieloklasowego zadania uczenia maszynowego klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f49f8-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="f49f8-133">Szablon klasyfikacji problemów dla scenariusza można użyć, jeśli chcesz podzielić dane na trzy lub więcej kategorii.</span><span class="sxs-lookup"><span data-stu-id="f49f8-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="f49f8-134">Przewidywanie liczby</span><span class="sxs-lookup"><span data-stu-id="f49f8-134">Predict a number</span></span>

<span data-ttu-id="f49f8-135">Regresja służy do przewidywania liczb.</span><span class="sxs-lookup"><span data-stu-id="f49f8-135">Regression is used to predict numbers.</span></span>

![Diagram przedstawiający przykłady regresji, takie jak przewidywanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

<span data-ttu-id="f49f8-137">Przewidywanie cen może służyć do przewidywania cen domów za pomocą lokalizacji, wielkości i innych cech domu.</span><span class="sxs-lookup"><span data-stu-id="f49f8-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="f49f8-138">Jest to przykład zadania uczenia maszynowego regresji.</span><span class="sxs-lookup"><span data-stu-id="f49f8-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="f49f8-139">Można użyć szablonu prognozowania cen dla scenariusza, jeśli chcesz przewidzieć wartość liczbową z własnego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="f49f8-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="f49f8-140">Klasyfikowanie obrazów na kategorie</span><span class="sxs-lookup"><span data-stu-id="f49f8-140">Classify images into categories</span></span>

<span data-ttu-id="f49f8-141">Ten scenariusz jest szczególnym przypadkiem klasyfikacji wieloklasowej, gdzie dane wejściowe, które mają być kategoryzowane jest zestaw obrazów.</span><span class="sxs-lookup"><span data-stu-id="f49f8-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="f49f8-142">Klasyfikacja obrazów może służyć do identyfikowania obrazów różnych kategorii.</span><span class="sxs-lookup"><span data-stu-id="f49f8-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="f49f8-143">Na przykład różne rodzaje terenu lub zwierząt lub wady produkcyjne.</span><span class="sxs-lookup"><span data-stu-id="f49f8-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="f49f8-144">Można użyć szablonu klasyfikacji obrazów dla scenariusza, jeśli masz zestaw obrazów i chcesz sklasyfikować obrazy na różne kategorie.</span><span class="sxs-lookup"><span data-stu-id="f49f8-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="f49f8-145">Scenariusz niestandardowy</span><span class="sxs-lookup"><span data-stu-id="f49f8-145">Custom scenario</span></span>

<span data-ttu-id="f49f8-146">Scenariusz niestandardowy umożliwia ręczne wybranie scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f49f8-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="f49f8-147">Dane</span><span class="sxs-lookup"><span data-stu-id="f49f8-147">Data</span></span>

<span data-ttu-id="f49f8-148">Po wybraniu scenariusza Konstruktor modeli prosi o podanie zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="f49f8-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="f49f8-149">Dane są używane do uczenia, oceny i wybrać najlepszy model dla scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f49f8-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram przedstawiający kroki konstruktora modeli](media/model-builder-steps.png)

<span data-ttu-id="f49f8-151">Program Model Builder obsługuje zestawy danych w formatach .tsv, csv, .txt, a także w formacie bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="f49f8-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="f49f8-152">Jeśli masz plik txt, kolumny powinny `,`być `;` `/t` oddzielone , a plik musi mieć wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="f49f8-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="f49f8-153">Jeśli zestaw danych składa się z obrazów, obsługiwane `.jpg` `.png`typy plików są i .</span><span class="sxs-lookup"><span data-stu-id="f49f8-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="f49f8-154">Aby uzyskać więcej informacji, zobacz [Ładowanie danych szkoleniowych do konstruktora modeli](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="f49f8-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="f49f8-155">Wybierz dane wyjściowe do przewidzenia (etykieta)</span><span class="sxs-lookup"><span data-stu-id="f49f8-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="f49f8-156">Zestaw danych to tabela wierszy przykładów szkoleniowych i kolumn atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f49f8-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="f49f8-157">Każdy wiersz ma:</span><span class="sxs-lookup"><span data-stu-id="f49f8-157">Each row has:</span></span>

- <span data-ttu-id="f49f8-158">**etykieta** (atrybut, który chcesz przewidzieć)</span><span class="sxs-lookup"><span data-stu-id="f49f8-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="f49f8-159">**(atrybuty,** które są używane jako dane wejściowe do przewidywania etykiety).</span><span class="sxs-lookup"><span data-stu-id="f49f8-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="f49f8-160">W scenariuszu prognozowania ceny domu funkcje mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="f49f8-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="f49f8-161">kwadratowy materiał filmowy domu</span><span class="sxs-lookup"><span data-stu-id="f49f8-161">the square footage of the house</span></span>
- <span data-ttu-id="f49f8-162">liczba sypialni i łazienek</span><span class="sxs-lookup"><span data-stu-id="f49f8-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="f49f8-163">kod pocztowy</span><span class="sxs-lookup"><span data-stu-id="f49f8-163">the zip code</span></span>

<span data-ttu-id="f49f8-164">Etykieta jest historyczna cena domu dla tego rzędu kwadratowych materiału, sypialni i wartości łazienki i kodu pocztowego.</span><span class="sxs-lookup"><span data-stu-id="f49f8-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela przedstawiająca wiersze i kolumny danych o cenach domów z funkcjami składającymi się z kodu pocztowego pokoi i etykiety cenowej](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="f49f8-166">Przykładowe zestawy danych</span><span class="sxs-lookup"><span data-stu-id="f49f8-166">Example datasets</span></span>

<span data-ttu-id="f49f8-167">Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z następujących zestawów danych:</span><span class="sxs-lookup"><span data-stu-id="f49f8-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="f49f8-168">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="f49f8-168">Scenario</span></span>|<span data-ttu-id="f49f8-169">Zadanie ML</span><span class="sxs-lookup"><span data-stu-id="f49f8-169">ML task</span></span>|<span data-ttu-id="f49f8-170">Dane</span><span class="sxs-lookup"><span data-stu-id="f49f8-170">Data</span></span>|<span data-ttu-id="f49f8-171">Label</span><span class="sxs-lookup"><span data-stu-id="f49f8-171">Label</span></span>|<span data-ttu-id="f49f8-172">Funkcje</span><span class="sxs-lookup"><span data-stu-id="f49f8-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="f49f8-173">Przewidywanie cen</span><span class="sxs-lookup"><span data-stu-id="f49f8-173">Price prediction</span></span>|<span data-ttu-id="f49f8-174">Regresji</span><span class="sxs-lookup"><span data-stu-id="f49f8-174">regression</span></span>|[<span data-ttu-id="f49f8-175">dane dotyczące opłat za przejazd taksówką</span><span class="sxs-lookup"><span data-stu-id="f49f8-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="f49f8-176">Taryfy</span><span class="sxs-lookup"><span data-stu-id="f49f8-176">Fare</span></span>|<span data-ttu-id="f49f8-177">Czas podróży, odległość</span><span class="sxs-lookup"><span data-stu-id="f49f8-177">Trip time, distance</span></span>|
|<span data-ttu-id="f49f8-178">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="f49f8-178">Anomaly detection</span></span>|<span data-ttu-id="f49f8-179">klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f49f8-179">binary classification</span></span>|[<span data-ttu-id="f49f8-180">dane o sprzedaży produktów</span><span class="sxs-lookup"><span data-stu-id="f49f8-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="f49f8-181">Sprzedaż produktów</span><span class="sxs-lookup"><span data-stu-id="f49f8-181">Product Sales</span></span>|<span data-ttu-id="f49f8-182">Month</span><span class="sxs-lookup"><span data-stu-id="f49f8-182">Month</span></span>|
|<span data-ttu-id="f49f8-183">Analiza tonacji</span><span class="sxs-lookup"><span data-stu-id="f49f8-183">Sentiment analysis</span></span>|<span data-ttu-id="f49f8-184">klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f49f8-184">binary classification</span></span>|[<span data-ttu-id="f49f8-185">dane komentarza strony internetowej</span><span class="sxs-lookup"><span data-stu-id="f49f8-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="f49f8-186">Etykieta (0, gdy negatywne nastroje, 1, gdy dodatnie)</span><span class="sxs-lookup"><span data-stu-id="f49f8-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="f49f8-187">Komentarz, Rok</span><span class="sxs-lookup"><span data-stu-id="f49f8-187">Comment, Year</span></span>|
|<span data-ttu-id="f49f8-188">Wykrywanie oszustw</span><span class="sxs-lookup"><span data-stu-id="f49f8-188">Fraud detection</span></span>|<span data-ttu-id="f49f8-189">klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="f49f8-189">binary classification</span></span>|[<span data-ttu-id="f49f8-190">dane karty kredytowej</span><span class="sxs-lookup"><span data-stu-id="f49f8-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="f49f8-191">Klasa (1 w przypadku oszustwa, 0 w przeciwnym razie)</span><span class="sxs-lookup"><span data-stu-id="f49f8-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="f49f8-192">Kwota, V1-V28 (funkcje zanonimizowane)</span><span class="sxs-lookup"><span data-stu-id="f49f8-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="f49f8-193">Klasyfikacja tekstu</span><span class="sxs-lookup"><span data-stu-id="f49f8-193">Text classification</span></span>|<span data-ttu-id="f49f8-194">klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="f49f8-194">multiclass classification</span></span>|[<span data-ttu-id="f49f8-195">Dane o problemach usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="f49f8-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="f49f8-196">Obszar</span><span class="sxs-lookup"><span data-stu-id="f49f8-196">Area</span></span>|<span data-ttu-id="f49f8-197">Tytuł, Opis</span><span class="sxs-lookup"><span data-stu-id="f49f8-197">Title, Description</span></span>|
|<span data-ttu-id="f49f8-198">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="f49f8-198">Image classification</span></span>|<span data-ttu-id="f49f8-199">klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="f49f8-199">multiclass classification</span></span>|[<span data-ttu-id="f49f8-200">Kwiaty obrazy</span><span class="sxs-lookup"><span data-stu-id="f49f8-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="f49f8-201">Rodzaj kwiatu: stokrotka, mniszek lekarski, róże, słoneczniki, tulipany</span><span class="sxs-lookup"><span data-stu-id="f49f8-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="f49f8-202">Same dane obrazu</span><span class="sxs-lookup"><span data-stu-id="f49f8-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="f49f8-203">Szkolenie</span><span class="sxs-lookup"><span data-stu-id="f49f8-203">Train</span></span>

<span data-ttu-id="f49f8-204">Po wybraniu scenariusza, danych i etykiety Konstruktor modeli szkoli model.</span><span class="sxs-lookup"><span data-stu-id="f49f8-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="f49f8-205">Co to jest szkolenie?</span><span class="sxs-lookup"><span data-stu-id="f49f8-205">What is training?</span></span>

<span data-ttu-id="f49f8-206">Szkolenie to automatyczny proces, za pomocą którego model Konstruktor nauczy model, jak odpowiadać na pytania dotyczące scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f49f8-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="f49f8-207">Po przeszkoleniu model może przewidywać dane wejściowe, których wcześniej nie widział.</span><span class="sxs-lookup"><span data-stu-id="f49f8-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="f49f8-208">Na przykład, jeśli przewidujesz ceny domów i nowy dom wchodzi na rynek, możesz przewidzieć jego cenę sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="f49f8-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="f49f8-209">Ponieważ Model Konstruktor używa automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani strojenia od ciebie podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="f49f8-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="f49f8-210">Jak długo powinienem trenować?</span><span class="sxs-lookup"><span data-stu-id="f49f8-210">How long should I train for?</span></span>

<span data-ttu-id="f49f8-211">Model Konstruktor używa automl do eksplorowania wielu modeli, aby znaleźć najlepszy model.</span><span class="sxs-lookup"><span data-stu-id="f49f8-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="f49f8-212">Dłuższe okresy treningowe umożliwiają automl eksplorowanie większej liczby modeli z szerszym zakresem ustawień.</span><span class="sxs-lookup"><span data-stu-id="f49f8-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="f49f8-213">W poniższej tabeli podsumowano średni czas, który został umówiony na uzyskanie dobrej wydajności dla zestawu przykładowych zestawów danych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f49f8-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="f49f8-214">Rozmiar zestawu danych</span><span class="sxs-lookup"><span data-stu-id="f49f8-214">Dataset size</span></span>|<span data-ttu-id="f49f8-215">Średni czas szkolenia</span><span class="sxs-lookup"><span data-stu-id="f49f8-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="f49f8-216">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="f49f8-216">0 - 10 MB</span></span>|<span data-ttu-id="f49f8-217">10 sek.</span><span class="sxs-lookup"><span data-stu-id="f49f8-217">10 sec</span></span>|
|<span data-ttu-id="f49f8-218">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="f49f8-218">10 - 100 MB</span></span>|<span data-ttu-id="f49f8-219">10 min.</span><span class="sxs-lookup"><span data-stu-id="f49f8-219">10 min</span></span>|
|<span data-ttu-id="f49f8-220">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="f49f8-220">100 - 500 MB</span></span>|<span data-ttu-id="f49f8-221">30 min.</span><span class="sxs-lookup"><span data-stu-id="f49f8-221">30 min</span></span>|
|<span data-ttu-id="f49f8-222">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="f49f8-222">500 - 1 GB</span></span>|<span data-ttu-id="f49f8-223">60 min.</span><span class="sxs-lookup"><span data-stu-id="f49f8-223">60 min</span></span>|
|<span data-ttu-id="f49f8-224">1 GB+</span><span class="sxs-lookup"><span data-stu-id="f49f8-224">1 GB+</span></span>|<span data-ttu-id="f49f8-225">3+ godzin</span><span class="sxs-lookup"><span data-stu-id="f49f8-225">3+ hours</span></span>|

<span data-ttu-id="f49f8-226">Liczby te są tylko przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="f49f8-226">These numbers are a guide only.</span></span> <span data-ttu-id="f49f8-227">Dokładna długość szkolenia zależy od:</span><span class="sxs-lookup"><span data-stu-id="f49f8-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="f49f8-228">liczba obiektów (kolumn) używanych jako dane wejściowe do modelu</span><span class="sxs-lookup"><span data-stu-id="f49f8-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="f49f8-229">typ kolumn</span><span class="sxs-lookup"><span data-stu-id="f49f8-229">the type of columns</span></span>
- <span data-ttu-id="f49f8-230">zadanie ML</span><span class="sxs-lookup"><span data-stu-id="f49f8-230">the ML task</span></span>
- <span data-ttu-id="f49f8-231">wydajność procesora, dysku i pamięci urządzenia używanego do szkolenia</span><span class="sxs-lookup"><span data-stu-id="f49f8-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="f49f8-232">Evaluate</span><span class="sxs-lookup"><span data-stu-id="f49f8-232">Evaluate</span></span>

<span data-ttu-id="f49f8-233">Ocena to proces pomiaru, jak dobry jest twój model.</span><span class="sxs-lookup"><span data-stu-id="f49f8-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="f49f8-234">Konstruktor modeli używa uczonego modelu do tworzenia prognoz z nowymi danymi testowymi, a następnie mierzy, jak dobre są prognozy.</span><span class="sxs-lookup"><span data-stu-id="f49f8-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="f49f8-235">Konstruktor modeli dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testów.</span><span class="sxs-lookup"><span data-stu-id="f49f8-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="f49f8-236">Dane szkoleniowe (80%) służy do szkolenia modelu i danych testowych (20%) jest wstrzymywana do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="f49f8-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="f49f8-237">Jak zrozumieć wydajność modelu?</span><span class="sxs-lookup"><span data-stu-id="f49f8-237">How do I understand my model performance?</span></span>

<span data-ttu-id="f49f8-238">Scenariusz jest mapowany do zadania uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="f49f8-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="f49f8-239">Każde zadanie ml ma swój własny zestaw metryk oceny.</span><span class="sxs-lookup"><span data-stu-id="f49f8-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="f49f8-240">Regresja (na przykład przewidywanie cen)</span><span class="sxs-lookup"><span data-stu-id="f49f8-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="f49f8-241">Domyślną metryką dla problemów z regresją jest RSquared, wartość RSquared waha się od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="f49f8-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="f49f8-242">1 jest najlepszą możliwą wartością lub innymi słowy, im bliżej wartości RSquared do 1, tym lepiej radzi sobie twój model.</span><span class="sxs-lookup"><span data-stu-id="f49f8-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="f49f8-243">Inne metryki zgłaszane, takie jak strata bezwzględna, kwadratowa strata i strata rms są dodatkowe metryki, które mogą służyć do zrozumienia, jak model działa i porównanie go z innymi modelami regresji.</span><span class="sxs-lookup"><span data-stu-id="f49f8-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="f49f8-244">Klasyfikacja binarna (na przykład analiza tonacji)</span><span class="sxs-lookup"><span data-stu-id="f49f8-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="f49f8-245">Domyślną metryką problemów z klasyfikacją jest dokładność.</span><span class="sxs-lookup"><span data-stu-id="f49f8-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="f49f8-246">Dokładność definiuje proporcję poprawnych prognoz modelu jest wykonywanie za pomocą zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="f49f8-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="f49f8-247">Im bliżej 100% lub 1,0, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="f49f8-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="f49f8-248">Inne zgłoszone wskaźniki, takie jak AUC (Obszar pod krzywą), który mierzy rzeczywistą dodatnią szybkość w porównaniu z fałszywie dodatnim wskaźnikiem, powinny być większe niż 0,50, aby modele były akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="f49f8-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="f49f8-249">Dodatkowe metryki, takie jak wynik F1 może służyć do kontrolowania równowagi między precyzji i odwołania.</span><span class="sxs-lookup"><span data-stu-id="f49f8-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="f49f8-250">Klasyfikacja wieloklasowa (na przykład klasyfikacja wydania, klasyfikacja obrazów)</span><span class="sxs-lookup"><span data-stu-id="f49f8-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="f49f8-251">Domyślną metryką dla klasyfikacji wieloklasowej jest Mikrodokładność.</span><span class="sxs-lookup"><span data-stu-id="f49f8-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="f49f8-252">Im bliżej Mikro dokładności do 100% lub 1,0, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="f49f8-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="f49f8-253">Inną ważną metryką dla klasyfikacji wieloklasowej jest dokładność makro, podobna do mikrodokładności im bliżej 1.0, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="f49f8-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="f49f8-254">Dobrym sposobem myślenia o tych dwóch rodzajach dokładności jest:</span><span class="sxs-lookup"><span data-stu-id="f49f8-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="f49f8-255">Mikrodokładność: Jak często bilet przychodzący jest klasyfikowany do właściwego zespołu?</span><span class="sxs-lookup"><span data-stu-id="f49f8-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="f49f8-256">Makrodokładność: Jak często bilet przychodzący jest prawidłowy dla ich drużyny?</span><span class="sxs-lookup"><span data-stu-id="f49f8-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="f49f8-257">Więcej informacji na temat wskaźników oceny</span><span class="sxs-lookup"><span data-stu-id="f49f8-257">More information on evaluation metrics</span></span>

<span data-ttu-id="f49f8-258">Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="f49f8-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="f49f8-259">Poprawić</span><span class="sxs-lookup"><span data-stu-id="f49f8-259">Improve</span></span>

<span data-ttu-id="f49f8-260">Jeśli wynik wydajności modelu nie jest tak dobry, jak chcesz, możesz:</span><span class="sxs-lookup"><span data-stu-id="f49f8-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="f49f8-261">Trenuj przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="f49f8-261">Train for a longer period of time.</span></span> <span data-ttu-id="f49f8-262">Z więcej czasu, aparat automatycznego uczenia maszynowego, aby wypróbować więcej algorytmów i ustawień.</span><span class="sxs-lookup"><span data-stu-id="f49f8-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="f49f8-263">Dodaj więcej danych.</span><span class="sxs-lookup"><span data-stu-id="f49f8-263">Add more data.</span></span> <span data-ttu-id="f49f8-264">Czasami ilość danych nie jest wystarczająca do nauczenia modelu uczenia maszynowego wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="f49f8-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="f49f8-265">Zrównoważ swoje dane.</span><span class="sxs-lookup"><span data-stu-id="f49f8-265">Balance your data.</span></span> <span data-ttu-id="f49f8-266">W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony w różnych kategoriach.</span><span class="sxs-lookup"><span data-stu-id="f49f8-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="f49f8-267">Na przykład jeśli masz cztery klasy na 100 przykładów szkolenia, a dwie pierwsze klasy (tag1 i tag2) są używane dla 90 rekordów, ale pozostałe dwie (tag3 i tag4) są używane tylko w pozostałych 10 rekordach, brak zrównoważonych danych może spowodować, że model będzie miał problemy z poprawnie przewidzieć tag3 lub tag4.</span><span class="sxs-lookup"><span data-stu-id="f49f8-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="f49f8-268">Code</span><span class="sxs-lookup"><span data-stu-id="f49f8-268">Code</span></span>

<span data-ttu-id="f49f8-269">Po fazie oceny Konstruktor modeli generuje plik modelu i kod, którego można użyć do dodania modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f49f8-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="f49f8-270">ML.NET modele są zapisywane jako plik zip.</span><span class="sxs-lookup"><span data-stu-id="f49f8-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="f49f8-271">Kod do załadowania i używania modelu jest dodawany jako nowy projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="f49f8-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="f49f8-272">Konstruktor modeli dodaje również przykładową aplikację konsoli, którą można uruchomić, aby zobaczyć model w działaniu.</span><span class="sxs-lookup"><span data-stu-id="f49f8-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="f49f8-273">Ponadto Konstruktor modeli generuje kod, który wygenerował model, dzięki czemu można zrozumieć kroki używane do generowania modelu.</span><span class="sxs-lookup"><span data-stu-id="f49f8-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="f49f8-274">Można również użyć kodu szkolenia modelu do ponownego uczenia modelu z nowymi danymi.</span><span class="sxs-lookup"><span data-stu-id="f49f8-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="f49f8-275">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="f49f8-275">What's next?</span></span>

<span data-ttu-id="f49f8-276">[Instalowanie](how-to-guides/install-model-builder.md) rozszerzenia programu Visual Studio dla konstruktora modeli</span><span class="sxs-lookup"><span data-stu-id="f49f8-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="f49f8-277">[Wypróbuj prognozę cen lub scenariusz regresji](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="f49f8-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
