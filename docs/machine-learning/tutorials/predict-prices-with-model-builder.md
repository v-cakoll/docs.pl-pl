---
title: Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen
description: W tym samouczku pokazano, jak do zbudowania modelu regresji przy użyciu konstruktora modeli strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9a6f193d877fc1a679b7a3cafd7491e021cb2ad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539633"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="02f9d-103">Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen</span><span class="sxs-lookup"><span data-stu-id="02f9d-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="02f9d-104">Dowiedz się, jak tworzyć za pomocą konstruktora modelu strukturze ML.NET [modelu regresji](../resources/glossary.md#regression) do prognozowania cen.</span><span class="sxs-lookup"><span data-stu-id="02f9d-104">Learn how to use ML.NET Model Builder to build a [regression model](../resources/glossary.md#regression) to predict prices.</span></span>  <span data-ttu-id="02f9d-105">Aplikacji konsolowej .NET, który tworzysz w tym samouczku przewiduje taksówek opłatami na podstawie danych historycznych taryfy taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="02f9d-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="02f9d-106">Szablon prognozowania ceny konstruktora modelu może być używany dla dowolnych scenariuszy wymaga wartości liczbowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="02f9d-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="02f9d-107">Przykładowe scenariusze obejmują: lokalne Prognozowanie cen, przewidywanie zapotrzebowania i Prognozowanie sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="02f9d-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="02f9d-108">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="02f9d-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="02f9d-109">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="02f9d-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="02f9d-110">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="02f9d-110">Choose a scenario</span></span>
> * <span data-ttu-id="02f9d-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="02f9d-111">Load the data</span></span>
> * <span data-ttu-id="02f9d-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="02f9d-112">Train the model</span></span>
> * <span data-ttu-id="02f9d-113">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="02f9d-113">Evaluate the model</span></span>
> * <span data-ttu-id="02f9d-114">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="02f9d-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="02f9d-115">Konstruktor modelu jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="02f9d-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="02f9d-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="02f9d-116">Pre-requisites</span></span>

<span data-ttu-id="02f9d-117">Aby uzyskać listę wymagań wstępnych i instrukcje dotyczące instalacji, odwiedź stronę [Przewodnik instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="02f9d-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="02f9d-118">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="02f9d-118">Create a console application</span></span>

1. <span data-ttu-id="02f9d-119">Tworzenie **aplikacji konsoli .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="02f9d-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="02f9d-120">Zainstaluj **Microsoft.ML** pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="02f9d-120">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="02f9d-121">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu, a następnie wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="02f9d-121">In **Solution Explorer**, right-click the *TaxiFarePrediction* project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="02f9d-122">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="02f9d-122">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="02f9d-123">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="02f9d-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="02f9d-124">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="02f9d-124">Prepare and understand the data</span></span>

1. <span data-ttu-id="02f9d-125">Utwórz katalog o nazwie *danych* w projekcie mają być przechowywane pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="02f9d-125">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="02f9d-126">Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) dane ustawić i zapisać go w celu *danych* folderu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="02f9d-126">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) data set and save it to the *Data* folder you created at the previous step.</span></span> <span data-ttu-id="02f9d-127">Ten zestaw danych służy do nauczanie i ocena modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="02f9d-127">This data set is used to train and evaluate the machine learning model.</span></span> <span data-ttu-id="02f9d-128">Ten zestaw danych pochodzi pierwotnie [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="02f9d-128">This data set is originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="02f9d-129">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *taksówek taryfy train.csv* plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="02f9d-129">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="02f9d-130">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="02f9d-130">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="02f9d-131">Każdy wiersz w `taxi-fare-train.csv` zestaw danych zawiera szczegółowe informacje o wymianie danych wprowadzonych przez taksówek.</span><span class="sxs-lookup"><span data-stu-id="02f9d-131">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="02f9d-132">Otwórz **taksówek taryfy train.csv** zestawu danych</span><span class="sxs-lookup"><span data-stu-id="02f9d-132">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="02f9d-133">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="02f9d-133">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="02f9d-134">**vendor_id:** Identyfikator dostawcy taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="02f9d-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="02f9d-135">**rate_code:** Typ stawki podróży taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="02f9d-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="02f9d-136">**passenger_count:** Liczba osób w ramach wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="02f9d-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="02f9d-137">**trip_time_in_secs:** Ilość czasu trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="02f9d-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="02f9d-138">Chcesz przewidzieć opłacie wyzwolenie przed zakończeniem podróż.</span><span class="sxs-lookup"><span data-stu-id="02f9d-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="02f9d-139">W tym momencie nie wiesz, jak długo podróży zajęłoby.</span><span class="sxs-lookup"><span data-stu-id="02f9d-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="02f9d-140">Dlatego czas podróży nie jest funkcją i będzie Wyklucz tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    * <span data-ttu-id="02f9d-141">**trip_distance:** Odległość wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="02f9d-141">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="02f9d-142">**payment_type:** Sposób zapłaty (pieniężnych lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="02f9d-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="02f9d-143">**fare_amount:** Taryfy taksówek łączna liczba płatnych jest etykieta.</span><span class="sxs-lookup"><span data-stu-id="02f9d-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="02f9d-144">`label` Kolumna, która chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="02f9d-144">The `label` is the column you want to predict.</span></span> <span data-ttu-id="02f9d-145">Podczas wykonywania zadania regresji, celem jest do przewidywania wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="02f9d-145">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="02f9d-146">W tym scenariuszu prognozowania ceny przewiduje koszt jazdy taksówek.</span><span class="sxs-lookup"><span data-stu-id="02f9d-146">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="02f9d-147">W związku z tym **fare_amount** jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="02f9d-147">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="02f9d-148">Wskazywanego przez nią `features` to dane wejściowe, nadaj model do przewidywania `label`.</span><span class="sxs-lookup"><span data-stu-id="02f9d-148">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="02f9d-149">W takim przypadku pozostałe kolumny są używane jako funkcje lub danych wejściowych do prognozowania kwota klasie.</span><span class="sxs-lookup"><span data-stu-id="02f9d-149">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="02f9d-150">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="02f9d-150">Choose a scenario</span></span>

<span data-ttu-id="02f9d-151">Do nauczenia modelu, należy wybrać z listy dostępnych usługi machine learning scenariuszy dostarczone przez Konstruktor modelu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-151">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="02f9d-152">W tym przypadku jest to scenariusz `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="02f9d-152">In this case, the scenario is `Price Prediction`.</span></span> <span data-ttu-id="02f9d-153">Bardziej rozległe listę można znaleźć [artykuł z omówieniem konstruktora modeli](../automate-training-with-model-builder.md#scenarios).</span><span class="sxs-lookup"><span data-stu-id="02f9d-153">For a more extensive list visit the [Model Builder overview article](../automate-training-with-model-builder.md#scenarios).</span></span>

1. <span data-ttu-id="02f9d-154">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu, a następnie wybierz **Dodaj** > **uczenia maszynowego**.</span><span class="sxs-lookup"><span data-stu-id="02f9d-154">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="02f9d-155">W kroku scenariusza narzędzia Konstruktor modelu, wybierz *Prognozowanie cen* scenariusza.</span><span class="sxs-lookup"><span data-stu-id="02f9d-155">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="02f9d-156">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="02f9d-156">Load the data</span></span>

<span data-ttu-id="02f9d-157">Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych programu SQL Server lub w pliku csv lub tsv pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="02f9d-157">Model Builder accepts data from two sources, a SQL Server database or a local file csv or tsv file.</span></span> <span data-ttu-id="02f9d-158">Aby uzyskać więcej informacji na temat wymagań dotyczących formatu danych, można znaleźć w następującej [łącze](../how-to-guides/install-model-builder.md#limitations).</span><span class="sxs-lookup"><span data-stu-id="02f9d-158">For more information on data format requirements, visit the following [link](../how-to-guides/install-model-builder.md#limitations).</span></span>

1. <span data-ttu-id="02f9d-159">W kroku danych narzędzia Konstruktor modelu, wybierz *pliku* z listy rozwijanej źródła danych.</span><span class="sxs-lookup"><span data-stu-id="02f9d-159">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="02f9d-160">Kliknij przycisk Dalej, aby *wybierz plik* pole tekstowe i użyj Eksploratora plików, przeglądania i wybierania *taksówek taryfy test.csv* w *danych* katalogu</span><span class="sxs-lookup"><span data-stu-id="02f9d-160">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="02f9d-161">Wybierz *fare_amount* w *etykiety lub kolumny Predict* listy rozwijanej i przejdź do kroku train narzędzia Konstruktor modelu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-161">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="02f9d-162">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="02f9d-162">Train the model</span></span>

<span data-ttu-id="02f9d-163">Używane do trenowania modelu prognozowania ceny w tym samouczku zadania uczenia maszynowego jest regresji.</span><span class="sxs-lookup"><span data-stu-id="02f9d-163">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="02f9d-164">W trakcie szkolenia modelu konstruktora modeli szkolenie modeli na osobne modele przy użyciu regresji różnych algorytmów i ustawienia, aby znaleźć najlepiej działający model dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="02f9d-164">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="02f9d-165">Czas wymagany do do nauczenia modelu jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="02f9d-165">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="02f9d-166">Skorzystaj z tej tabeli jako wskazówki wybrać odpowiednią wartość `Time to train (seconds)` pola:</span><span class="sxs-lookup"><span data-stu-id="02f9d-166">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="02f9d-167">\* Rozmiar zestawu danych</span><span class="sxs-lookup"><span data-stu-id="02f9d-167">\*Dataset Size</span></span>  | <span data-ttu-id="02f9d-168">Typ zestawu danych</span><span class="sxs-lookup"><span data-stu-id="02f9d-168">Dataset Type</span></span>       | <span data-ttu-id="02f9d-169">Średni Czas do pociągu \*</span><span class="sxs-lookup"><span data-stu-id="02f9d-169">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="02f9d-170">0 - 10 mb</span><span class="sxs-lookup"><span data-stu-id="02f9d-170">0 - 10 Mb</span></span>     | <span data-ttu-id="02f9d-171">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="02f9d-171">Numeric and Text</span></span>   | <span data-ttu-id="02f9d-172">10 s</span><span class="sxs-lookup"><span data-stu-id="02f9d-172">10 sec</span></span>
<span data-ttu-id="02f9d-173">10 - 100 mb</span><span class="sxs-lookup"><span data-stu-id="02f9d-173">10 - 100 Mb</span></span>   | <span data-ttu-id="02f9d-174">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="02f9d-174">Numeric and Text</span></span>   | <span data-ttu-id="02f9d-175">10 min</span><span class="sxs-lookup"><span data-stu-id="02f9d-175">10 min</span></span>
<span data-ttu-id="02f9d-176">100 – 500 mb</span><span class="sxs-lookup"><span data-stu-id="02f9d-176">100 - 500 Mb</span></span>  | <span data-ttu-id="02f9d-177">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="02f9d-177">Numeric and Text</span></span>   | <span data-ttu-id="02f9d-178">30 min</span><span class="sxs-lookup"><span data-stu-id="02f9d-178">30 min</span></span>
<span data-ttu-id="02f9d-179">500 — 1 Gb</span><span class="sxs-lookup"><span data-stu-id="02f9d-179">500 - 1 Gb</span></span>    | <span data-ttu-id="02f9d-180">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="02f9d-180">Numeric and Text</span></span>   | <span data-ttu-id="02f9d-181">60 min</span><span class="sxs-lookup"><span data-stu-id="02f9d-181">60 min</span></span>
<span data-ttu-id="02f9d-182">1 Gb+</span><span class="sxs-lookup"><span data-stu-id="02f9d-182">1 Gb+</span></span>         | <span data-ttu-id="02f9d-183">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="02f9d-183">Numeric and Text</span></span>   | <span data-ttu-id="02f9d-184">3 godziny +</span><span class="sxs-lookup"><span data-stu-id="02f9d-184">3 hour+</span></span>

1. <span data-ttu-id="02f9d-185">Ponieważ plik danych szkoleniowych więcej niż 10MB, należy użyć 600 sekund (10 minut), jako wartość pozycji *czas na nauczenie (w sekundach)* .</span><span class="sxs-lookup"><span data-stu-id="02f9d-185">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="02f9d-186">Wybierz *Rozpocznij szkolenie*.</span><span class="sxs-lookup"><span data-stu-id="02f9d-186">Select *Start Training*.</span></span>

<span data-ttu-id="02f9d-187">Przez cały proces szkolenia postępu dane są wyświetlane w `Progress` części kroku pociągu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-187">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="02f9d-188">Stan wyświetlany stan ukończenia procesu uczenia.</span><span class="sxs-lookup"><span data-stu-id="02f9d-188">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="02f9d-189">Najlepsze dokładności Wyświetla dokładność najlepiej działający model znalezione przez konstruktora modeli do tej pory.</span><span class="sxs-lookup"><span data-stu-id="02f9d-189">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="02f9d-190">Większą dokładność oznacza, że model przewiduje właściwie na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="02f9d-190">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="02f9d-191">Najlepszy algorytm Wyświetla nazwę algorytmu działają najlepiej wykonać znalezione przez konstruktora modeli do tej pory.</span><span class="sxs-lookup"><span data-stu-id="02f9d-191">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="02f9d-192">Ostatni algorytm Wyświetla nazwę algorytmu do nauczenia modelu, ostatnio używane przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-192">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="02f9d-193">Po zakończeniu szkolenia, przejdź do kroku evaluate.</span><span class="sxs-lookup"><span data-stu-id="02f9d-193">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="02f9d-194">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="02f9d-194">Evaluate the model</span></span>

<span data-ttu-id="02f9d-195">Wynik kroku szkolenia będzie jednego modelu, który ma najwyższą wydajność.</span><span class="sxs-lookup"><span data-stu-id="02f9d-195">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="02f9d-196">W kroku evaluate narzędzia Konstruktor modelu, w sekcji danych wyjściowych będzie zawierać algorytmów używanych przez funkcję najlepiej działający model w *najlepszy Model* wpisu wraz z metrykami w *Najlepsza jakość modeli (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="02f9d-196">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="02f9d-197">Ponadto podsumowanie tabelę zawierającą pięć modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="02f9d-197">Additionally, a summary table containing top five models and their metrics.</span></span> <span data-ttu-id="02f9d-198">Skorzystaj z następującego linku, aby dowiedzieć się więcej na temat [oceniania modelu metryki](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span><span class="sxs-lookup"><span data-stu-id="02f9d-198">Visit the following link to learn more about [evaluating model metrics](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span></span>

<span data-ttu-id="02f9d-199">Jeśli nie jesteś zadowolony z metryk dokładności, niektóre łatwy sposób zwiększenia dokładności modelu i spróbuj mają zwiększyć ilość czasu do nauczenia modelu, lub Użyj większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="02f9d-199">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="02f9d-200">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="02f9d-200">Use the model for predictions</span></span>

<span data-ttu-id="02f9d-201">Dwa projekty zostaną utworzone w wyniku procesu uczenia.</span><span class="sxs-lookup"><span data-stu-id="02f9d-201">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="02f9d-202">TaxiFarePredictionML.ConsoleApp: Aplikacja konsoli .NET, która zawiera kod, szkolenia i użycie modelu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-202">TaxiFarePredictionML.ConsoleApp: A .NET Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="02f9d-203">TaxiFarePredictionML.Model: Biblioteki klas .NET Standard zawierający modeli danych, które zdefiniować schemat danych wejściowych i wyjściowych modelu danych, a także utrwalonych wersję najlepiej działający model podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="02f9d-203">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="02f9d-204">W sekcji kodu, narzędzia konstruktora modeli wybierz **dodać projekty** dodać projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="02f9d-204">In the code section of the Model Builder tool, select **Added Projects** to add the projects to the solution.</span></span>
2. <span data-ttu-id="02f9d-205">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-205">In solution explorer, right-click the *TaxiFarePrediction* project.</span></span> <span data-ttu-id="02f9d-206">Następnie wybierz **Dodaj > istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="02f9d-206">Then, select **Add > Existing Item**.</span></span> <span data-ttu-id="02f9d-207">Plik typu listy rozwijanej wybierz `All Files`, przejdź do *TaxiFarePredictionML.Model* projekt katalogu i wybierz `MLModel.zip` pliku.</span><span class="sxs-lookup"><span data-stu-id="02f9d-207">For file type drop down, select `All Files`, navigate to the *TaxiFarePredictionML.Model* project directory and select the `MLModel.zip` file.</span></span> <span data-ttu-id="02f9d-208">Kliknij prawym przyciskiem myszy ostatnio dodane `MLModel.zip` plik i wybierz *właściwości*.</span><span class="sxs-lookup"><span data-stu-id="02f9d-208">Then right-click the recently added `MLModel.zip` file and select *Properties*.</span></span> <span data-ttu-id="02f9d-209">Kopiuj do katalogu wyjściowego opcji, można wybrać *Kopiuj Jeśli nowszy* z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="02f9d-209">For the Copy to Output Directory option, select *Copy if Newer* from the dropdown.</span></span>
3. <span data-ttu-id="02f9d-210">Kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-210">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="02f9d-211">Następnie **Dodaj > dokumentacja**.</span><span class="sxs-lookup"><span data-stu-id="02f9d-211">Then, **Add > Reference**.</span></span> <span data-ttu-id="02f9d-212">Wybierz **projektów > rozwiązania** węzła i z listy, sprawdź *TaxiFarePredictionML.Model* projektu, a następnie wybierz przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="02f9d-212">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>

4. <span data-ttu-id="02f9d-213">Otwórz *Program.cs* w pliku *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-213">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
5. <span data-ttu-id="02f9d-214">Dodaj następujące instrukcje using:</span><span class="sxs-lookup"><span data-stu-id="02f9d-214">Add the following using statements:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. <span data-ttu-id="02f9d-215">Dodaj `ConsumeModel` metody `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="02f9d-215">Add the `ConsumeModel` method to the `Program` class.</span></span> <span data-ttu-id="02f9d-216">`ConsumeModel` Utworzy `PredictionEngine` oparte na modelu wygenerowany przez konstruktora modelu do prognozowania na nowe dane i wydrukuj do konsoli.</span><span class="sxs-lookup"><span data-stu-id="02f9d-216">The `ConsumeModel` will create a `PredictionEngine` based on the model generated by Model Builder to make predictions on new data and print them out to the console.</span></span>

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. <span data-ttu-id="02f9d-217">Dodaj następujący kod do `Main` metody i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="02f9d-217">Add the following code to the `Main` method and run the application.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    <span data-ttu-id="02f9d-218">Dane wyjściowe generowane przez program powinien wyglądać podobnie jak poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="02f9d-218">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="02f9d-219">Jeśli musisz odwoływać się do wygenerowanego projektów w późniejszym czasie wewnątrz innego rozwiązania, możesz znaleźć je wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` katalogu.</span><span class="sxs-lookup"><span data-stu-id="02f9d-219">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="02f9d-220">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="02f9d-220">Next Steps</span></span>

<span data-ttu-id="02f9d-221">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="02f9d-221">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="02f9d-222">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="02f9d-222">Prepare and understand the data</span></span>
> * <span data-ttu-id="02f9d-223">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="02f9d-223">Choose a scenario</span></span>
> * <span data-ttu-id="02f9d-224">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="02f9d-224">Load the data</span></span>
> * <span data-ttu-id="02f9d-225">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="02f9d-225">Train the model</span></span>
> * <span data-ttu-id="02f9d-226">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="02f9d-226">Evaluate the model</span></span>
> * <span data-ttu-id="02f9d-227">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="02f9d-227">Use the model for predictions</span></span>

<span data-ttu-id="02f9d-228">Przejdź do jednej z następujących artykułów z instrukcjami, aby dowiedzieć się, jak wdrożyć model.</span><span class="sxs-lookup"><span data-stu-id="02f9d-228">Advance to either of the following how-to articles to learn how to deploy your model.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02f9d-229">Wdrażanie modelu w usłudze Azure Functions</span><span class="sxs-lookup"><span data-stu-id="02f9d-229">Deploy a model to Azure Functions</span></span>](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="02f9d-230">Wdrażanie modelu do internetowego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="02f9d-230">Deploy a model to a Web API</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
