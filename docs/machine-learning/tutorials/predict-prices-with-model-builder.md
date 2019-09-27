---
title: 'Samouczek: Przewidywanie cen przy użyciu regresji z konstruktorem modelu'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu konstruktora modelu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
author: luisquintanilla
ms.author: luquinta
ms.date: 09/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c7075e64738279cd712f5db837074a44e96db954
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332594"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="c4c11-103">Samouczek: Przewidywanie cen przy użyciu regresji z konstruktorem modelu</span><span class="sxs-lookup"><span data-stu-id="c4c11-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="c4c11-104">Dowiedz się, jak za pomocą konstruktora modeli ML.NET utworzyć model regresji () w celu przewidywania cen.</span><span class="sxs-lookup"><span data-stu-id="c4c11-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="c4c11-105">Aplikacja konsolowa platformy .NET, którą opracowujesz w tym samouczku, przewiduje opłaty za taksówkę w oparciu o historyczne dane dotyczące opłat za taksówkę w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="c4c11-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="c4c11-106">Szablon prognozowania cen konstruktora modeli może być używany w każdym scenariuszu wymagającym wartości prognozowanych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="c4c11-107">Przykładowe scenariusze obejmują: prognozowanie cen domu, prognozowanie popytu i prognozowanie sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="c4c11-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="c4c11-108">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c4c11-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="c4c11-109">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="c4c11-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="c4c11-110">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="c4c11-110">Choose a scenario</span></span>
> - <span data-ttu-id="c4c11-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="c4c11-111">Load the data</span></span>
> - <span data-ttu-id="c4c11-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="c4c11-112">Train the model</span></span>
> - <span data-ttu-id="c4c11-113">Oceń model</span><span class="sxs-lookup"><span data-stu-id="c4c11-113">Evaluate the model</span></span>
> - <span data-ttu-id="c4c11-114">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="c4c11-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="c4c11-115">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="c4c11-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="c4c11-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c4c11-116">Pre-requisites</span></span>

