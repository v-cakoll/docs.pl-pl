---
title: Co to jest Kreator modeli i jak działa?
description: Jak automatycznie szkolić model uczenia maszynowego za pomocą ML.NET Programu Model Builder
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344768"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="2a831-103">Co to jest Kreator modeli i jak działa?</span><span class="sxs-lookup"><span data-stu-id="2a831-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="2a831-104">ML.NET Model Builder to intuicyjne graficzne rozszerzenie programu Visual Studio do tworzenia, szkolenia i wdrażania niestandardowych modeli uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="2a831-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="2a831-105">Kreator modeli używa automatycznego uczenia maszynowego (AutoML) do eksplorowania różnych algorytmów i ustawień uczenia maszynowego, aby ułatwić znalezienie tego, który najlepiej odpowiada twojemu scenariuszowi.</span><span class="sxs-lookup"><span data-stu-id="2a831-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="2a831-106">Nie potrzebujesz wiedzy specjalistycznej w zakresie uczenia maszynowego, aby korzystać z kreatora modeli.</span><span class="sxs-lookup"><span data-stu-id="2a831-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="2a831-107">Wszystko, czego potrzebujesz, to dane i problem do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2a831-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="2a831-108">Kreator modeli generuje kod, aby dodać model do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="2a831-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animacja interfejsu użytkownika rozszerzenia programu Visual Studio programu Model Builder](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="2a831-110">Kreator modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="2a831-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="2a831-111">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="2a831-111">Scenario</span></span>

<span data-ttu-id="2a831-112">Można przynieść wiele różnych scenariuszy do konstruktora modelu, aby wygenerować model uczenia maszynowego dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2a831-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="2a831-113">Scenariusz to opis typu prognozowania, które chcesz wprowadzić przy użyciu danych.</span><span class="sxs-lookup"><span data-stu-id="2a831-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="2a831-114">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2a831-114">For example:</span></span>

- <span data-ttu-id="2a831-115">przewidywanie przyszłej wielkości sprzedaży produktu na podstawie historycznych danych o sprzedaży</span><span class="sxs-lookup"><span data-stu-id="2a831-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="2a831-116">klasyfikowanie nastrojów jako pozytywnych lub negatywnych na podstawie opinii klientów</span><span class="sxs-lookup"><span data-stu-id="2a831-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="2a831-117">wykrywanie, czy transakcja bankowa jest oszukańcza</span><span class="sxs-lookup"><span data-stu-id="2a831-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="2a831-118">rozsyłanie problemów z opiniami klientów do właściwego zespołu w firmie</span><span class="sxs-lookup"><span data-stu-id="2a831-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="2a831-119">Który scenariusz uczenia maszynowego jest dla mnie odpowiedni?</span><span class="sxs-lookup"><span data-stu-id="2a831-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="2a831-120">W Kreatorze modeli należy wybrać scenariusz.</span><span class="sxs-lookup"><span data-stu-id="2a831-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="2a831-121">Typ scenariusza zależy od tego, jaki typ prognozowania próbujesz zrobić.</span><span class="sxs-lookup"><span data-stu-id="2a831-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="2a831-122">Klasyfikacja tekstu</span><span class="sxs-lookup"><span data-stu-id="2a831-122">Text classification</span></span>

<span data-ttu-id="2a831-123">Klasyfikacja służy do kategoryzowanie danych na kategorie.</span><span class="sxs-lookup"><span data-stu-id="2a831-123">Classification is used to categorize data into categories.</span></span>

![Diagram przedstawiający przykłady klasyfikacji binarnej, w tym wykrywanie oszustw, ograniczanie ryzyka i monitorowanie aplikacji](media/binary-classification-examples.png)

![Przykłady klasyfikacji wieloklasowej, w tym klasyfikacja dokumentów i produktów, routing biletów pomocy technicznej i ustalanie priorytetów problemów klientów](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="2a831-126">Przewidywanie wartości</span><span class="sxs-lookup"><span data-stu-id="2a831-126">Value prediction</span></span>

<span data-ttu-id="2a831-127">Regresja jest używana do przewidywania liczb.</span><span class="sxs-lookup"><span data-stu-id="2a831-127">Regression is used to predict numbers.</span></span>

![Diagram przedstawiający przykłady regresji, takie jak przewidywanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="2a831-129">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="2a831-129">Image classification</span></span>

<span data-ttu-id="2a831-130">Klasyfikacja obrazów może służyć do identyfikowania obrazów różnych kategorii.</span><span class="sxs-lookup"><span data-stu-id="2a831-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="2a831-131">Na przykład różne rodzaje terenu lub zwierząt lub wady produkcyjne.</span><span class="sxs-lookup"><span data-stu-id="2a831-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="2a831-132">Można użyć scenariusza klasyfikacji obrazów, jeśli masz zestaw obrazów i chcesz sklasyfikować obrazy do różnych kategorii.</span><span class="sxs-lookup"><span data-stu-id="2a831-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="2a831-133">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="2a831-133">Recommendation</span></span>

<span data-ttu-id="2a831-134">Scenariusz rekomendacji przewiduje listę sugerowanych elementów dla określonego użytkownika, na podstawie tego, jak podobne są ich polubienia i antypatie do innych użytkowników".</span><span class="sxs-lookup"><span data-stu-id="2a831-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="2a831-135">Możesz użyć scenariusza rekomendacji, gdy masz zestaw użytkowników i zestaw "produktów", takich jak produkty do zakupu, filmy, książki lub programy telewizyjne, wraz z zestawem "ocen" tych produktów przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2a831-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="2a831-136">Środowisko</span><span class="sxs-lookup"><span data-stu-id="2a831-136">Environment</span></span>

<span data-ttu-id="2a831-137">Model uczenia maszynowego można trenować lokalnie na komputerze lub w chmurze na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="2a831-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="2a831-138">Podczas szkolenia lokalnego, pracujesz w ramach ograniczeń zasobów komputera (procesora CPU, pamięci i dysku).</span><span class="sxs-lookup"><span data-stu-id="2a831-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="2a831-139">Podczas szkolenia w chmurze, można skalować zasoby w górę, aby spełnić wymagania scenariusza, szczególnie dla dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="2a831-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="2a831-140">Szkolenie lokalne jest obsługiwane dla wszystkich scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="2a831-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="2a831-141">Szkolenie platformy Azure jest obsługiwane dla klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="2a831-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="2a831-142">Dane</span><span class="sxs-lookup"><span data-stu-id="2a831-142">Data</span></span>

<span data-ttu-id="2a831-143">Po wybraniu scenariusza Kreator modelu prosi o podanie zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="2a831-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="2a831-144">Dane są używane do szkolenia, oceny i wybierz najlepszy model dla scenariusza.</span><span class="sxs-lookup"><span data-stu-id="2a831-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram przedstawiający kroki Konstruktora modeli](media/model-builder-steps.png)

<span data-ttu-id="2a831-146">Program Model Builder obsługuje zestawy danych w formatach .tsv, csv, .txt, a także w formacie bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="2a831-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="2a831-147">Jeśli masz plik txt, kolumny powinny być `,`oddzielone `/t` lub, `;` a plik musi mieć wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="2a831-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="2a831-148">Jeśli zestaw danych składa się z obrazów, obsługiwane `.jpg` `.png`typy plików są i .</span><span class="sxs-lookup"><span data-stu-id="2a831-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="2a831-149">Aby uzyskać więcej informacji, zobacz [Ładowanie danych szkoleniowych do kreatora modeli](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="2a831-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="2a831-150">Wybierz dane wyjściowe do przewidzenia (etykieta)</span><span class="sxs-lookup"><span data-stu-id="2a831-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="2a831-151">Zestaw danych to tabela wierszy przykładów treningu i kolumn atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2a831-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="2a831-152">Każdy wiersz ma:</span><span class="sxs-lookup"><span data-stu-id="2a831-152">Each row has:</span></span>

- <span data-ttu-id="2a831-153">**etykieta** (atrybut, który chcesz przewidzieć)</span><span class="sxs-lookup"><span data-stu-id="2a831-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="2a831-154">**funkcje** (atrybuty, które są używane jako dane wejściowe do przewidywania etykiety).</span><span class="sxs-lookup"><span data-stu-id="2a831-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="2a831-155">W przypadku scenariusza przewidywania ceny domu funkcje mogą być:</span><span class="sxs-lookup"><span data-stu-id="2a831-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="2a831-156">kwadratowy materiał z domu</span><span class="sxs-lookup"><span data-stu-id="2a831-156">the square footage of the house</span></span>
- <span data-ttu-id="2a831-157">liczba sypialni i łazienek</span><span class="sxs-lookup"><span data-stu-id="2a831-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="2a831-158">kod pocztowy</span><span class="sxs-lookup"><span data-stu-id="2a831-158">the zip code</span></span>

<span data-ttu-id="2a831-159">Etykieta jest historyczną ceną domu dla tego rzędu kwadratowych materiałów, sypialni i wartości łazienki i kodu pocztowego.</span><span class="sxs-lookup"><span data-stu-id="2a831-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela przedstawiająca wiersze i kolumny danych o cenie domu z funkcjami składającymi się z kodu pocztowego pokoi wielkości i etykiety cenowej](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="2a831-161">Przykładowe zestawy danych</span><span class="sxs-lookup"><span data-stu-id="2a831-161">Example datasets</span></span>

<span data-ttu-id="2a831-162">Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z następujących zestawów danych:</span><span class="sxs-lookup"><span data-stu-id="2a831-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="2a831-163">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="2a831-163">Scenario</span></span>|<span data-ttu-id="2a831-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a831-164">Example</span></span>|<span data-ttu-id="2a831-165">Dane</span><span class="sxs-lookup"><span data-stu-id="2a831-165">Data</span></span>|<span data-ttu-id="2a831-166">Label</span><span class="sxs-lookup"><span data-stu-id="2a831-166">Label</span></span>|<span data-ttu-id="2a831-167">Funkcje</span><span class="sxs-lookup"><span data-stu-id="2a831-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="2a831-168">Klasyfikacja</span><span class="sxs-lookup"><span data-stu-id="2a831-168">Classification</span></span>|<span data-ttu-id="2a831-169">Przewidywanie anomalii sprzedaży</span><span class="sxs-lookup"><span data-stu-id="2a831-169">Predict sales anomalies</span></span>|[<span data-ttu-id="2a831-170">dane dotyczące sprzedaży produktów</span><span class="sxs-lookup"><span data-stu-id="2a831-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="2a831-171">Sprzedaż produktów</span><span class="sxs-lookup"><span data-stu-id="2a831-171">Product Sales</span></span>|<span data-ttu-id="2a831-172">Month</span><span class="sxs-lookup"><span data-stu-id="2a831-172">Month</span></span>|
||<span data-ttu-id="2a831-173">Przewidywanie nastrojów komentarzy na stronie internetowej</span><span class="sxs-lookup"><span data-stu-id="2a831-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="2a831-174">dane dotyczące komentarzy do witryny</span><span class="sxs-lookup"><span data-stu-id="2a831-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="2a831-175">Etykieta (0, gdy negatywne nastroje, 1, gdy dodatnie)</span><span class="sxs-lookup"><span data-stu-id="2a831-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="2a831-176">Komentarz, Rok</span><span class="sxs-lookup"><span data-stu-id="2a831-176">Comment, Year</span></span>|
||<span data-ttu-id="2a831-177">Przewidywanie nieuczciwych transakcji kartą kredytową</span><span class="sxs-lookup"><span data-stu-id="2a831-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="2a831-178">dane karty kredytowej</span><span class="sxs-lookup"><span data-stu-id="2a831-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="2a831-179">Klasa (1, gdy oszukańcze, 0 w przeciwnym razie)</span><span class="sxs-lookup"><span data-stu-id="2a831-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="2a831-180">Kwota, V1-V28 (funkcje zanonimizowane)</span><span class="sxs-lookup"><span data-stu-id="2a831-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="2a831-181">Przewidywanie typu problemu w repozytorium Usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="2a831-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="2a831-182">Dane o problemie z githubem</span><span class="sxs-lookup"><span data-stu-id="2a831-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="2a831-183">Obszar</span><span class="sxs-lookup"><span data-stu-id="2a831-183">Area</span></span>|<span data-ttu-id="2a831-184">Tytuł, Opis</span><span class="sxs-lookup"><span data-stu-id="2a831-184">Title, Description</span></span>|
|<span data-ttu-id="2a831-185">Przewidywanie wartości</span><span class="sxs-lookup"><span data-stu-id="2a831-185">Value prediction</span></span>|<span data-ttu-id="2a831-186">Przewiduj cenę taryfy taksówek</span><span class="sxs-lookup"><span data-stu-id="2a831-186">Predict taxi fare price</span></span>|[<span data-ttu-id="2a831-187">dane dotyczące taryfy taksówek</span><span class="sxs-lookup"><span data-stu-id="2a831-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="2a831-188">Taryfy</span><span class="sxs-lookup"><span data-stu-id="2a831-188">Fare</span></span>|<span data-ttu-id="2a831-189">Czas podróży, odległość</span><span class="sxs-lookup"><span data-stu-id="2a831-189">Trip time, distance</span></span>|
|<span data-ttu-id="2a831-190">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="2a831-190">Image classification</span></span>|<span data-ttu-id="2a831-191">Przewidywanie kategorii problemu</span><span class="sxs-lookup"><span data-stu-id="2a831-191">Predict the category of an issue</span></span>|[<span data-ttu-id="2a831-192">obrazy kwiatów</span><span class="sxs-lookup"><span data-stu-id="2a831-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="2a831-193">Rodzaj kwiatu: stokrotka, mniszek lekarski, róże, słoneczniki, tulipany</span><span class="sxs-lookup"><span data-stu-id="2a831-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="2a831-194">Same dane obrazu</span><span class="sxs-lookup"><span data-stu-id="2a831-194">The image data itself</span></span>|
|<span data-ttu-id="2a831-195">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="2a831-195">Recommendation</span></span>|<span data-ttu-id="2a831-196">Przewiduj filmy, które komuś się spodobają</span><span class="sxs-lookup"><span data-stu-id="2a831-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="2a831-197">oceny filmów</span><span class="sxs-lookup"><span data-stu-id="2a831-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="2a831-198">Użytkownicy, Filmy</span><span class="sxs-lookup"><span data-stu-id="2a831-198">Users, Movies</span></span>|<span data-ttu-id="2a831-199">Klasyfikacje</span><span class="sxs-lookup"><span data-stu-id="2a831-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="2a831-200">Szkolenie</span><span class="sxs-lookup"><span data-stu-id="2a831-200">Train</span></span>

<span data-ttu-id="2a831-201">Po wybraniu scenariusza, danych i etykiety, Model Builder trenuje modelu.</span><span class="sxs-lookup"><span data-stu-id="2a831-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="2a831-202">Co to jest szkolenie?</span><span class="sxs-lookup"><span data-stu-id="2a831-202">What is training?</span></span>

<span data-ttu-id="2a831-203">Szkolenie to automatyczny proces, w którym kreator modelu uczy modelu, jak odpowiedzieć na pytania dotyczące scenariusza.</span><span class="sxs-lookup"><span data-stu-id="2a831-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="2a831-204">Po przeszkoleniu modelu można dokonać prognoz z danych wejściowych, które nie widział wcześniej.</span><span class="sxs-lookup"><span data-stu-id="2a831-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="2a831-205">Na przykład, jeśli przewidujesz ceny domów i nowy dom pojawia się na rynku, możesz przewidzieć jego cenę sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="2a831-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="2a831-206">Ponieważ program Model Builder używa automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani dostrajania od ciebie podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="2a831-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="2a831-207">Jak długo powinienem trenować?</span><span class="sxs-lookup"><span data-stu-id="2a831-207">How long should I train for?</span></span>

<span data-ttu-id="2a831-208">Kreator modeli używa automl do eksplorowania wielu modeli, aby znaleźć model o najlepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="2a831-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="2a831-209">Dłuższe okresy treningowe umożliwiają automl eksplorowanie większej liczby modeli z szerszym zakresem ustawień.</span><span class="sxs-lookup"><span data-stu-id="2a831-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="2a831-210">W poniższej tabeli podsumowano średni czas wykonania pakietu przykładowych zestawów danych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="2a831-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="2a831-211">Rozmiar zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2a831-211">Dataset size</span></span>|<span data-ttu-id="2a831-212">Średni czas szkolenia</span><span class="sxs-lookup"><span data-stu-id="2a831-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="2a831-213">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="2a831-213">0 - 10 MB</span></span>|<span data-ttu-id="2a831-214">10 sek.</span><span class="sxs-lookup"><span data-stu-id="2a831-214">10 sec</span></span>|
|<span data-ttu-id="2a831-215">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="2a831-215">10 - 100 MB</span></span>|<span data-ttu-id="2a831-216">10 min.</span><span class="sxs-lookup"><span data-stu-id="2a831-216">10 min</span></span>|
|<span data-ttu-id="2a831-217">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="2a831-217">100 - 500 MB</span></span>|<span data-ttu-id="2a831-218">30 min.</span><span class="sxs-lookup"><span data-stu-id="2a831-218">30 min</span></span>|
|<span data-ttu-id="2a831-219">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="2a831-219">500 - 1 GB</span></span>|<span data-ttu-id="2a831-220">60 min.</span><span class="sxs-lookup"><span data-stu-id="2a831-220">60 min</span></span>|
|<span data-ttu-id="2a831-221">1 GB+</span><span class="sxs-lookup"><span data-stu-id="2a831-221">1 GB+</span></span>|<span data-ttu-id="2a831-222">3+ godzin</span><span class="sxs-lookup"><span data-stu-id="2a831-222">3+ hours</span></span>|

<span data-ttu-id="2a831-223">Te liczby są tylko przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="2a831-223">These numbers are a guide only.</span></span> <span data-ttu-id="2a831-224">Dokładna długość szkolenia zależy od:</span><span class="sxs-lookup"><span data-stu-id="2a831-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="2a831-225">liczba obiektów (kolumn) używanych jako dane wejściowe do modelu</span><span class="sxs-lookup"><span data-stu-id="2a831-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="2a831-226">typ kolumn</span><span class="sxs-lookup"><span data-stu-id="2a831-226">the type of columns</span></span>
- <span data-ttu-id="2a831-227">zadanie ML</span><span class="sxs-lookup"><span data-stu-id="2a831-227">the ML task</span></span>
- <span data-ttu-id="2a831-228">wydajność procesora, dysku i pamięci urządzenia używanego do treningu</span><span class="sxs-lookup"><span data-stu-id="2a831-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="2a831-229">Evaluate</span><span class="sxs-lookup"><span data-stu-id="2a831-229">Evaluate</span></span>

<span data-ttu-id="2a831-230">Ocena to proces pomiaru, jak dobry jest Twój model.</span><span class="sxs-lookup"><span data-stu-id="2a831-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="2a831-231">Kreator modeli używa uczonego modelu do tworzenia prognoz z nowymi danymi testowymi, a następnie mierzy, jak dobre są prognozy.</span><span class="sxs-lookup"><span data-stu-id="2a831-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="2a831-232">Kreator modeli dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testów.</span><span class="sxs-lookup"><span data-stu-id="2a831-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="2a831-233">Dane szkoleniowe (80%) służy do szkolenia modelu i danych testowych (20%) zostanie wstrzymana w celu oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="2a831-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="2a831-234">Jak zrozumieć wydajność modelu?</span><span class="sxs-lookup"><span data-stu-id="2a831-234">How do I understand my model performance?</span></span>

<span data-ttu-id="2a831-235">Scenariusz mapuje zadanie uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="2a831-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="2a831-236">Każde zadanie uczenia maszynowego ma swój własny zestaw metryk oceny.</span><span class="sxs-lookup"><span data-stu-id="2a831-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="2a831-237">Przewidywanie wartości</span><span class="sxs-lookup"><span data-stu-id="2a831-237">Value prediction</span></span>

<span data-ttu-id="2a831-238">Domyślną metryką problemów z przewidywaniem wartości jest RSquared, wartość RSquared waha się od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="2a831-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="2a831-239">1 jest najlepszą możliwą wartością lub innymi słowy im bliżej wartości RSquared do 1, tym lepszy model wykonuje.</span><span class="sxs-lookup"><span data-stu-id="2a831-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="2a831-240">Inne metryki zgłaszane, takie jak bezwzględna strata, strata kwadratowa i strata usługi RMS to dodatkowe metryki, których można użyć do zrozumienia działania modelu i porównania go z innymi modelami przewidywania wartości.</span><span class="sxs-lookup"><span data-stu-id="2a831-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="2a831-241">Klasyfikacja (2 kategorie)</span><span class="sxs-lookup"><span data-stu-id="2a831-241">Classification (2 categories)</span></span>

<span data-ttu-id="2a831-242">Domyślną metryką problemów z klasyfikacją jest dokładność.</span><span class="sxs-lookup"><span data-stu-id="2a831-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="2a831-243">Dokładność definiuje proporcję poprawnych prognoz, które model tworzy za pomocą zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2a831-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="2a831-244">Im bliżej 100% lub 1,0 tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="2a831-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="2a831-245">Inne zgłaszane wskaźniki, takie jak AUC (Obszar pod krzywą), który mierzy rzeczywistą dodatnią stopę w porównaniu z fałszywie dodatnim wskaźnikiem powinny być większe niż 0,50 dla modeli, które mają być dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="2a831-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="2a831-246">Dodatkowe metryki, takie jak wynik F1 może służyć do kontrolowania równowagi między Precision i Recall.</span><span class="sxs-lookup"><span data-stu-id="2a831-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="2a831-247">Klasyfikacja (3+ kategorie)</span><span class="sxs-lookup"><span data-stu-id="2a831-247">Classification (3+ categories)</span></span>

<span data-ttu-id="2a831-248">Domyślną metryką dla klasyfikacji wieloklasowej jest mikrodyskość.</span><span class="sxs-lookup"><span data-stu-id="2a831-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="2a831-249">Im bliżej mikrodemy do 100% lub 1,0, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="2a831-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="2a831-250">Inną ważną metryką dla klasyfikacji wieloklasowej jest dokładność makro, podobna do mikrodyskności im bliżej 1.0, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="2a831-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="2a831-251">Dobrym sposobem na zastanowienie się nad tymi dwoma typami dokładności jest:</span><span class="sxs-lookup"><span data-stu-id="2a831-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="2a831-252">Mikrodyskłańca: Jak często przychodzący bilet jest klasyfikowany do właściwego zespołu?</span><span class="sxs-lookup"><span data-stu-id="2a831-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="2a831-253">Makrodność: Jak często bilet przychodzący jest poprawny dla swojej drużyny?</span><span class="sxs-lookup"><span data-stu-id="2a831-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="2a831-254">Więcej informacji na temat wskaźników oceny</span><span class="sxs-lookup"><span data-stu-id="2a831-254">More information on evaluation metrics</span></span>

<span data-ttu-id="2a831-255">Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="2a831-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="2a831-256">Poprawić</span><span class="sxs-lookup"><span data-stu-id="2a831-256">Improve</span></span>

<span data-ttu-id="2a831-257">Jeśli wynik wydajności modelu nie jest tak dobry, jak chcesz, możesz:</span><span class="sxs-lookup"><span data-stu-id="2a831-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="2a831-258">Trenuj przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="2a831-258">Train for a longer period of time.</span></span> <span data-ttu-id="2a831-259">Z więcej czasu, zautomatyzowany aparat uczenia maszynowego eksperymenty z więcej algorytmów i ustawień.</span><span class="sxs-lookup"><span data-stu-id="2a831-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="2a831-260">Dodaj więcej danych.</span><span class="sxs-lookup"><span data-stu-id="2a831-260">Add more data.</span></span> <span data-ttu-id="2a831-261">Czasami ilość danych nie jest wystarczająca do przeszkolenia modelu uczenia maszynowego wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="2a831-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="2a831-262">Zrównoważyć swoje dane.</span><span class="sxs-lookup"><span data-stu-id="2a831-262">Balance your data.</span></span> <span data-ttu-id="2a831-263">W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony między kategoriami.</span><span class="sxs-lookup"><span data-stu-id="2a831-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="2a831-264">Na przykład, jeśli masz cztery klasy dla 100 przykładów treningu, a dwie pierwsze klasy (tag1 i tag2) są używane dla 90 rekordów, ale pozostałe dwie (tag3 i tag4) są używane tylko w pozostałych 10 rekordach, brak zrównoważonych danych może spowodować, że model będzie miał problemy z poprawnie przewidzieć tag3 lub tag4.</span><span class="sxs-lookup"><span data-stu-id="2a831-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="2a831-265">Code</span><span class="sxs-lookup"><span data-stu-id="2a831-265">Code</span></span>

<span data-ttu-id="2a831-266">Po fazie oceny Program Model Builder wyprowadza plik modelu i kod, którego można użyć do dodania modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2a831-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="2a831-267">ML.NET modele są zapisywane jako plik zip.</span><span class="sxs-lookup"><span data-stu-id="2a831-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="2a831-268">Kod do ładowania i używania modelu jest dodawany jako nowy projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="2a831-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="2a831-269">Kreator modeli dodaje również przykładową aplikację konsoli, którą można uruchomić, aby wyświetlić model w działaniu.</span><span class="sxs-lookup"><span data-stu-id="2a831-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="2a831-270">Ponadto Program Model Builder wyprowadza kod, który wygenerował model, dzięki czemu można zrozumieć kroki używane do generowania modelu.</span><span class="sxs-lookup"><span data-stu-id="2a831-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="2a831-271">Można również użyć kodu szkolenia modelu do ponownego przeszkolenia modelu z nowymi danymi.</span><span class="sxs-lookup"><span data-stu-id="2a831-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="2a831-272">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="2a831-272">What's next?</span></span>

<span data-ttu-id="2a831-273">[Instalowanie](how-to-guides/install-model-builder.md) rozszerzenia programu Visual Studio programu Builder</span><span class="sxs-lookup"><span data-stu-id="2a831-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="2a831-274">Wypróbuj [przewidywanie cen lub dowolny scenariusz regresji](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="2a831-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
