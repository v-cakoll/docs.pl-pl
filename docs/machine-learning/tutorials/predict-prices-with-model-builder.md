---
title: Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen
description: W tym samouczku pokazano, jak do zbudowania modelu regresji przy użyciu konstruktora modeli strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d8c901a10c91c8a6c16ca59516b633a99785ebac
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238567"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="7b1c1-103">Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen</span><span class="sxs-lookup"><span data-stu-id="7b1c1-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="7b1c1-104">Dowiedz się, jak tworzyć model() regresji, do prognozowania cen za pomocą konstruktora modelu strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="7b1c1-105">Aplikacji konsolowej .NET, który tworzysz w tym samouczku przewiduje taksówek opłatami na podstawie danych historycznych taryfy taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="7b1c1-106">Szablon prognozowania ceny konstruktora modelu może być używany dla dowolnych scenariuszy wymaga wartości liczbowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="7b1c1-107">Przykładowe scenariusze obejmują: lokalne Prognozowanie cen, przewidywanie zapotrzebowania i Prognozowanie sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="7b1c1-108">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7b1c1-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7b1c1-109">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="7b1c1-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="7b1c1-110">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="7b1c1-110">Choose a scenario</span></span>
> * <span data-ttu-id="7b1c1-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="7b1c1-111">Load the data</span></span>
> * <span data-ttu-id="7b1c1-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-112">Train the model</span></span>
> * <span data-ttu-id="7b1c1-113">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-113">Evaluate the model</span></span>
> * <span data-ttu-id="7b1c1-114">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="7b1c1-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="7b1c1-115">Konstruktor modelu jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="7b1c1-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7b1c1-116">Pre-requisites</span></span>

