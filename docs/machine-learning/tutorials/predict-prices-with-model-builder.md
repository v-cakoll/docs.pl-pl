---
title: 'Samouczek: Przewidywanie cen za pomocą regresji za pomocą Konstruktora modeli'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu ML.NET Model Builder do przewidywania cen, w szczególności, opłaty za taksówki w Nowym Jorku.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c027fe57f571c791784b0bdb7ad9503fc49daa1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187697"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="1bfc4-103">Samouczek: Przewidywanie cen za pomocą regresji za pomocą Konstruktora modeli</span><span class="sxs-lookup"><span data-stu-id="1bfc4-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="1bfc4-104">Dowiedz się, jak używać ML.NET Model Builder do tworzenia modelu regresji do przewidywania cen.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="1bfc4-105">Aplikacja konsoli .NET, który opracujesz w tym samouczku, przewiduje opłaty za przejazdtaksówką na podstawie historycznych danych taryfy taksówkowej w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="1bfc4-106">Szablon prognozowania cen konstruktora modeli może służyć dla każdego scenariusza wymagającego wartości przewidywania numerycznego.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="1bfc4-107">Przykładowe scenariusze to: przewidywanie cen domów, przewidywanie popytu i prognozowanie sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="1bfc4-108">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1bfc4-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1bfc4-109">Przygotowywanie i rozumienie danych</span><span class="sxs-lookup"><span data-stu-id="1bfc4-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="1bfc4-110">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="1bfc4-110">Choose a scenario</span></span>
> - <span data-ttu-id="1bfc4-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1bfc4-111">Load the data</span></span>
> - <span data-ttu-id="1bfc4-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="1bfc4-112">Train the model</span></span>
> - <span data-ttu-id="1bfc4-113">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="1bfc4-113">Evaluate the model</span></span>
> - <span data-ttu-id="1bfc4-114">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="1bfc4-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="1bfc4-115">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="1bfc4-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1bfc4-116">Pre-requisites</span></span>

