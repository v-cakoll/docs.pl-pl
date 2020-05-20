---
title: Co to jest Konstruktor modelu i jak to działa?
description: Jak korzystać z konstruktora modelu ML.NET w celu automatycznego uczenia modelu uczenia maszynowego
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 4afdbfd1682a30647b09d05d51a5c73c214fe2bd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616933"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="a1682-103">Co to jest Konstruktor modelu i jak to działa?</span><span class="sxs-lookup"><span data-stu-id="a1682-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="a1682-104">Konstruktor modelu ML.NET to intuicyjne graficzne rozszerzenie programu Visual Studio służące do kompilowania, uczenia i wdrażania niestandardowych modeli uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="a1682-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="a1682-105">Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), aby poznać różne algorytmy uczenia maszynowego i ustawienia, które ułatwiają znalezienie tego, który najlepiej odpowiada Twojemu scenariuszowi.</span><span class="sxs-lookup"><span data-stu-id="a1682-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="a1682-106">Nie musisz uczyć się uczenia maszynowego, aby korzystać z konstruktora modeli.</span><span class="sxs-lookup"><span data-stu-id="a1682-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="a1682-107">Wystarczy kilka danych i problem do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a1682-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="a1682-108">Konstruktor modelu generuje kod umożliwiający dodanie modelu do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="a1682-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animacja interfejsu użytkownika rozszerzenia programu Visual Studio Builder](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="a1682-110">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="a1682-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="a1682-111">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="a1682-111">Scenario</span></span>

<span data-ttu-id="a1682-112">W celu wygenerowania modelu uczenia maszynowego dla aplikacji można przenieść wiele różnych scenariuszy do programu model Builder.</span><span class="sxs-lookup"><span data-stu-id="a1682-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="a1682-113">Scenariusz to opis typu przewidywania, które chcesz wprowadzić przy użyciu danych.</span><span class="sxs-lookup"><span data-stu-id="a1682-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="a1682-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a1682-114">For example:</span></span>

- <span data-ttu-id="a1682-115">przewidywanie przyszłego wolumenu sprzedaży produktu na podstawie historycznych danych sprzedaży</span><span class="sxs-lookup"><span data-stu-id="a1682-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="a1682-116">Klasyfikuj mową jako dodatnie lub ujemne na podstawie recenzji klienta</span><span class="sxs-lookup"><span data-stu-id="a1682-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="a1682-117">Wykryj, czy transakcja bankowa jest fałszywa</span><span class="sxs-lookup"><span data-stu-id="a1682-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="a1682-118">kierowanie problemów z opiniami klientów do właściwego zespołu w firmie</span><span class="sxs-lookup"><span data-stu-id="a1682-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="a1682-119">Który scenariusz uczenia maszynowego jest dla mnie właściwy?</span><span class="sxs-lookup"><span data-stu-id="a1682-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="a1682-120">W konstruktorze modelu należy wybrać scenariusz.</span><span class="sxs-lookup"><span data-stu-id="a1682-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="a1682-121">Typ scenariusza zależy od typu przewidywania, które próbujesz wprowadzić.</span><span class="sxs-lookup"><span data-stu-id="a1682-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="a1682-122">Klasyfikacja tekstu</span><span class="sxs-lookup"><span data-stu-id="a1682-122">Text classification</span></span>

<span data-ttu-id="a1682-123">Klasyfikacja służy do klasyfikowania danych do kategorii.</span><span class="sxs-lookup"><span data-stu-id="a1682-123">Classification is used to categorize data into categories.</span></span>

![Diagram przedstawiający przykłady klasyfikacji danych binarnych, w tym wykrywanie oszustw, łagodzenie ryzyka i osłanianie aplikacji](media/binary-classification-examples.png)

![Przykłady klasyfikacji wieloklasowej, w tym Klasyfikacja dokumentów i produktów, obsługa routingu biletów i problemów klientów](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="a1682-126">Przewidywanie wartości</span><span class="sxs-lookup"><span data-stu-id="a1682-126">Value prediction</span></span>

<span data-ttu-id="a1682-127">Regresja służy do przewidywania liczby.</span><span class="sxs-lookup"><span data-stu-id="a1682-127">Regression is used to predict numbers.</span></span>

![Diagram przedstawiający przykłady regresji, takie jak prognozowanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="a1682-129">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="a1682-129">Image classification</span></span>

<span data-ttu-id="a1682-130">Klasyfikacja obrazu może służyć do identyfikowania obrazów różnych kategorii.</span><span class="sxs-lookup"><span data-stu-id="a1682-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="a1682-131">Na przykład różne rodzaje terenów lub zwierząt lub wady produkcji.</span><span class="sxs-lookup"><span data-stu-id="a1682-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="a1682-132">Możesz użyć scenariusza klasyfikacji obrazu, jeśli masz zestaw obrazów i chcesz sklasyfikować obrazy w różnych kategoriach.</span><span class="sxs-lookup"><span data-stu-id="a1682-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="a1682-133">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="a1682-133">Recommendation</span></span>

<span data-ttu-id="a1682-134">Scenariusz rekomendacji przewiduje listę sugerowanych elementów dla określonego użytkownika, w zależności od tego, jak podobne ich polubienia i przeciwieństwo do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a1682-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="a1682-135">Scenariusza zalecenia można użyć, jeśli masz zestaw użytkowników i zestaw "produktów", takich jak elementy do zakupu, filmy, książki lub programy telewizyjne, a także zestaw klasyfikacji użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a1682-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="a1682-136">Środowisko</span><span class="sxs-lookup"><span data-stu-id="a1682-136">Environment</span></span>

<span data-ttu-id="a1682-137">Model uczenia maszynowego można uczenie lokalnie na komputerze lub w chmurze na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="a1682-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="a1682-138">W przypadku nauczenia lokalnego można obejść ograniczenia zasobów komputera (procesor CPU, pamięć i dysk).</span><span class="sxs-lookup"><span data-stu-id="a1682-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="a1682-139">Podczas uczenia się w chmurze można skalować zasoby w górę w celu spełnienia wymagań scenariusza, szczególnie w przypadku dużych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="a1682-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="a1682-140">Szkolenia lokalne są obsługiwane we wszystkich scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="a1682-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="a1682-141">Szkolenia platformy Azure są obsługiwane na potrzeby klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="a1682-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="a1682-142">Dane</span><span class="sxs-lookup"><span data-stu-id="a1682-142">Data</span></span>

<span data-ttu-id="a1682-143">Po wybraniu scenariusza Konstruktor modelu prosi o dostarczenie zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a1682-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="a1682-144">Dane służą do uczenia, oszacowania i wyboru najlepszego modelu dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="a1682-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram przedstawiający kroki konstruktora modelu](media/model-builder-steps.png)

<span data-ttu-id="a1682-146">Konstruktor modelu obsługuje zestawy danych w formatach. tsv,. csv,. txt, a także w formacie SQL Database.</span><span class="sxs-lookup"><span data-stu-id="a1682-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="a1682-147">Jeśli masz plik txt, kolumny powinny być rozdzielone znakami `,` , `;` lub, `/t` a plik musi mieć wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a1682-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="a1682-148">Jeśli zestaw danych składa się z obrazów, obsługiwane typy plików to `.jpg` i `.png` .</span><span class="sxs-lookup"><span data-stu-id="a1682-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="a1682-149">Aby uzyskać więcej informacji, zobacz [ładowanie danych szkoleniowych do konstruktora modeli](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="a1682-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="a1682-150">Wybierz dane wyjściowe do przewidywania (etykieta)</span><span class="sxs-lookup"><span data-stu-id="a1682-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="a1682-151">Zestaw danych to tabela wierszy przykładów szkoleniowych i kolumn atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a1682-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="a1682-152">Każdy wiersz ma:</span><span class="sxs-lookup"><span data-stu-id="a1682-152">Each row has:</span></span>

- <span data-ttu-id="a1682-153">**etykieta** (atrybut, który ma zostać przewidywalna)</span><span class="sxs-lookup"><span data-stu-id="a1682-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="a1682-154">**funkcje** (atrybuty, które są używane jako dane wejściowe do przewidywania etykiet).</span><span class="sxs-lookup"><span data-stu-id="a1682-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="a1682-155">W przypadku scenariusza przewidywania cen dla domu funkcje mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="a1682-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="a1682-156">kwadratowy materiał dla domu</span><span class="sxs-lookup"><span data-stu-id="a1682-156">the square footage of the house</span></span>
- <span data-ttu-id="a1682-157">Liczba sypialniami i bathrooms</span><span class="sxs-lookup"><span data-stu-id="a1682-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="a1682-158">kod pocztowy</span><span class="sxs-lookup"><span data-stu-id="a1682-158">the zip code</span></span>

<span data-ttu-id="a1682-159">Etykieta to historyczna cena za ten wiersz kwadratów, Bedroom i wartości łazienkowych oraz kod pocztowy.</span><span class="sxs-lookup"><span data-stu-id="a1682-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela przedstawiająca wiersze i kolumny danych cen domu z funkcjami zawierającymi kod pocztowy pokojów i etykietę cen](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="a1682-161">Przykładowe zestawy danych</span><span class="sxs-lookup"><span data-stu-id="a1682-161">Example datasets</span></span>

<span data-ttu-id="a1682-162">Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z tych zestawów danych:</span><span class="sxs-lookup"><span data-stu-id="a1682-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="a1682-163">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="a1682-163">Scenario</span></span>|<span data-ttu-id="a1682-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1682-164">Example</span></span>|<span data-ttu-id="a1682-165">Dane</span><span class="sxs-lookup"><span data-stu-id="a1682-165">Data</span></span>|<span data-ttu-id="a1682-166">Etykieta</span><span class="sxs-lookup"><span data-stu-id="a1682-166">Label</span></span>|<span data-ttu-id="a1682-167">Funkcje</span><span class="sxs-lookup"><span data-stu-id="a1682-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="a1682-168">Klasyfikacja</span><span class="sxs-lookup"><span data-stu-id="a1682-168">Classification</span></span>|<span data-ttu-id="a1682-169">Przewidywanie anomalii sprzedaży</span><span class="sxs-lookup"><span data-stu-id="a1682-169">Predict sales anomalies</span></span>|[<span data-ttu-id="a1682-170">dane sprzedaży produktu</span><span class="sxs-lookup"><span data-stu-id="a1682-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="a1682-171">Sprzedaż produktu</span><span class="sxs-lookup"><span data-stu-id="a1682-171">Product Sales</span></span>|<span data-ttu-id="a1682-172">Month</span><span class="sxs-lookup"><span data-stu-id="a1682-172">Month</span></span>|
||<span data-ttu-id="a1682-173">Przewidywanie tonacji z komentarzy w witrynie sieci Web</span><span class="sxs-lookup"><span data-stu-id="a1682-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="a1682-174">dane komentarzy witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="a1682-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="a1682-175">Etykieta (0 w przypadku wartości ujemnej tonacji, 1, gdy wartość jest dodatnia)</span><span class="sxs-lookup"><span data-stu-id="a1682-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="a1682-176">Komentarz, rok</span><span class="sxs-lookup"><span data-stu-id="a1682-176">Comment, Year</span></span>|
||<span data-ttu-id="a1682-177">Przewidywanie oszustw transakcji kart kredytowych</span><span class="sxs-lookup"><span data-stu-id="a1682-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="a1682-178">dane karty kredytowej</span><span class="sxs-lookup"><span data-stu-id="a1682-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="a1682-179">Klasa (1 w przypadku oszustwa, 0 w przeciwnym razie)</span><span class="sxs-lookup"><span data-stu-id="a1682-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="a1682-180">Kwota, v1 — v28 (funkcje anonimowe)</span><span class="sxs-lookup"><span data-stu-id="a1682-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="a1682-181">Przewidywanie typu problemu w repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="a1682-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="a1682-182">Dane problemu w usłudze GitHub</span><span class="sxs-lookup"><span data-stu-id="a1682-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="a1682-183">Warstwowy</span><span class="sxs-lookup"><span data-stu-id="a1682-183">Area</span></span>|<span data-ttu-id="a1682-184">Tytuł, opis</span><span class="sxs-lookup"><span data-stu-id="a1682-184">Title, Description</span></span>|
|<span data-ttu-id="a1682-185">Przewidywanie wartości</span><span class="sxs-lookup"><span data-stu-id="a1682-185">Value prediction</span></span>|<span data-ttu-id="a1682-186">Przewidywanie ceny opłat za taksówkę</span><span class="sxs-lookup"><span data-stu-id="a1682-186">Predict taxi fare price</span></span>|[<span data-ttu-id="a1682-187">dane dotyczące opłat za taksówki</span><span class="sxs-lookup"><span data-stu-id="a1682-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="a1682-188">Bezprzewodow</span><span class="sxs-lookup"><span data-stu-id="a1682-188">Fare</span></span>|<span data-ttu-id="a1682-189">Czas podróży, odległość</span><span class="sxs-lookup"><span data-stu-id="a1682-189">Trip time, distance</span></span>|
|<span data-ttu-id="a1682-190">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="a1682-190">Image classification</span></span>|<span data-ttu-id="a1682-191">Przewidywanie kategorii kwiatów</span><span class="sxs-lookup"><span data-stu-id="a1682-191">Predict the category of a flower</span></span> |[<span data-ttu-id="a1682-192">obrazy kwiatów</span><span class="sxs-lookup"><span data-stu-id="a1682-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="a1682-193">Typ kwitnienia: wirujące, Dandelion, róże, przepływy, Tulips</span><span class="sxs-lookup"><span data-stu-id="a1682-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="a1682-194">Same dane obrazu</span><span class="sxs-lookup"><span data-stu-id="a1682-194">The image data itself</span></span>|
|<span data-ttu-id="a1682-195">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="a1682-195">Recommendation</span></span>|<span data-ttu-id="a1682-196">Przewidywania filmów, które ktoś chce</span><span class="sxs-lookup"><span data-stu-id="a1682-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="a1682-197">Klasyfikacje filmów</span><span class="sxs-lookup"><span data-stu-id="a1682-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="a1682-198">Użytkownicy, filmy</span><span class="sxs-lookup"><span data-stu-id="a1682-198">Users, Movies</span></span>|<span data-ttu-id="a1682-199">Klasyfikacje</span><span class="sxs-lookup"><span data-stu-id="a1682-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="a1682-200">Szkolenie</span><span class="sxs-lookup"><span data-stu-id="a1682-200">Train</span></span>

<span data-ttu-id="a1682-201">Po wybraniu scenariusza, danych i etykiety, Konstruktor modelu pociąga za niego model.</span><span class="sxs-lookup"><span data-stu-id="a1682-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="a1682-202">Co to jest szkolenie?</span><span class="sxs-lookup"><span data-stu-id="a1682-202">What is training?</span></span>

<span data-ttu-id="a1682-203">Szkolenia są procesem automatycznym, dzięki któremu Konstruktor modelu uczy się, jak odpowiedzieć na pytania dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="a1682-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="a1682-204">Po przeszkoleniu model może tworzyć prognozy zawierające dane wejściowe, które nie były wcześniej widoczne.</span><span class="sxs-lookup"><span data-stu-id="a1682-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="a1682-205">Na przykład jeśli zamierzasz przewidzieć ceny domu i nowe miejsce na rynku, możesz przewidzieć cenę sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="a1682-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="a1682-206">Ponieważ Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani dostrajania podczas szkoleń.</span><span class="sxs-lookup"><span data-stu-id="a1682-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="a1682-207">Jak długo mam nauczyć?</span><span class="sxs-lookup"><span data-stu-id="a1682-207">How long should I train for?</span></span>

<span data-ttu-id="a1682-208">Konstruktor modelu używa AutoML do eksplorowania wielu modeli, aby znaleźć najlepszy model.</span><span class="sxs-lookup"><span data-stu-id="a1682-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="a1682-209">Dłuższe okresy szkoleniowe umożliwiają AutoMLom Eksplorowanie więcej modeli z szerszym zakresem ustawień.</span><span class="sxs-lookup"><span data-stu-id="a1682-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="a1682-210">W poniższej tabeli zestawiono średni czas potrzebny do uzyskania dobrej wydajności zestawu przykładowych zestawów danych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a1682-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="a1682-211">Rozmiar zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a1682-211">Dataset size</span></span>|<span data-ttu-id="a1682-212">Średni czas uczenia</span><span class="sxs-lookup"><span data-stu-id="a1682-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="a1682-213">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="a1682-213">0 - 10 MB</span></span>|<span data-ttu-id="a1682-214">10 sekund</span><span class="sxs-lookup"><span data-stu-id="a1682-214">10 sec</span></span>|
|<span data-ttu-id="a1682-215">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="a1682-215">10 - 100 MB</span></span>|<span data-ttu-id="a1682-216">10 min</span><span class="sxs-lookup"><span data-stu-id="a1682-216">10 min</span></span>|
|<span data-ttu-id="a1682-217">100 – 500 MB</span><span class="sxs-lookup"><span data-stu-id="a1682-217">100 - 500 MB</span></span>|<span data-ttu-id="a1682-218">30 minut</span><span class="sxs-lookup"><span data-stu-id="a1682-218">30 min</span></span>|
|<span data-ttu-id="a1682-219">500 – 1 GB</span><span class="sxs-lookup"><span data-stu-id="a1682-219">500 - 1 GB</span></span>|<span data-ttu-id="a1682-220">60 min</span><span class="sxs-lookup"><span data-stu-id="a1682-220">60 min</span></span>|
|<span data-ttu-id="a1682-221">1 GB +</span><span class="sxs-lookup"><span data-stu-id="a1682-221">1 GB+</span></span>|<span data-ttu-id="a1682-222">3 godziny</span><span class="sxs-lookup"><span data-stu-id="a1682-222">3+ hours</span></span>|

<span data-ttu-id="a1682-223">Te liczby są tylko przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="a1682-223">These numbers are a guide only.</span></span> <span data-ttu-id="a1682-224">Dokładna długość szkolenia zależy od:</span><span class="sxs-lookup"><span data-stu-id="a1682-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="a1682-225">liczba funkcji (kolumn) używanych jako dane wejściowe do modelu</span><span class="sxs-lookup"><span data-stu-id="a1682-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="a1682-226">Typ kolumn</span><span class="sxs-lookup"><span data-stu-id="a1682-226">the type of columns</span></span>
- <span data-ttu-id="a1682-227">zadanie ML</span><span class="sxs-lookup"><span data-stu-id="a1682-227">the ML task</span></span>
- <span data-ttu-id="a1682-228">wydajność procesora, dysku i pamięci maszyny używanej na potrzeby szkolenia</span><span class="sxs-lookup"><span data-stu-id="a1682-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="a1682-229">Evaluate</span><span class="sxs-lookup"><span data-stu-id="a1682-229">Evaluate</span></span>

<span data-ttu-id="a1682-230">Ocena to proces mierzenia, jaki jest dobry model.</span><span class="sxs-lookup"><span data-stu-id="a1682-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="a1682-231">Konstruktor modelu korzysta z przeszkolonego modelu do tworzenia prognoz z nowymi danymi testowymi, a następnie mierzy, jak dobre są przewidywania.</span><span class="sxs-lookup"><span data-stu-id="a1682-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="a1682-232">Konstruktor modelu dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testowy.</span><span class="sxs-lookup"><span data-stu-id="a1682-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="a1682-233">Dane szkoleniowe (80%) służy do uczenia modelu i danych testowych (20%) jest zatrzymywany z powrotem do oszacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="a1682-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="a1682-234">Jak mogę zrozumieć moją wydajność modelu?</span><span class="sxs-lookup"><span data-stu-id="a1682-234">How do I understand my model performance?</span></span>

<span data-ttu-id="a1682-235">Scenariusz jest mapowany na zadanie uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="a1682-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="a1682-236">Każde zadanie ML ma swój własny zestaw metryk oceny.</span><span class="sxs-lookup"><span data-stu-id="a1682-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="a1682-237">Przewidywanie wartości</span><span class="sxs-lookup"><span data-stu-id="a1682-237">Value prediction</span></span>

<span data-ttu-id="a1682-238">Domyślną metryką dla problemów przewidywania wartości jest RSquared, wartość RSquared zakresów z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="a1682-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="a1682-239">1 jest najlepszą możliwą wartością lub innymi słowy, im bliżej wartości RSquared do 1 lepiej, gdy model jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="a1682-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="a1682-240">Inne raportowane metryki, takie jak bezwzględne, kwadratowe straty i straty RMS, to dodatkowe metryki, których można użyć do zrozumienia, jak model jest wykonywany i który jest porównywany z innymi modelami przewidywania wartości.</span><span class="sxs-lookup"><span data-stu-id="a1682-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="a1682-241">Klasyfikacja (2 kategorie)</span><span class="sxs-lookup"><span data-stu-id="a1682-241">Classification (2 categories)</span></span>

<span data-ttu-id="a1682-242">Domyślna Metryka dla problemów klasyfikacji jest dokładność.</span><span class="sxs-lookup"><span data-stu-id="a1682-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="a1682-243">Dokładność definiuje proporcję poprawnych prognoz, jaką model przekracza zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a1682-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="a1682-244">Im bliżej 100% lub 1,0, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="a1682-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="a1682-245">Inne raportowane metryki, takie jak AUC (obszar pod krzywą), które mierzą prawdziwą dodatnią stawkę w porównaniu z fałszywą dodatnią częstotliwością, która powinna być większa niż 0,50, aby można było zaakceptować modele.</span><span class="sxs-lookup"><span data-stu-id="a1682-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="a1682-246">Dodatkowe metryki, takie jak F1, mogą służyć do kontrolowania równowagi między dokładnością i odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="a1682-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="a1682-247">Klasyfikacja (3 kategorie)</span><span class="sxs-lookup"><span data-stu-id="a1682-247">Classification (3+ categories)</span></span>

<span data-ttu-id="a1682-248">Metryka domyślna dla klasyfikacji wieloklasowej to Micro dokładności.</span><span class="sxs-lookup"><span data-stu-id="a1682-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="a1682-249">Im bliżej nie jest to lepsza dokładność do 100% lub 1,0.</span><span class="sxs-lookup"><span data-stu-id="a1682-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="a1682-250">Kolejną ważną metryką dla klasyfikacji wieloklasowej jest dokładność makro, podobnie jak w przypadku mikrodokładności zbliżonej do 1,0.</span><span class="sxs-lookup"><span data-stu-id="a1682-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="a1682-251">Dobrym sposobem na to, że te dwa typy dokładności są następujące:</span><span class="sxs-lookup"><span data-stu-id="a1682-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="a1682-252">Mikro-dokładność: jak często bilet przychodzący jest klasyfikowany do właściwego zespołu?</span><span class="sxs-lookup"><span data-stu-id="a1682-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="a1682-253">Dokładność makr: dla średniego zespołu, jak często bilet przychodzący jest poprawny dla swojego zespołu?</span><span class="sxs-lookup"><span data-stu-id="a1682-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="a1682-254">Więcej informacji na temat metryk oceny</span><span class="sxs-lookup"><span data-stu-id="a1682-254">More information on evaluation metrics</span></span>

<span data-ttu-id="a1682-255">Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="a1682-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="a1682-256">Przyspieszy</span><span class="sxs-lookup"><span data-stu-id="a1682-256">Improve</span></span>

<span data-ttu-id="a1682-257">Jeśli Ocena wydajności modelu nie jest tak dobra, jak chcesz, możesz:</span><span class="sxs-lookup"><span data-stu-id="a1682-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="a1682-258">Uczenie przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="a1682-258">Train for a longer period of time.</span></span> <span data-ttu-id="a1682-259">Przez więcej czasu eksperymenty aparatu uczenia maszynowego z dodatkowymi algorytmami i ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="a1682-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="a1682-260">Dodaj więcej danych.</span><span class="sxs-lookup"><span data-stu-id="a1682-260">Add more data.</span></span> <span data-ttu-id="a1682-261">Czasami ilość danych nie wystarcza do uczenia modelu uczenia maszynowego o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="a1682-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="a1682-262">Zrównoważ dane.</span><span class="sxs-lookup"><span data-stu-id="a1682-262">Balance your data.</span></span> <span data-ttu-id="a1682-263">W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony w różnych kategoriach.</span><span class="sxs-lookup"><span data-stu-id="a1682-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="a1682-264">Na przykład, jeśli masz cztery klasy do 100 przykładów szkoleniowych, a dwie pierwszej klasy (tag1 i tag2) są używane do 90 rekordów, ale pozostałe dwa (tag3 i tag4) są używane tylko w pozostałych 10 rekordach, brak zrównoważonych danych może spowodować, że model będzie mógł niezawodnie przewidzieć, czy ma być prawidłowo przewidywalna wartość tag3 lub tag4.</span><span class="sxs-lookup"><span data-stu-id="a1682-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="a1682-265">Kod</span><span class="sxs-lookup"><span data-stu-id="a1682-265">Code</span></span>

<span data-ttu-id="a1682-266">Po zakończeniu fazy oceny Konstruktor modelu wyprowadza plik modelu i kod, którego można użyć do dodania modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1682-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="a1682-267">Modele ML.NET są zapisywane jako plik zip.</span><span class="sxs-lookup"><span data-stu-id="a1682-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="a1682-268">Kod do załadowania i użycia modelu jest dodawany jako nowy projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="a1682-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="a1682-269">Konstruktor modelu dodaje również przykładową aplikację konsolową, którą można uruchomić, aby zobaczyć model w działaniu.</span><span class="sxs-lookup"><span data-stu-id="a1682-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="a1682-270">Ponadto Konstruktor modelu wyprowadza kod, który wygenerował model, dzięki czemu można zrozumieć czynności używane do generowania modelu.</span><span class="sxs-lookup"><span data-stu-id="a1682-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="a1682-271">Możesz również użyć kodu szkolenia modelu, aby ponownie przeprowadzić uczenie modelu z nowymi danymi.</span><span class="sxs-lookup"><span data-stu-id="a1682-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="a1682-272">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="a1682-272">What's next?</span></span>

<span data-ttu-id="a1682-273">[Zainstaluj](how-to-guides/install-model-builder.md) rozszerzenie programu Visual Studio dla programu model Builder</span><span class="sxs-lookup"><span data-stu-id="a1682-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="a1682-274">Wypróbuj [prognozę cenową lub dowolny scenariusz regresji](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="a1682-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
