---
title: 'Samouczek: prognozowanie cen przy użyciu regresji z konstruktorem modelu'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu konstruktora modelu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 254f3c4c05a2c18f6182fc5f18d93114e20ed953
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344991"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="1a7d1-103">Samouczek: prognozowanie cen przy użyciu regresji z konstruktorem modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="1a7d1-104">Dowiedz się, jak za pomocą konstruktora modeli ML.NET utworzyć model regresji do przewidywania cen.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="1a7d1-105">Aplikacja konsolowa platformy .NET, którą opracowujesz w tym samouczku, przewiduje opłaty za taksówkę w oparciu o historyczne dane dotyczące opłat za taksówkę w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="1a7d1-106">Szablon prognozowania cen konstruktora modeli może być używany w każdym scenariuszu wymagającym wartości prognozowanych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="1a7d1-107">Przykładowe scenariusze obejmują: prognozowanie cen domu, prognozowanie popytu i prognozowanie sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="1a7d1-108">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1a7d1-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1a7d1-109">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="1a7d1-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="1a7d1-110">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="1a7d1-110">Choose a scenario</span></span>
> - <span data-ttu-id="1a7d1-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1a7d1-111">Load the data</span></span>
> - <span data-ttu-id="1a7d1-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-112">Train the model</span></span>
> - <span data-ttu-id="1a7d1-113">Ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-113">Evaluate the model</span></span>
> - <span data-ttu-id="1a7d1-114">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="1a7d1-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="1a7d1-115">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="1a7d1-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1a7d1-116">Pre-requisites</span></span>