<span data-ttu-id="7b1c1-117">Aby uzyskać listę wymagań wstępnych i instrukcje dotyczące instalacji, odwiedź stronę [Przewodnik instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="7b1c1-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7b1c1-118">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="7b1c1-118">Create a console application</span></span>

1. <span data-ttu-id="7b1c1-119">Tworzenie **aplikacji konsoli .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="7b1c1-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="7b1c1-120">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="7b1c1-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="7b1c1-121">Utwórz katalog o nazwie *danych* w projekcie mają być przechowywane pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="7b1c1-122">Zestaw danych używany do nauczanie i ocena modeli usługi machine learning jest pierwotnie z zestawu danych NYC TLC taksówek podróży.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span> 

    <span data-ttu-id="7b1c1-123">Aby pobrać zestaw danych, przejdź do [link pobierania taksówek taryfy train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="7b1c1-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span> 
    
    <span data-ttu-id="7b1c1-124">Po załadowaniu strony, kliknij prawym przyciskiem myszy na stronie i wybierz **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span> 
    
    <span data-ttu-id="7b1c1-125">Użyj **Zapisz jako okno dialogowe** Aby zapisać plik w *danych* folderu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span> 
    
1. <span data-ttu-id="7b1c1-126">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *taksówek taryfy train.csv* plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="7b1c1-127">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="7b1c1-128">Każdy wiersz w `taxi-fare-train.csv` zestaw danych zawiera szczegółowe informacje o wymianie danych wprowadzonych przez taksówek.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="7b1c1-129">Otwórz **taksówek taryfy train.csv** zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7b1c1-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="7b1c1-130">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="7b1c1-130">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="7b1c1-131">**vendor_id:** Identyfikator dostawcy taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="7b1c1-132">**rate_code:** Typ stawki podróży taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="7b1c1-133">**passenger_count:** Liczba osób w ramach wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="7b1c1-134">**trip_time_in_secs:** Ilość czasu trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> 
    * <span data-ttu-id="7b1c1-135">**trip_distance:** Odległość wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="7b1c1-136">**payment_type:** Sposób zapłaty (pieniężnych lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="7b1c1-137">**fare_amount:** Taryfy taksówek łączna liczba płatnych jest etykieta.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="7b1c1-138">`label` Kolumna, która chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="7b1c1-139">Podczas wykonywania zadania regresji, celem jest do przewidywania wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="7b1c1-140">W tym scenariuszu prognozowania ceny przewiduje koszt jazdy taksówek.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="7b1c1-141">W związku z tym **fare_amount** jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="7b1c1-142">Wskazywanego przez nią `features` to dane wejściowe, nadaj model do przewidywania `label`.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="7b1c1-143">W takim przypadku pozostałe kolumny są używane jako funkcje lub danych wejściowych do prognozowania kwota klasie.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="7b1c1-144">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="7b1c1-144">Choose a scenario</span></span>

<span data-ttu-id="7b1c1-145">Do nauczenia modelu, należy wybrać z listy dostępnych usługi machine learning scenariuszy dostarczone przez Konstruktor modelu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="7b1c1-146">W tym przypadku jest to scenariusz `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-146">In this case, the scenario is `Price Prediction`.</span></span> 

1. <span data-ttu-id="7b1c1-147">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu, a następnie wybierz **Dodaj** > **uczenia maszynowego**.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="7b1c1-148">W kroku scenariusza narzędzia Konstruktor modelu, wybierz *Prognozowanie cen* scenariusza.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="7b1c1-149">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="7b1c1-149">Load the data</span></span>

<span data-ttu-id="7b1c1-150">Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych programu SQL Server lub lokalny plik w formacie csv lub tsv.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span> 

1. <span data-ttu-id="7b1c1-151">W kroku danych narzędzia Konstruktor modelu, wybierz *pliku* z listy rozwijanej źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="7b1c1-152">Kliknij przycisk Dalej, aby *wybierz plik* pole tekstowe i użyj Eksploratora plików, przeglądania i wybierania *taksówek taryfy test.csv* w *danych* katalogu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="7b1c1-153">Wybierz *fare_amount* w *etykiety lub kolumny Predict* listy rozwijanej i przejdź do kroku train narzędzia Konstruktor modelu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="7b1c1-154">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-154">Train the model</span></span>

<span data-ttu-id="7b1c1-155">Używane do trenowania modelu prognozowania ceny w tym samouczku zadania uczenia maszynowego jest regresji.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="7b1c1-156">W trakcie szkolenia modelu konstruktora modeli szkolenie modeli na osobne modele przy użyciu regresji różnych algorytmów i ustawienia, aby znaleźć najlepiej działający model dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="7b1c1-157">Czas wymagany do do nauczenia modelu jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="7b1c1-158">Skorzystaj z tej tabeli jako wskazówki wybrać odpowiednią wartość `Time to train (seconds)` pola:</span><span class="sxs-lookup"><span data-stu-id="7b1c1-158">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="7b1c1-159">\* Rozmiar zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7b1c1-159">\*Dataset Size</span></span>  | <span data-ttu-id="7b1c1-160">Typ zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7b1c1-160">Dataset Type</span></span>       | <span data-ttu-id="7b1c1-161">Średni Czas do pociągu \*</span><span class="sxs-lookup"><span data-stu-id="7b1c1-161">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="7b1c1-162">0 - 10 mb</span><span class="sxs-lookup"><span data-stu-id="7b1c1-162">0 - 10 Mb</span></span>     | <span data-ttu-id="7b1c1-163">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="7b1c1-163">Numeric and Text</span></span>   | <span data-ttu-id="7b1c1-164">10 s</span><span class="sxs-lookup"><span data-stu-id="7b1c1-164">10 sec</span></span>
<span data-ttu-id="7b1c1-165">10 - 100 mb</span><span class="sxs-lookup"><span data-stu-id="7b1c1-165">10 - 100 Mb</span></span>   | <span data-ttu-id="7b1c1-166">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="7b1c1-166">Numeric and Text</span></span>   | <span data-ttu-id="7b1c1-167">10-minutowy materiał</span><span class="sxs-lookup"><span data-stu-id="7b1c1-167">10 min</span></span>
<span data-ttu-id="7b1c1-168">100 – 500 mb</span><span class="sxs-lookup"><span data-stu-id="7b1c1-168">100 - 500 Mb</span></span>  | <span data-ttu-id="7b1c1-169">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="7b1c1-169">Numeric and Text</span></span>   | <span data-ttu-id="7b1c1-170">30 minut</span><span class="sxs-lookup"><span data-stu-id="7b1c1-170">30 min</span></span>
<span data-ttu-id="7b1c1-171">500 — 1 Gb</span><span class="sxs-lookup"><span data-stu-id="7b1c1-171">500 - 1 Gb</span></span>    | <span data-ttu-id="7b1c1-172">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="7b1c1-172">Numeric and Text</span></span>   | <span data-ttu-id="7b1c1-173">60-minutowe</span><span class="sxs-lookup"><span data-stu-id="7b1c1-173">60 min</span></span>
<span data-ttu-id="7b1c1-174">1 Gb+</span><span class="sxs-lookup"><span data-stu-id="7b1c1-174">1 Gb+</span></span>         | <span data-ttu-id="7b1c1-175">Liczbowe i tekstowe</span><span class="sxs-lookup"><span data-stu-id="7b1c1-175">Numeric and Text</span></span>   | <span data-ttu-id="7b1c1-176">3 godziny +</span><span class="sxs-lookup"><span data-stu-id="7b1c1-176">3 hour+</span></span>

1. <span data-ttu-id="7b1c1-177">Ponieważ plik danych szkoleniowych więcej niż 10MB, należy użyć 600 sekund (10 minut), jako wartość pozycji *czas na nauczenie (w sekundach)* .</span><span class="sxs-lookup"><span data-stu-id="7b1c1-177">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="7b1c1-178">Wybierz *Rozpocznij szkolenie*.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-178">Select *Start Training*.</span></span>

<span data-ttu-id="7b1c1-179">Przez cały proces szkolenia postępu dane są wyświetlane w `Progress` części kroku pociągu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-179">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="7b1c1-180">Stan wyświetlany stan ukończenia procesu uczenia.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-180">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="7b1c1-181">Najlepsze dokładności Wyświetla dokładność najlepiej działający model znalezione przez konstruktora modeli do tej pory.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-181">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="7b1c1-182">Większą dokładność oznacza, że model przewiduje właściwie na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-182">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="7b1c1-183">Najlepszy algorytm Wyświetla nazwę algorytmu działają najlepiej wykonać znalezione przez konstruktora modeli do tej pory.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-183">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="7b1c1-184">Ostatni algorytm Wyświetla nazwę algorytmu do nauczenia modelu, ostatnio używane przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-184">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="7b1c1-185">Po zakończeniu szkolenia, przejdź do kroku evaluate.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-185">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="7b1c1-186">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-186">Evaluate the model</span></span>

<span data-ttu-id="7b1c1-187">Wynik kroku szkolenia będzie jednego modelu, który ma najwyższą wydajność.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-187">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="7b1c1-188">W kroku evaluate narzędzia Konstruktor modelu, w sekcji danych wyjściowych będzie zawierać algorytmów używanych przez funkcję najlepiej działający model w *najlepszy Model* wpisu wraz z metrykami w *Najlepsza jakość modeli (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="7b1c1-188">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="7b1c1-189">Ponadto podsumowanie tabelę zawierającą pięć modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-189">Additionally, a summary table containing top five models and their metrics.</span></span> 

<span data-ttu-id="7b1c1-190">Jeśli nie jesteś zadowolony z metryk dokładności, niektóre łatwy sposób zwiększenia dokładności modelu i spróbuj mają zwiększyć ilość czasu do nauczenia modelu, lub Użyj większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-190">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="7b1c1-191">W przeciwnym razie przejdź do kroku kodu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-191">Otherwise, navigate to the code step.</span></span> 

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="7b1c1-192">Dodaj kod, aby tworzyć prognozy</span><span class="sxs-lookup"><span data-stu-id="7b1c1-192">Add the code to make predictions</span></span>

<span data-ttu-id="7b1c1-193">Dwa projekty zostaną utworzone w wyniku procesu uczenia.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-193">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="7b1c1-194">TaxiFarePredictionML.ConsoleApp: Aplikacja Konsolowa .NET Core, która zawiera kod, szkolenia i użycie modelu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-194">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="7b1c1-195">TaxiFarePredictionML.Model: Biblioteki klas .NET Standard zawierający modeli danych, które zdefiniować schemat danych wejściowych i wyjściowych modelu danych, a także utrwalonych wersję najlepiej działający model podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-195">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>


1. <span data-ttu-id="7b1c1-196">W kroku kodu narzędzia Konstruktor modelu, wybierz **dodać projekty** dodać generowanych automatycznie projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-196">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="7b1c1-197">Kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-197">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="7b1c1-198">Następnie **Dodaj > dokumentacja**.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-198">Then, **Add > Reference**.</span></span> <span data-ttu-id="7b1c1-199">Wybierz **projektów > rozwiązania** węzła i z listy, sprawdź *TaxiFarePredictionML.Model* projektu, a następnie wybierz przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-199">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="7b1c1-200">Otwórz *Program.cs* w pliku *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-200">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="7b1c1-201">Dodaj następujące za pomocą instrukcji, aby odwołać się do *Microsoft.ML* pakietu NuGet i *TaxiFarePredictionML.Model* projektu:</span><span class="sxs-lookup"><span data-stu-id="7b1c1-201">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>


    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="7b1c1-202">Dodaj `ConsumeModel` metody `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-202">Add the `ConsumeModel` method to the `Program` class.</span></span> 

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

    <span data-ttu-id="7b1c1-203">`ConsumeModel` Będzie załadować trenowanego modelu, tworzenie [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) modelu i użyj jej do prognozowania na nowych danych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-203">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

7. <span data-ttu-id="7b1c1-204">Przewiduje nowe dane przy użyciu modelu, należy utworzyć nowe wystąpienie klasy `ModelInput` klasy i użyć `ConsumeModel` metody.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-204">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="7b1c1-205">Należy zauważyć, że kwota taryfy nie jest częścią danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-205">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="7b1c1-206">Jest to spowodowane modelu spowoduje wygenerowanie prognoz dla niego.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-206">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="7b1c1-207">Dodaj następujący kod do `Main` metody i uruchom aplikację</span><span class="sxs-lookup"><span data-stu-id="7b1c1-207">Add the following code to the `Main` method and run the application</span></span>

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

    <span data-ttu-id="7b1c1-208">Dane wyjściowe generowane przez program powinien wyglądać podobnie jak poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="7b1c1-208">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="7b1c1-209">Jeśli musisz odwoływać się do wygenerowanego projektów w późniejszym czasie wewnątrz innego rozwiązania, możesz znaleźć je wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` katalogu.</span><span class="sxs-lookup"><span data-stu-id="7b1c1-209">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7b1c1-210">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7b1c1-210">Next Steps</span></span>

<span data-ttu-id="7b1c1-211">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7b1c1-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7b1c1-212">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="7b1c1-212">Prepare and understand the data</span></span>
> * <span data-ttu-id="7b1c1-213">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="7b1c1-213">Choose a scenario</span></span>
> * <span data-ttu-id="7b1c1-214">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="7b1c1-214">Load the data</span></span>
> * <span data-ttu-id="7b1c1-215">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-215">Train the model</span></span>
> * <span data-ttu-id="7b1c1-216">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-216">Evaluate the model</span></span>
> * <span data-ttu-id="7b1c1-217">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="7b1c1-217">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7b1c1-218">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7b1c1-218">Additional Resources</span></span>

<span data-ttu-id="7b1c1-219">Aby dowiedzieć się więcej na temat tematy wymienione w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="7b1c1-219">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="7b1c1-220">Scenariusze konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-220">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="7b1c1-221">Formaty danych konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="7b1c1-221">Model Builder Data Formats</span></span>](../automate-training-with-model-builder.md#data-formats)
- [<span data-ttu-id="7b1c1-222">Regression</span><span class="sxs-lookup"><span data-stu-id="7b1c1-222">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="7b1c1-223">Metryki modelu regresji</span><span class="sxs-lookup"><span data-stu-id="7b1c1-223">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="7b1c1-224">Zestaw danych podróży taksówek TLC NYC</span><span class="sxs-lookup"><span data-stu-id="7b1c1-224">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