<span data-ttu-id="1bfc4-117">Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, odwiedź [podręcznik instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="1bfc4-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="1bfc4-118">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="1bfc4-118">Create a console application</span></span>

1. <span data-ttu-id="1bfc4-119">Utwórz **aplikację C# .NET Core Console** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="1bfc4-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="1bfc4-120">Upewnij się, że **rozwiązanie i projekt w tym samym katalogu** są **zaznaczone** (VS 2019) lub **Zaznacz akcesornie utwórz katalog dla rozwiązania** (VS 2017). **checked**</span><span class="sxs-lookup"><span data-stu-id="1bfc4-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="1bfc4-121">Przygotowywanie i rozumienie danych</span><span class="sxs-lookup"><span data-stu-id="1bfc4-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="1bfc4-122">Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="1bfc4-123">Zestaw danych używany do szkolenia i oceny modelu uczenia maszynowego pochodzi z zestawu danych NYC TLC Taxi Trip.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="1bfc4-124">Aby pobrać zestaw danych, przejdź do [linku pobierania taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="1bfc4-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="1bfc4-125">Po załadowaniu strony kliknij prawym przyciskiem myszy dowolne miejsce na stronie i wybierz polecenie **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="1bfc4-126">Użyj **okna dialogowego Zapisz jako,** aby zapisać plik w folderze *Dane* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="1bfc4-127">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *taxi-fare-train.csv* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="1bfc4-128">W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="1bfc4-129">Każdy wiersz `taxi-fare-train.csv` w zestawie danych zawiera szczegółowe informacje o podróżach taksówką.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="1bfc4-130">Otwórz zestaw danych **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="1bfc4-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="1bfc4-131">Dostarczony zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="1bfc4-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="1bfc4-132">**vendor_id:** Identyfikator dostawcy taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="1bfc4-133">**rate_code:** Typ stawki podróży taksówką jest cechą.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="1bfc4-134">**passenger_count:** Liczba pasażerów w podróży jest cechą.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="1bfc4-135">**trip_time_in_secs:** Czas podróży.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="1bfc4-136">Chcesz przewidzieć taryfę podróży przed zakończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="1bfc4-137">W tym momencie nie wiesz, jak długo potrwa podróż.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="1bfc4-138">W związku z tym czas podróży nie jest funkcją i wykluczysz tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="1bfc4-139">**trip_distance:** Odległość podróży jest cechą.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="1bfc4-140">**payment_type:** Metoda płatności (gotówka lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="1bfc4-141">**fare_amount:** Całkowita opłata za przejazd taksówką jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="1bfc4-142">Jest `label` to kolumna, którą chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="1bfc4-143">Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="1bfc4-144">W tym scenariuszu przewidywania cen przewidywany jest koszt przejazdu taksówką.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="1bfc4-145">W związku z tym **fare_amount** jest etykieta.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="1bfc4-146">Zidentyfikowane `features` są dane wejściowe, które dajesz modelowi przewidzieć `label`.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="1bfc4-147">W takim przypadku pozostałe kolumny z wyjątkiem **trip_time_in_secs** są używane jako funkcje lub dane wejściowe do przewidywania kwoty taryfy.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="1bfc4-148">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="1bfc4-148">Choose a scenario</span></span>

<span data-ttu-id="1bfc4-149">Aby nabyć model, należy wybrać z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez Konstruktora modeli.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="1bfc4-150">W takim przypadku scenariusz `Price Prediction`jest .</span><span class="sxs-lookup"><span data-stu-id="1bfc4-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="1bfc4-151">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="1bfc4-152">W kroku scenariusza narzędzia Konstruktor modeli wybierz scenariusz *prognozowania cen.*</span><span class="sxs-lookup"><span data-stu-id="1bfc4-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="1bfc4-153">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1bfc4-153">Load the data</span></span>

<span data-ttu-id="1bfc4-154">ProgramKonystor modeli akceptuje dane z dwóch źródeł: bazy danych programu SQL Server lub pliku lokalnego w formacie csv lub tsv.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="1bfc4-155">W kroku danych narzędzia Konstruktor modeli wybierz pozycję *Plik* z listy rozwijanej źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="1bfc4-156">Wybierz przycisk obok pola *tekstowego Wybierz plik* i użyj Eksploratora plików, aby przeglądać i wybierać *taxi-fare-test.csv* w katalogu *Data*</span><span class="sxs-lookup"><span data-stu-id="1bfc4-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="1bfc4-157">Wybierz *fare_amount* z listy rozwijanej *Kolumna do przewidywania (etykieta).*</span><span class="sxs-lookup"><span data-stu-id="1bfc4-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="1bfc4-158">Rozwiń menu *rozwijane Kolumny wejściowe (Funkcje)* i usuń zaznaczenie kolumny *trip_time_in_secs,* aby wykluczyć ją jako obiekt podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="1bfc4-159">Przejdź do etapu pociągu narzędzia Konstruktor modeli.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="1bfc4-160">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="1bfc4-160">Train the model</span></span>

<span data-ttu-id="1bfc4-161">Zadaniem uczenia maszynowego używanym do uczenia modelu prognozowania cen w tym samouczku jest regresja.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="1bfc4-162">Podczas procesu szkolenia modelu Model Builder pociągów oddzielnych modeli przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć model o najlepszej wydajności dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="1bfc4-163">Czas wymagany do przeszkolenia modelu jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="1bfc4-164">Konstruktor modeli automatycznie wybiera wartość domyślną dla **time to train (seconds)** na podstawie rozmiaru źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="1bfc4-165">Pozostaw wartość domyślną, jak jest dla *Time to train (sekundy),* chyba że wolisz trenować przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="1bfc4-166">Wybierz *pozycję Rozpocznij szkolenie*.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-166">Select *Start Training*.</span></span>

<span data-ttu-id="1bfc4-167">W trakcie całego procesu szkolenia dane `Progress` postępu są wyświetlane w sekcji etapu pociągu.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="1bfc4-168">Stan wyświetla stan ukończenia procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="1bfc4-169">Najlepsza dokładność pokazuje dokładność najlepiej działającego modelu znalezionego do tej pory przez Model Builder.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="1bfc4-170">Większa dokładność oznacza, że model jest bardziej poprawnie przewidywany na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="1bfc4-171">Najlepszy algorytm wyświetla nazwę algorytmu o najlepszej wydajności, który został znaleziony do tej pory przez Konstruktora modeli.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="1bfc4-172">Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="1bfc4-173">Po zakończeniu szkolenia przejdź do kroku oceny.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="1bfc4-174">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="1bfc4-174">Evaluate the model</span></span>

<span data-ttu-id="1bfc4-175">Wynikiem etapu szkolenia będzie jeden model, który miał najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="1bfc4-176">W kroku oceny narzędzia Konstruktor modeli sekcja danych wyjściowych będzie zawierać algorytm używany przez model o najlepszej wydajności we wpisie *Najlepszy model* wraz z metrykami w *najlepszej jakości modelu (RSquared).*</span><span class="sxs-lookup"><span data-stu-id="1bfc4-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="1bfc4-177">Ponadto tabela podsumowania zawierająca pięć najlepszych modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="1bfc4-178">Jeśli nie jesteś zadowolony z metryk dokładności, kilka prostych sposobów, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="1bfc4-179">W przeciwnym razie przejdź do kroku kodu.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="1bfc4-180">Dodawanie kodu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="1bfc4-180">Add the code to make predictions</span></span>

<span data-ttu-id="1bfc4-181">W wyniku procesu szkoleniowego zostaną utworzone dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="1bfc4-182">TaxiFarePredictionML.ConsoleApp: Aplikacja .NET Core Console, która zawiera szkolenie modelu i przykładowy kod zużycia.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="1bfc4-183">TaxiFarePredictionML.Model: Biblioteka klas .NET Standard zawierająca modele danych definiujące schemat danych modelu wejściowego i wyjściowego, zapisaną `ConsumeModel` wersję modelu o najlepszej wydajności podczas szkolenia i klasę pomocnika wywoływaną do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="1bfc4-184">W kroku kodu narzędzia Konstruktor modeli wybierz pozycję **Dodaj projekty,** aby dodać automatycznie wygenerowane projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="1bfc4-185">Otwórz plik *Program.cs* w projekcie *TaxiFarePrediction.*</span><span class="sxs-lookup"><span data-stu-id="1bfc4-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="1bfc4-186">Dodaj następującą instrukcję, aby odwołać się do projektu *TaxiFarePredictionML.Model:*</span><span class="sxs-lookup"><span data-stu-id="1bfc4-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="1bfc4-187">Aby przewidzieć nowe dane przy użyciu modelu, należy `ModelInput` utworzyć `Main` nowe wystąpienie klasy wewnątrz metody aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="1bfc4-188">Należy zauważyć, że kwota taryfy nie jest częścią danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="1bfc4-189">Jest to spowodowane model wygeneruje przewidywanie dla niego.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-189">This is because the model will generate the prediction for it.</span></span>

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

1. <span data-ttu-id="1bfc4-190">Użyj `Predict` metody z `ConsumeModel` klasy.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="1bfc4-191">Metoda `Predict` ładuje uczonego [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) modelu, utworzyć dla modelu i używa go do prognozowania nowych danych.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="1bfc4-192">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-192">Run the application.</span></span>

    <span data-ttu-id="1bfc4-193">Dane wyjściowe wygenerowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:</span><span class="sxs-lookup"><span data-stu-id="1bfc4-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="1bfc4-194">Jeśli chcesz odwołać się do wygenerowanych projektów w późniejszym czasie wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` innego rozwiązania, można je znaleźć w katalogu.</span><span class="sxs-lookup"><span data-stu-id="1bfc4-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bfc4-195">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1bfc4-195">Next Steps</span></span>

<span data-ttu-id="1bfc4-196">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1bfc4-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1bfc4-197">Przygotowywanie i rozumienie danych</span><span class="sxs-lookup"><span data-stu-id="1bfc4-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="1bfc4-198">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="1bfc4-198">Choose a scenario</span></span>
> - <span data-ttu-id="1bfc4-199">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1bfc4-199">Load the data</span></span>
> - <span data-ttu-id="1bfc4-200">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="1bfc4-200">Train the model</span></span>
> - <span data-ttu-id="1bfc4-201">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="1bfc4-201">Evaluate the model</span></span>
> - <span data-ttu-id="1bfc4-202">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="1bfc4-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1bfc4-203">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="1bfc4-203">Additional Resources</span></span>

<span data-ttu-id="1bfc4-204">Aby dowiedzieć się więcej na tematy wymienione w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="1bfc4-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="1bfc4-205">Scenariusze konstruktora modeli</span><span class="sxs-lookup"><span data-stu-id="1bfc4-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="1bfc4-206">Regresji</span><span class="sxs-lookup"><span data-stu-id="1bfc4-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="1bfc4-207">Metryki modelu regresji</span><span class="sxs-lookup"><span data-stu-id="1bfc4-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="1bfc4-208">NYC TLC Taxi Trip zestaw danych</span><span class="sxs-lookup"><span data-stu-id="1bfc4-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