<span data-ttu-id="1a7d1-117">Listę wymagań wstępnych i instrukcji instalacji można znaleźć w [podręczniku instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="1a7d1-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="1a7d1-118">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="1a7d1-118">Create a console application</span></span>

1. <span data-ttu-id="1a7d1-119">Utwórz  **C# aplikację konsolową .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="1a7d1-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="1a7d1-120">Upewnij się, że w tym samym katalogu nie jest **zaznaczone pole wyboru** **Umieść rozwiązanie i projekt** (vs 2019) lub pozycję **Utwórz katalog dla rozwiązania** jest **zaznaczone** (vs 2017).</span><span class="sxs-lookup"><span data-stu-id="1a7d1-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="1a7d1-121">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="1a7d1-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="1a7d1-122">Utwórz katalog o nazwie *dane* w projekcie, aby przechowywać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="1a7d1-123">Zestaw danych służący do uczenia i oszacowania modelu uczenia maszynowego jest pierwotnie z zestawu danych o podróży NYC TLC.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="1a7d1-124">Aby pobrać zestaw danych, przejdź do [linku pobierania Taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="1a7d1-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="1a7d1-125">Gdy strona zostanie załadowana, kliknij prawym przyciskiem myszy w dowolnym miejscu na stronie i wybierz polecenie **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="1a7d1-126">Użyj **okna dialogowego Zapisz jako** , aby zapisać plik w folderze *danych* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="1a7d1-127">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Taxi-Fare-Train. csv* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="1a7d1-128">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="1a7d1-129">Każdy wiersz w zestawie danych `taxi-fare-train.csv` zawiera szczegółowe informacje o podróży dokonywanych przez taksówkę.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="1a7d1-130">Otwórz zestaw danych **Taxi-Fare-Train. csv**</span><span class="sxs-lookup"><span data-stu-id="1a7d1-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="1a7d1-131">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="1a7d1-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="1a7d1-132">**vendor_id:** Identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="1a7d1-133">**rate_code:** Typ szybkości podróży z taksówką jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="1a7d1-134">**passenger_count:** Liczba pasażerów w podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="1a7d1-135">**trip_time_in_secs:** Czas trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="1a7d1-136">Chcesz przewidzieć przejazd podróży przed ukończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="1a7d1-137">W tym momencie nie wiesz, jak długo trwa podróż.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="1a7d1-138">W ten sposób czas podróży nie jest funkcją, a ta kolumna zostanie wykluczona z modelu.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="1a7d1-139">**trip_distance:** Odległość podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="1a7d1-140">**payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="1a7d1-141">**fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="1a7d1-142">`label` to kolumna, która ma zostać przewidywalna.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="1a7d1-143">Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="1a7d1-144">W tym scenariuszu prognozowania cen jest przewidywany koszt najazdy z taksówką.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="1a7d1-145">W związku z tym **fare_amount** jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="1a7d1-146">Zidentyfikowane `features` są danymi wejściowymi, które umożliwiają modelowi przewidywanie `label`.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="1a7d1-147">W takim przypadku pozostałe kolumny z wyjątkiem **trip_time_in_secs** są używane jako funkcje lub dane wejściowe do przewidywania kwoty opłat.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="1a7d1-148">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="1a7d1-148">Choose a scenario</span></span>

<span data-ttu-id="1a7d1-149">Aby szkolić model, musisz wybrać z listy dostępnych scenariuszy uczenia maszynowego udostępnianych przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="1a7d1-150">W takim przypadku scenariusz jest `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="1a7d1-151">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* i wybierz polecenie **Dodaj** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="1a7d1-152">W kroku scenariusz narzędzia model Builder wybierz opcję scenariusz *prognozowania cen* .</span><span class="sxs-lookup"><span data-stu-id="1a7d1-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="1a7d1-153">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1a7d1-153">Load the data</span></span>

<span data-ttu-id="1a7d1-154">Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych SQL Server lub pliku lokalnego w formacie CSV lub TSV.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="1a7d1-155">W kroku dane narzędzia model Builder wybierz pozycję *plik* z listy rozwijanej Źródło danych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="1a7d1-156">Wybierz przycisk obok pola tekstowego *Wybierz plik* i Użyj Eksploratora plików do przeglądania i wybierania *Taxi-Fare-test. csv* w katalogu *danych*</span><span class="sxs-lookup"><span data-stu-id="1a7d1-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="1a7d1-157">Wybierz *fare_amount* w *kolumnie do przewidywania (etykieta)* listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="1a7d1-158">Rozwiń listę rozwijaną *kolumny wejściowe (funkcje)* i usuń zaznaczenie kolumny *trip_time_in_secs* , aby wykluczyć ją jako funkcję podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="1a7d1-159">Przejdź do kroku uczenia narzędzia model Builder.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="1a7d1-160">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-160">Train the model</span></span>

<span data-ttu-id="1a7d1-161">Zadanie uczenia maszynowego używane do uczenia modelu prognozowania cen w tym samouczku to regresja.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="1a7d1-162">W trakcie procesu szkolenia modelu, Konstruktor modelu pociąga za siebie różne modele przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć najlepszy model dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="1a7d1-163">Czas wymagany przez model do uczenia jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="1a7d1-164">Konstruktor modelu automatycznie wybiera wartość domyślną dla **czasu do uczenia (w sekundach)** na podstawie rozmiaru źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="1a7d1-165">Pozostaw wartość domyślną jako *czas do uczenia (w sekundach)* , chyba że wolisz dłużej uczenie się przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="1a7d1-166">Wybierz pozycję *Rozpocznij szkolenie*.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-166">Select *Start Training*.</span></span>

<span data-ttu-id="1a7d1-167">W trakcie całego procesu szkolenia dane o postępie są wyświetlane w sekcji `Progress` kroku uczenie.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="1a7d1-168">Stan przedstawia stan zakończenia procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="1a7d1-169">Najlepsza dokładność przedstawia dokładność najlepszego modelu, który został znaleziony przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="1a7d1-170">Większa dokładność oznacza, że model przewidywalno dokładniej na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="1a7d1-171">Najlepszym algorytmem jest wyświetlana nazwa najlepszego wykonywania algorytmu, który został wykonany przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="1a7d1-172">Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="1a7d1-173">Po zakończeniu szkolenia przejdź do kroku szacowania.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="1a7d1-174">Ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-174">Evaluate the model</span></span>

<span data-ttu-id="1a7d1-175">Wynikiem kroku szkolenia będzie jeden model, który miał najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="1a7d1-176">W kroku szacowania narzędzia model Builder sekcja Output będzie zawierać algorytm używany przez model najlepszego wykonywania w najlepszym wpisie *modelu* oraz metryki w *najlepszej jakości modelu (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="1a7d1-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="1a7d1-177">Ponadto tabela podsumowująca zawierająca pięć najważniejszych modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="1a7d1-178">Jeśli Twoje metryki dokładności nie są zadowalające, niektóre proste sposoby wypróbowania i poprawienia dokładności modelu mają na celu zwiększenie ilości czasu na nauczenie modelu lub użycie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="1a7d1-179">W przeciwnym razie przejdź do kroku kodu.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="1a7d1-180">Dodaj kod, aby tworzyć przewidywania</span><span class="sxs-lookup"><span data-stu-id="1a7d1-180">Add the code to make predictions</span></span>

<span data-ttu-id="1a7d1-181">W wyniku procesu szkolenia zostaną utworzone dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="1a7d1-182">TaxiFarePredictionML. ConsoleApp: Aplikacja konsolowa platformy .NET Core, która zawiera model szkoleń i przykładowego kodu zużycia.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="1a7d1-183">TaxiFarePredictionML. model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych wejściowych i wyjściowych, zapisana wersja modelu najlepszego przebiegu podczas szkolenia i klasy pomocnika o nazwie `ConsumeModel` do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="1a7d1-184">W kroku Code narzędzia model Builder wybierz pozycję **Dodaj projekty** , aby dodać automatycznie generowane projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="1a7d1-185">Otwórz plik *program.cs* w projekcie *TaxiFarePrediction* .</span><span class="sxs-lookup"><span data-stu-id="1a7d1-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="1a7d1-186">Dodaj następującą instrukcję using, aby odwołać się do projektu *TaxiFarePredictionML. model* :</span><span class="sxs-lookup"><span data-stu-id="1a7d1-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="1a7d1-187">Aby przeprowadzić prognozowanie nowych danych przy użyciu modelu, Utwórz nowe wystąpienie klasy `ModelInput` wewnątrz metody `Main` aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="1a7d1-188">Zwróć uwagę, że opłata za opłaty nie jest częścią danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="1a7d1-189">Dzieje się tak, ponieważ model generuje dla niego prognozę.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-189">This is because the model will generate the prediction for it.</span></span>

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

1. <span data-ttu-id="1a7d1-190">Użyj metody `Predict` z klasy `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="1a7d1-191">Metoda `Predict` ładuje przeszkolony model, tworzy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dla modelu i używa go do prognozowania nowych danych.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="1a7d1-192">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-192">Run the application.</span></span>

    <span data-ttu-id="1a7d1-193">Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:</span><span class="sxs-lookup"><span data-stu-id="1a7d1-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="1a7d1-194">Jeśli musisz odwoływać się do wygenerowanych projektów w późniejszym czasie w innym rozwiązaniu, możesz je znaleźć w katalogu `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1a7d1-195">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1a7d1-195">Next Steps</span></span>

<span data-ttu-id="1a7d1-196">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1a7d1-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1a7d1-197">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="1a7d1-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="1a7d1-198">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="1a7d1-198">Choose a scenario</span></span>
> - <span data-ttu-id="1a7d1-199">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1a7d1-199">Load the data</span></span>
> - <span data-ttu-id="1a7d1-200">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-200">Train the model</span></span>
> - <span data-ttu-id="1a7d1-201">Ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-201">Evaluate the model</span></span>
> - <span data-ttu-id="1a7d1-202">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="1a7d1-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1a7d1-203">Dodatkowe materiały</span><span class="sxs-lookup"><span data-stu-id="1a7d1-203">Additional Resources</span></span>

<span data-ttu-id="1a7d1-204">Aby dowiedzieć się więcej na temat tematów wymienionych w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="1a7d1-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="1a7d1-205">Scenariusze konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="1a7d1-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="1a7d1-206">Regression</span><span class="sxs-lookup"><span data-stu-id="1a7d1-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="1a7d1-207">Metryki modelu regresji</span><span class="sxs-lookup"><span data-stu-id="1a7d1-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="1a7d1-208">Zestaw danych podróży NYC TLC</span><span class="sxs-lookup"><span data-stu-id="1a7d1-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
