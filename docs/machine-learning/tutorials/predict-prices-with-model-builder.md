---
title: 'Samouczek: Przewidywanie cen przy użyciu regresji za pomocą Kreatora modeli'
description: W tym samouczku pokazano, jak utworzyć model regresji przy użyciu ML.NET Model Builder do przewidywania cen, w szczególności, New York City opłat za taksówki.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: 750738f8e3c65363e9996667feeccd1b84391f9f
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438241"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="bb720-103">Samouczek: Przewidywanie cen przy użyciu regresji za pomocą Kreatora modeli</span><span class="sxs-lookup"><span data-stu-id="bb720-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="bb720-104">Dowiedz się, jak używać ML.NET Model Builder do tworzenia modelu regresji do przewidywania cen.</span><span class="sxs-lookup"><span data-stu-id="bb720-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="bb720-105">Aplikacja konsoli .NET, która została opracowyna w tym samouczku, przewiduje opłaty za taksówki na podstawie historycznych danych taryfy taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="bb720-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="bb720-106">Szablon prognozowania cen kreatora modeli może służyć do dowolnego scenariusza wymagającego wartości przewidywania liczbowego.</span><span class="sxs-lookup"><span data-stu-id="bb720-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="bb720-107">Przykładowe scenariusze obejmują: przewidywanie cen nieruchomości, przewidywanie popytu i prognozowanie sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="bb720-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="bb720-108">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bb720-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bb720-109">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="bb720-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="bb720-110">Wybieranie scenariusza</span><span class="sxs-lookup"><span data-stu-id="bb720-110">Choose a scenario</span></span>
> - <span data-ttu-id="bb720-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="bb720-111">Load the data</span></span>
> - <span data-ttu-id="bb720-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="bb720-112">Train the model</span></span>
> - <span data-ttu-id="bb720-113">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="bb720-113">Evaluate the model</span></span>
> - <span data-ttu-id="bb720-114">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="bb720-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="bb720-115">Kreator modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="bb720-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="bb720-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bb720-116">Pre-requisites</span></span>