<span data-ttu-id="c4c11-117">Listę wymagań wstępnych i instrukcji instalacji można znaleźć w [podręczniku instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="c4c11-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c4c11-118">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="c4c11-118">Create a console application</span></span>

1. <span data-ttu-id="c4c11-119">Utwórz **aplikację konsolową .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="c4c11-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="c4c11-120">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="c4c11-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="c4c11-121">Utwórz katalog o nazwie *dane* w projekcie, aby przechowywać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="c4c11-122">Zestaw danych służący do uczenia i oszacowania modelu uczenia maszynowego jest pierwotnie z zestawu danych o podróży NYC TLC.</span><span class="sxs-lookup"><span data-stu-id="c4c11-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="c4c11-123">Aby pobrać zestaw danych, przejdź do linku [pobierania Taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="c4c11-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="c4c11-124">Gdy strona zostanie załadowana, kliknij prawym przyciskiem myszy w dowolnym miejscu na stronie i wybierz polecenie **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="c4c11-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="c4c11-125">Użyj **okna dialogowego Zapisz jako** , aby zapisać plik w folderze *danych* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="c4c11-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="c4c11-126">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Taxi-Fare-Train. csv* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c4c11-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="c4c11-127">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="c4c11-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="c4c11-128">Każdy wiersz w `taxi-fare-train.csv` zestawie danych zawiera szczegółowe informacje o podróży dokonywanych przez taksówkę.</span><span class="sxs-lookup"><span data-stu-id="c4c11-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="c4c11-129">Otwórz zestaw danych **Taxi-Fare-Train. csv**</span><span class="sxs-lookup"><span data-stu-id="c4c11-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="c4c11-130">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="c4c11-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="c4c11-131">**vendor_id:** Identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="c4c11-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="c4c11-132">**rate_code:** Typ szybkości podróży z taksówką jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="c4c11-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="c4c11-133">**passenger_count:** Liczba pasażerów w podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="c4c11-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="c4c11-134">**trip_time_in_secs:** Czas trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="c4c11-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="c4c11-135">Chcesz przewidzieć przejazd podróży przed ukończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="c4c11-135">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="c4c11-136">W tym momencie nie wiesz, jak długo trwa podróż.</span><span class="sxs-lookup"><span data-stu-id="c4c11-136">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="c4c11-137">W ten sposób czas podróży nie jest funkcją, a ta kolumna zostanie wykluczona z modelu.</span><span class="sxs-lookup"><span data-stu-id="c4c11-137">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="c4c11-138">**trip_distance:** Odległość podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="c4c11-138">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="c4c11-139">**payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.</span><span class="sxs-lookup"><span data-stu-id="c4c11-139">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="c4c11-140">**fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.</span><span class="sxs-lookup"><span data-stu-id="c4c11-140">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="c4c11-141">`label` Jest to kolumna, która ma zostać przewidywalna.</span><span class="sxs-lookup"><span data-stu-id="c4c11-141">The `label` is the column you want to predict.</span></span> <span data-ttu-id="c4c11-142">Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="c4c11-142">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="c4c11-143">W tym scenariuszu prognozowania cen jest przewidywany koszt najazdy z taksówką.</span><span class="sxs-lookup"><span data-stu-id="c4c11-143">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="c4c11-144">W związku z tym **fare_amount** jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="c4c11-144">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="c4c11-145">Identyfikowane `features` są dane wejściowe, które dają model do `label`przewidywania.</span><span class="sxs-lookup"><span data-stu-id="c4c11-145">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="c4c11-146">W takim przypadku pozostałe kolumny z wyjątkiem **trip_time_in_secs** są używane jako funkcje lub dane wejściowe do przewidywania kwoty opłat.</span><span class="sxs-lookup"><span data-stu-id="c4c11-146">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="c4c11-147">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="c4c11-147">Choose a scenario</span></span>

<span data-ttu-id="c4c11-148">Aby szkolić model, musisz wybrać z listy dostępnych scenariuszy uczenia maszynowego udostępnianych przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="c4c11-148">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="c4c11-149">W tym przypadku scenariuszem jest `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="c4c11-149">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="c4c11-150">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* , a następnie wybierz pozycję **Dodaj** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="c4c11-150">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="c4c11-151">W kroku scenariusz narzędzia model Builder wybierz opcję scenariusz prognozowania *cen* .</span><span class="sxs-lookup"><span data-stu-id="c4c11-151">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="c4c11-152">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="c4c11-152">Load the data</span></span>

<span data-ttu-id="c4c11-153">Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych SQL Server lub pliku lokalnego w formacie CSV lub TSV.</span><span class="sxs-lookup"><span data-stu-id="c4c11-153">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="c4c11-154">W kroku dane narzędzia model Builder wybierz pozycję *plik* z listy rozwijanej Źródło danych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-154">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="c4c11-155">Wybierz przycisk obok pola tekstowego *Wybierz plik* i Użyj Eksploratora plików do przeglądania i wybierania *Taxi-Fare-test. csv* w katalogu *danych*</span><span class="sxs-lookup"><span data-stu-id="c4c11-155">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="c4c11-156">Wybierz pozycję *fare_amount* w *kolumnie do przewidywania (etykieta)* , a następnie przejdź do kroku uczenia narzędzia model Builder.</span><span class="sxs-lookup"><span data-stu-id="c4c11-156">Choose *fare_amount* in the *Column to Predict (Label)* dropdown and navigate to the train step of the Model Builder tool.</span></span>
1. <span data-ttu-id="c4c11-157">Rozwiń listę rozwijaną *kolumny wejściowe (funkcje)* i usuń zaznaczenie kolumny *trip_time_in_secs* , aby wykluczyć ją jako funkcję podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="c4c11-157">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="c4c11-158">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="c4c11-158">Train the model</span></span>

<span data-ttu-id="c4c11-159">Zadanie uczenia maszynowego używane do uczenia modelu prognozowania cen w tym samouczku to regresja.</span><span class="sxs-lookup"><span data-stu-id="c4c11-159">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="c4c11-160">W trakcie procesu szkolenia modelu, Konstruktor modelu pociąga za siebie różne modele przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć najlepszy model dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-160">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="c4c11-161">Czas wymagany przez model do uczenia jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="c4c11-162">Konstruktor modelu automatycznie wybiera wartość domyślną dla **czasu do uczenia (w sekundach)** na podstawie rozmiaru źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="c4c11-163">Pozostaw wartość domyślną jako *czas do uczenia (w sekundach)* , chyba że wolisz dłużej uczenie się przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="c4c11-163">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="c4c11-164">Wybierz pozycję *Rozpocznij szkolenie*.</span><span class="sxs-lookup"><span data-stu-id="c4c11-164">Select *Start Training*.</span></span>

<span data-ttu-id="c4c11-165">W trakcie całego procesu szkolenia dane o postępie są wyświetlane `Progress` w sekcji kroku uczenie.</span><span class="sxs-lookup"><span data-stu-id="c4c11-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="c4c11-166">Stan przedstawia stan zakończenia procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="c4c11-166">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="c4c11-167">Najlepsza dokładność przedstawia dokładność najlepszego modelu, który został znaleziony przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="c4c11-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="c4c11-168">Większa dokładność oznacza, że model przewidywalno dokładniej na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="c4c11-169">Najlepszym algorytmem jest wyświetlana nazwa najlepszego wykonywania algorytmu, który został wykonany przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="c4c11-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="c4c11-170">Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="c4c11-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="c4c11-171">Po zakończeniu szkolenia przejdź do kroku szacowania.</span><span class="sxs-lookup"><span data-stu-id="c4c11-171">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="c4c11-172">Oceń model</span><span class="sxs-lookup"><span data-stu-id="c4c11-172">Evaluate the model</span></span>

<span data-ttu-id="c4c11-173">Wynikiem kroku szkolenia będzie jeden model, który miał najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="c4c11-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="c4c11-174">W kroku szacowania narzędzia model Builder sekcja Output będzie zawierać algorytm używany przez model najlepszego wykonywania w najlepszym wpisie *modelu* oraz metryki w *najlepszej jakości modelu (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="c4c11-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="c4c11-175">Ponadto tabela podsumowująca zawierająca pięć najważniejszych modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="c4c11-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="c4c11-176">Jeśli Twoje metryki dokładności nie są zadowalające, niektóre proste sposoby wypróbowania i poprawienia dokładności modelu mają na celu zwiększenie ilości czasu na nauczenie modelu lub użycie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="c4c11-177">W przeciwnym razie przejdź do kroku kodu.</span><span class="sxs-lookup"><span data-stu-id="c4c11-177">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="c4c11-178">Dodaj kod, aby tworzyć przewidywania</span><span class="sxs-lookup"><span data-stu-id="c4c11-178">Add the code to make predictions</span></span>

<span data-ttu-id="c4c11-179">W wyniku procesu szkolenia zostaną utworzone dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="c4c11-179">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="c4c11-180">TaxiFarePredictionML.ConsoleApp: Aplikacja konsolowa platformy .NET Core, która zawiera model szkoleń i przykładowego kodu zużycia.</span><span class="sxs-lookup"><span data-stu-id="c4c11-180">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="c4c11-181">TaxiFarePredictionML. model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych wejściowych i wyjściowych modelu, zapisana wersja modelu najlepszego przebiegu podczas uczenia i klasy pomocnika o nazwie `ConsumeModel` do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="c4c11-181">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="c4c11-182">W kroku Code narzędzia model Builder wybierz pozycję **Dodaj projekty** , aby dodać automatycznie generowane projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c4c11-182">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="c4c11-183">Otwórz plik *program.cs* w projekcie *TaxiFarePrediction* .</span><span class="sxs-lookup"><span data-stu-id="c4c11-183">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="c4c11-184">Dodaj następującą instrukcję using, aby odwołać się do projektu *TaxiFarePredictionML. model* :</span><span class="sxs-lookup"><span data-stu-id="c4c11-184">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="c4c11-185">Aby przeprowadzić prognozowanie nowych danych przy użyciu modelu, Utwórz nowe wystąpienie klasy `ModelInput` w ramach metody `Main` aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c4c11-185">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="c4c11-186">Zwróć uwagę, że opłata za opłaty nie jest częścią danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-186">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="c4c11-187">Dzieje się tak, ponieważ model generuje dla niego prognozę.</span><span class="sxs-lookup"><span data-stu-id="c4c11-187">This is because the model will generate the prediction for it.</span></span> 

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

1. <span data-ttu-id="c4c11-188">Użyj metody `Predict` z klasy `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="c4c11-188">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="c4c11-189">Metoda `Predict` ładuje przeszkolony model, tworzy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dla modelu i używa go do prognozowania nowych danych.</span><span class="sxs-lookup"><span data-stu-id="c4c11-189">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span> 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="c4c11-190">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="c4c11-190">Run the application.</span></span>

    <span data-ttu-id="c4c11-191">Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:</span><span class="sxs-lookup"><span data-stu-id="c4c11-191">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="c4c11-192">Jeśli musisz odwoływać się do wygenerowanych projektów w późniejszym czasie w innym rozwiązaniu, możesz je znaleźć w `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` katalogu.</span><span class="sxs-lookup"><span data-stu-id="c4c11-192">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c4c11-193">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c4c11-193">Next Steps</span></span>

<span data-ttu-id="c4c11-194">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c4c11-194">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="c4c11-195">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="c4c11-195">Prepare and understand the data</span></span>
> - <span data-ttu-id="c4c11-196">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="c4c11-196">Choose a scenario</span></span>
> - <span data-ttu-id="c4c11-197">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="c4c11-197">Load the data</span></span>
> - <span data-ttu-id="c4c11-198">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="c4c11-198">Train the model</span></span>
> - <span data-ttu-id="c4c11-199">Oceń model</span><span class="sxs-lookup"><span data-stu-id="c4c11-199">Evaluate the model</span></span>
> - <span data-ttu-id="c4c11-200">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="c4c11-200">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c4c11-201">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="c4c11-201">Additional Resources</span></span>

<span data-ttu-id="c4c11-202">Aby dowiedzieć się więcej na temat tematów wymienionych w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="c4c11-202">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="c4c11-203">Scenariusze konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="c4c11-203">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="c4c11-204">Regression</span><span class="sxs-lookup"><span data-stu-id="c4c11-204">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="c4c11-205">Metryki modelu regresji</span><span class="sxs-lookup"><span data-stu-id="c4c11-205">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="c4c11-206">Zestaw danych podróży NYC TLC</span><span class="sxs-lookup"><span data-stu-id="c4c11-206">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