<span data-ttu-id="bb720-117">Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, zapoznaj się z [podręcznikiem instalacji Kreatora modeli.](../how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="bb720-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="bb720-118">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="bb720-118">Create a console application</span></span>

1. <span data-ttu-id="bb720-119">Utwórz **aplikację konsoli .NET Core o** nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="bb720-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="bb720-120">Upewnij **się,** że rozwiązanie i projekt Umieść w tym samym katalogu **nie są zaznaczone** (VS 2019) lub **Sprawdź katalog** Create **dla rozwiązania** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="bb720-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="bb720-121">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="bb720-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="bb720-122">Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać pliki zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="bb720-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="bb720-123">Zestaw danych używany do uczenia i oceny modelu uczenia maszynowego pochodzi z zestawu danych NYC TLC Taxi Trip.</span><span class="sxs-lookup"><span data-stu-id="bb720-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="bb720-124">Aby pobrać zestaw danych, przejdź do linku do [pobrania taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="bb720-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="bb720-125">Po załadowaniu strony kliknij prawym przyciskiem myszy dowolne miejsce na stronie i wybierz pozycję **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="bb720-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="bb720-126">Użyj **okna dialogowego Zapisz jako,** aby zapisać plik w folderze *Dane* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="bb720-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="bb720-127">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *taxi-fare-train.csv* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="bb720-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="bb720-128">W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.</span><span class="sxs-lookup"><span data-stu-id="bb720-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="bb720-129">Każdy wiersz `taxi-fare-train.csv` w zestawie danych zawiera szczegóły podróży dokonywanych przez taksówkę.</span><span class="sxs-lookup"><span data-stu-id="bb720-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="bb720-130">Otwórz zestaw danych **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="bb720-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="bb720-131">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="bb720-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="bb720-132">**vendor_id:** Identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="bb720-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="bb720-133">**rate_code:** Rodzaj stawki podróży taksówką jest cechą.</span><span class="sxs-lookup"><span data-stu-id="bb720-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="bb720-134">**passenger_count:** Liczba pasażerów w podróży jest cechą.</span><span class="sxs-lookup"><span data-stu-id="bb720-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="bb720-135">**trip_time_in_secs:** Czas podróży trwał.</span><span class="sxs-lookup"><span data-stu-id="bb720-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="bb720-136">Chcesz przewidzieć taryfę podróży przed zakończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="bb720-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="bb720-137">W tym momencie nie wiesz, jak długo potrwa podróż.</span><span class="sxs-lookup"><span data-stu-id="bb720-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="bb720-138">W związku z tym czas podróży nie jest funkcją i wykluczysz tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="bb720-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="bb720-139">**trip_distance:** Odległość podróży jest cechą.</span><span class="sxs-lookup"><span data-stu-id="bb720-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="bb720-140">**payment_type:** Metoda płatności (gotówka lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="bb720-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="bb720-141">**fare_amount:** Całkowita opłata za przejazd taksówką jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="bb720-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="bb720-142">Jest `label` to kolumna, którą chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="bb720-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="bb720-143">Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="bb720-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="bb720-144">W tym scenariuszu przewidywania cen przewidywany jest koszt przejazdu taksówką.</span><span class="sxs-lookup"><span data-stu-id="bb720-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="bb720-145">W związku z tym **fare_amount** jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="bb720-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="bb720-146">Zidentyfikowane `features` są dane wejściowe, które można `label`podać model do przewidzenia .</span><span class="sxs-lookup"><span data-stu-id="bb720-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="bb720-147">W takim przypadku pozostałe kolumny z wyjątkiem **trip_time_in_secs** są używane jako funkcje lub dane wejściowe do przewidywania kwoty taryfy.</span><span class="sxs-lookup"><span data-stu-id="bb720-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="bb720-148">Wybieranie scenariusza</span><span class="sxs-lookup"><span data-stu-id="bb720-148">Choose a scenario</span></span>

<span data-ttu-id="bb720-149">Aby uszkolić model, należy wybrać z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez program Model Builder.</span><span class="sxs-lookup"><span data-stu-id="bb720-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="bb720-150">W takim przypadku scenariusz `Price Prediction`jest .</span><span class="sxs-lookup"><span data-stu-id="bb720-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="bb720-151">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.</span><span class="sxs-lookup"><span data-stu-id="bb720-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="bb720-152">W kroku scenariusza narzędzia Konstruktor modelu wybierz scenariusz *przewidywania cen.*</span><span class="sxs-lookup"><span data-stu-id="bb720-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="bb720-153">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="bb720-153">Load the data</span></span>

<span data-ttu-id="bb720-154">Kreator modeli akceptuje dane z dwóch źródeł: bazy danych programu SQL Server lub pliku lokalnego w formacie csv lub tsv.</span><span class="sxs-lookup"><span data-stu-id="bb720-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="bb720-155">W kroku danych narzędzia Konstruktor modelu wybierz pozycję *Plik* z listy rozwijanej źródła danych.</span><span class="sxs-lookup"><span data-stu-id="bb720-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="bb720-156">Zaznacz przycisk obok pola *tekstowego Wybierz plik* i użyj Eksploratora plików do przeglądania i wybierz *taxi-fare-test.csv* w katalogu *Danych*</span><span class="sxs-lookup"><span data-stu-id="bb720-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="bb720-157">Wybierz *fare_amount* z *listy rozwijanej Kolumna do przewidzenia (etykieta).*</span><span class="sxs-lookup"><span data-stu-id="bb720-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="bb720-158">Rozwiń *rozwijanie kolumny wejściowej (funkcje)* i odznacz *kolumnę trip_time_in_secs,* aby wykluczyć ją jako funkcję podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bb720-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="bb720-159">Przejdź do etapu pociągu narzędzia Kreator modelu.</span><span class="sxs-lookup"><span data-stu-id="bb720-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="bb720-160">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="bb720-160">Train the model</span></span>

<span data-ttu-id="bb720-161">Zadaniem uczenia maszynowego używanego do uczenia modelu przewidywania cen w tym samouczku jest regresja.</span><span class="sxs-lookup"><span data-stu-id="bb720-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="bb720-162">Podczas procesu szkolenia modelu Model Builder trenuje oddzielne modele przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć model o najwyższej wydajności dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="bb720-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="bb720-163">Czas wymagany do szkolenia modelu jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="bb720-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="bb720-164">Kreator modelu automatycznie wybiera wartość domyślną **dla czasu do wytrenowania (sekundy)** na podstawie rozmiaru źródła danych.</span><span class="sxs-lookup"><span data-stu-id="bb720-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="bb720-165">Pozostaw wartość domyślną, tak jak w *przypadku czasu na trening (sekundy),* chyba że wolisz trenować przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="bb720-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="bb720-166">Wybierz *pozycję Rozpocznij szkolenie*.</span><span class="sxs-lookup"><span data-stu-id="bb720-166">Select *Start Training*.</span></span>

<span data-ttu-id="bb720-167">W trakcie całego procesu szkolenia dane o `Progress` postępach są wyświetlane w sekcji kroku pociągu.</span><span class="sxs-lookup"><span data-stu-id="bb720-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="bb720-168">Stan wyświetla stan ukończenia procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bb720-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="bb720-169">Najlepsza dokładność wyświetla dokładność najlepszego modelu znalezionego do tej pory przez Model Builder.</span><span class="sxs-lookup"><span data-stu-id="bb720-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="bb720-170">Większa dokładność oznacza, że model przewidział bardziej poprawnie na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="bb720-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="bb720-171">Najlepszy algorytm wyświetla nazwę najlepiej działającego algorytmu wykonywanego do tej pory przez Model Builder.</span><span class="sxs-lookup"><span data-stu-id="bb720-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="bb720-172">Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez program Model Builder do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="bb720-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="bb720-173">Po zakończeniu szkolenia przejdź do kroku oceny.</span><span class="sxs-lookup"><span data-stu-id="bb720-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="bb720-174">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="bb720-174">Evaluate the model</span></span>

<span data-ttu-id="bb720-175">Wynikiem etapu szkolenia będzie jeden model, który miał najlepsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="bb720-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="bb720-176">W kroku oceny narzędzia Model Builder, sekcja danych wyjściowych, będzie zawierać algorytm używany przez model o najwyższej wydajności we wpisie *Najlepszy model* wraz z metrykami w najlepszej jakości *modelu (RSquared).*</span><span class="sxs-lookup"><span data-stu-id="bb720-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="bb720-177">Ponadto tabela podsumowania zawierająca pięć najlepszych modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="bb720-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="bb720-178">Jeśli nie jesteś zadowolony z metryk dokładności, niektóre proste sposoby, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych.</span><span class="sxs-lookup"><span data-stu-id="bb720-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="bb720-179">W przeciwnym razie przejdź do kroku kodu.</span><span class="sxs-lookup"><span data-stu-id="bb720-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="bb720-180">Dodaj kod, aby przewidywać</span><span class="sxs-lookup"><span data-stu-id="bb720-180">Add the code to make predictions</span></span>

<span data-ttu-id="bb720-181">W wyniku procesu szkolenia zostaną utworzone dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="bb720-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="bb720-182">TaxiFarePredictionML.ConsoleApp: Aplikacja .NET Core Console, która zawiera kod szkolenia modelu i przykładowego użycia.</span><span class="sxs-lookup"><span data-stu-id="bb720-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="bb720-183">TaxiFarePredictionML.Model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych modelu wejściowego i wyjściowego, `ConsumeModel` zapisaną wersję modelu o najwyższej skuteczności podczas szkolenia i klasę pomocniczą wywołaną do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="bb720-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="bb720-184">W kroku kodu narzędzia Kreator modelu wybierz pozycję **Dodaj projekty,** aby dodać automatycznie generowane projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bb720-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="bb720-185">Otwórz plik *Program.cs* w projekcie *TaxiFarePrediction.*</span><span class="sxs-lookup"><span data-stu-id="bb720-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="bb720-186">Dodaj następującą instrukcję using, aby odwołać się do projektu *TaxiFarePredictionML.Model:*</span><span class="sxs-lookup"><span data-stu-id="bb720-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="bb720-187">Aby przewidzieć na nowe dane przy użyciu modelu, `ModelInput` należy utworzyć `Main` nowe wystąpienie klasy wewnątrz metody aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb720-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="bb720-188">Należy zauważyć, że kwota taryfy nie jest częścią danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="bb720-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="bb720-189">Jest to spowodowane model wygeneruje przewidywanie dla niego.</span><span class="sxs-lookup"><span data-stu-id="bb720-189">This is because the model will generate the prediction for it.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="bb720-190">Użyj `Predict` metody z `ConsumeModel` klasy.</span><span class="sxs-lookup"><span data-stu-id="bb720-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="bb720-191">Metoda `Predict` ładuje przeszkolony model, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) utworzyć dla modelu i używa go do prognozowania na nowe dane.</span><span class="sxs-lookup"><span data-stu-id="bb720-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="bb720-192">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="bb720-192">Run the application.</span></span>

    <span data-ttu-id="bb720-193">Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu:</span><span class="sxs-lookup"><span data-stu-id="bb720-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="bb720-194">Jeśli chcesz odwołać się do wygenerowanych projektów w późniejszym czasie wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` innego rozwiązania, można je znaleźć w katalogu.</span><span class="sxs-lookup"><span data-stu-id="bb720-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bb720-195">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="bb720-195">Next Steps</span></span>

<span data-ttu-id="bb720-196">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bb720-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bb720-197">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="bb720-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="bb720-198">Wybieranie scenariusza</span><span class="sxs-lookup"><span data-stu-id="bb720-198">Choose a scenario</span></span>
> - <span data-ttu-id="bb720-199">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="bb720-199">Load the data</span></span>
> - <span data-ttu-id="bb720-200">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="bb720-200">Train the model</span></span>
> - <span data-ttu-id="bb720-201">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="bb720-201">Evaluate the model</span></span>
> - <span data-ttu-id="bb720-202">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="bb720-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bb720-203">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="bb720-203">Additional Resources</span></span>

<span data-ttu-id="bb720-204">Aby dowiedzieć się więcej o tematach wymienionych w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="bb720-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="bb720-205">Scenariusze konstruktora modeli</span><span class="sxs-lookup"><span data-stu-id="bb720-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="bb720-206">Regresji</span><span class="sxs-lookup"><span data-stu-id="bb720-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="bb720-207">Metryki modelu regresji</span><span class="sxs-lookup"><span data-stu-id="bb720-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="bb720-208">Zestaw danych NYC TLC Taxi Trip</span><span class="sxs-lookup"><span data-stu-id="bb720-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
