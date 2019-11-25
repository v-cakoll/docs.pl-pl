---
title: 'Samouczek: analizowanie klasyfikacji tonacji-Binary'
description: W tym samouczku przedstawiono sposób tworzenia aplikacji Razor Pages, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Tonacji klasyfikator binarny używa konstruktora modelu w programie Visual Studio.
ms.date: 10/08/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 5e5b60a53db70b33ed798bcf33497b74911ba727
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974798"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="0c378-104">Samouczek: analizowanie tonacji komentarzy witryny internetowej w aplikacji sieci Web przy użyciu konstruktora modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="0c378-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="0c378-105">Dowiedz się, jak analizować tonacji z komentarzy w czasie rzeczywistym w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0c378-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="0c378-106">W tym samouczku pokazano, jak utworzyć aplikację Razor Pages ASP.NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="0c378-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="0c378-107">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0c378-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="0c378-108">Tworzenie aplikacji Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0c378-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="0c378-109">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="0c378-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="0c378-110">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="0c378-110">Choose a scenario</span></span>
> - <span data-ttu-id="0c378-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="0c378-111">Load the data</span></span>
> - <span data-ttu-id="0c378-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="0c378-112">Train the model</span></span>
> - <span data-ttu-id="0c378-113">Oceń model</span><span class="sxs-lookup"><span data-stu-id="0c378-113">Evaluate the model</span></span>
> - <span data-ttu-id="0c378-114">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="0c378-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="0c378-115">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="0c378-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="0c378-116">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="0c378-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="0c378-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0c378-117">Pre-requisites</span></span>

<span data-ttu-id="0c378-118">Listę wymagań wstępnych i instrukcji instalacji można znaleźć w [podręczniku instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="0c378-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="0c378-119">Tworzenie aplikacji Razor Pages</span><span class="sxs-lookup"><span data-stu-id="0c378-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="0c378-120">Utwórz **aplikację Razor Pages ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="0c378-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="0c378-121">Otwórz program Visual Studio i wybierz pozycję **plik > nowy > projekt** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="0c378-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="0c378-122">W oknie dialogowym Nowy projekt wybierz węzeł **wizualizacji C#**  , a następnie węzeł **sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="0c378-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="0c378-123">Następnie wybierz szablon projektu **aplikacji sieci Web ASP.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="0c378-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="0c378-124">W polu tekstowym **Nazwa** wpisz "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="0c378-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="0c378-125">Pole wyboru **Utwórz katalog dla rozwiązania** powinno być domyślnie zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="0c378-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="0c378-126">Jeśli tak nie jest, należy go sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="0c378-126">If that's not the case, check it.</span></span>
    1. <span data-ttu-id="0c378-127">Wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="0c378-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="0c378-128">W oknie Wybierz **aplikację sieci Web** , która wyświetla różne typy projektów ASP.NET Core, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="0c378-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0c378-129">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="0c378-129">Prepare and understand the data</span></span>

<span data-ttu-id="0c378-130">Pobierz [zestaw danych detox Wikipedia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="0c378-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="0c378-131">Gdy zostanie otwarta strona sieci Web, kliknij prawym przyciskiem myszy na stronie, wybierz polecenie **Zapisz jako** i Zapisz plik w dowolnym miejscu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0c378-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="0c378-132">Każdy wiersz w zestawie danych *Wikipedia-detox-250-line-Data. tsv* reprezentuje inny przegląd, który został pozostawiony przez użytkownika w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="0c378-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="0c378-133">Pierwsza kolumna reprezentuje tonacji tekstu (0 to nietoksyczne, 1 jest toksyczny), a druga kolumna reprezentuje komentarz, który został pozostawiony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0c378-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="0c378-134">Kolumny są oddzielane znakami tabulacji.</span><span class="sxs-lookup"><span data-stu-id="0c378-134">The columns are separated by tabs.</span></span> <span data-ttu-id="0c378-135">Dane wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="0c378-135">The data looks like the following:</span></span>

| <span data-ttu-id="0c378-136">Tonacji</span><span class="sxs-lookup"><span data-stu-id="0c378-136">Sentiment</span></span> | <span data-ttu-id="0c378-137">SentimentText</span><span class="sxs-lookup"><span data-stu-id="0c378-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="0c378-138">1</span><span class="sxs-lookup"><span data-stu-id="0c378-138">1</span></span> | <span data-ttu-id="0c378-139">= = Prosta = = informatyku, prosta to Carl Picture lub else.</span><span class="sxs-lookup"><span data-stu-id="0c378-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="0c378-140">1</span><span class="sxs-lookup"><span data-stu-id="0c378-140">1</span></span> | <span data-ttu-id="0c378-141">= = OK!</span><span class="sxs-lookup"><span data-stu-id="0c378-141">== OK!</span></span> <span data-ttu-id="0c378-142">= = BŁYSKAWICZNE PRZECHODZENIE DO VANDALIZE DZIKICH WITRYN TYPU WIKI, A NASTĘPNIE!!!</span><span class="sxs-lookup"><span data-stu-id="0c378-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="0c378-143">0</span><span class="sxs-lookup"><span data-stu-id="0c378-143">0</span></span> | <span data-ttu-id="0c378-144">Mam nadzieję, że to pomoże.</span><span class="sxs-lookup"><span data-stu-id="0c378-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="0c378-145">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="0c378-145">Choose a scenario</span></span>

![Kreator konstruktora modelu w programie Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="0c378-147">Aby szkolić model, musisz wybrać z listy dostępnych scenariuszy uczenia maszynowego udostępnianych przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="0c378-147">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="0c378-148">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *SentimentRazor* i wybierz polecenie **Dodaj** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="0c378-148">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="0c378-149">Na potrzeby tego przykładu scenariusz jest tonacji analizy.</span><span class="sxs-lookup"><span data-stu-id="0c378-149">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="0c378-150">W kroku *scenariusz* narzędzia model Builder wybierz scenariusz **Analiza tonacji** .</span><span class="sxs-lookup"><span data-stu-id="0c378-150">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="0c378-151">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="0c378-151">Load the data</span></span>

<span data-ttu-id="0c378-152">Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych SQL Server lub lokalnego pliku w formacie `csv` lub `tsv`.</span><span class="sxs-lookup"><span data-stu-id="0c378-152">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="0c378-153">W kroku dane narzędzia model Builder wybierz pozycję **plik** z listy rozwijanej Źródło danych.</span><span class="sxs-lookup"><span data-stu-id="0c378-153">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="0c378-154">Wybierz przycisk obok pola tekstowego **Wybierz plik** i Użyj Eksploratora plików, aby przeglądać i wybrać plik *Wikipedia-detox-250-line-Data. tsv* .</span><span class="sxs-lookup"><span data-stu-id="0c378-154">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="0c378-155">Wybierz pozycję **tonacji** w **kolumnie do przewidywania (etykieta)** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="0c378-155">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="0c378-156">Pozostaw wartości domyślne dla listy rozwijanej **kolumny wejściowe (Features)** .</span><span class="sxs-lookup"><span data-stu-id="0c378-156">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="0c378-157">Wybierz łącze **uczenie** , aby przejść do następnego kroku w narzędziu model Builder.</span><span class="sxs-lookup"><span data-stu-id="0c378-157">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="0c378-158">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="0c378-158">Train the model</span></span>

<span data-ttu-id="0c378-159">Zadanie uczenia maszynowego używane do uczenia modelu analizy tonacji w tym samouczku jest klasyfikacją binarną.</span><span class="sxs-lookup"><span data-stu-id="0c378-159">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="0c378-160">Podczas procesu uczenia modelowego, Konstruktor modelu pociąga za siebie różne modele przy użyciu różnych binarnych algorytmów klasyfikacji i ustawień, aby znaleźć najlepszy model dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="0c378-160">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="0c378-161">Czas wymagany przez model do uczenia jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="0c378-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="0c378-162">Konstruktor modelu automatycznie wybiera wartość domyślną dla **czasu do uczenia (w sekundach)** na podstawie rozmiaru źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0c378-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="0c378-163">Chociaż Konstruktor modelu ustawia wartość **czasu do uczenia (sekundy)** do 10 sekund, zwiększ go do 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="0c378-163">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="0c378-164">Szkolenie przez dłuższy czas umożliwia konstruktorowi modelu Eksplorowanie większej liczby algorytmów i kombinacji parametrów podczas wyszukiwania najlepszego modelu.</span><span class="sxs-lookup"><span data-stu-id="0c378-164">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="0c378-165">Wybierz pozycję **Rozpocznij szkolenie**.</span><span class="sxs-lookup"><span data-stu-id="0c378-165">Select **Start Training**.</span></span>

    <span data-ttu-id="0c378-166">W trakcie całego procesu szkolenia dane o postępie są wyświetlane w sekcji `Progress` kroku uczenie.</span><span class="sxs-lookup"><span data-stu-id="0c378-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="0c378-167">Stan przedstawia stan zakończenia procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="0c378-167">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="0c378-168">Najlepsza dokładność przedstawia dokładność najlepszego modelu, który został znaleziony przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="0c378-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="0c378-169">Większa dokładność oznacza, że model przewidywalno dokładniej na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="0c378-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="0c378-170">Najlepszym algorytmem jest wyświetlana nazwa najlepszego wykonywania algorytmu, który został wykonany przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="0c378-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="0c378-171">Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="0c378-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="0c378-172">Po zakończeniu szkolenia wybierz łącze **Oceń** , aby przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="0c378-172">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="0c378-173">Oceń model</span><span class="sxs-lookup"><span data-stu-id="0c378-173">Evaluate the model</span></span>

<span data-ttu-id="0c378-174">Wynikiem kroku szkolenia będzie jeden model, który miał najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="0c378-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="0c378-175">W kroku szacowania narzędzia model Builder sekcja Output zawiera algorytm używany przez model najlepiej działający w najlepszym wpisie **modelu** oraz metryki o **najwyższej dokładności modelu**.</span><span class="sxs-lookup"><span data-stu-id="0c378-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="0c378-176">Ponadto tabela podsumowująca zawierająca pięć najważniejszych modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="0c378-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="0c378-177">Jeśli Twoje metryki dokładności nie są zadowalające, niektóre proste sposoby wypróbowania i poprawienia dokładności modelu mają na celu zwiększenie ilości czasu na nauczenie modelu lub użycie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="0c378-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="0c378-178">W przeciwnym razie wybierz łącze **kod** , aby przejść do ostatniego kroku w narzędziu model Builder.</span><span class="sxs-lookup"><span data-stu-id="0c378-178">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="0c378-179">Dodaj kod, aby tworzyć przewidywania</span><span class="sxs-lookup"><span data-stu-id="0c378-179">Add the code to make predictions</span></span>

<span data-ttu-id="0c378-180">W wyniku procesu szkolenia zostaną utworzone dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="0c378-180">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="0c378-181">Odwołuje się do przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="0c378-181">Reference the trained model</span></span>

1. <span data-ttu-id="0c378-182">W kroku *Code* narzędzia model Builder wybierz pozycję **Dodaj projekty** , aby dodać automatycznie generowane projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0c378-182">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="0c378-183">Następujące projekty powinny pojawić się w **Eksplorator rozwiązań**:</span><span class="sxs-lookup"><span data-stu-id="0c378-183">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="0c378-184">*SentimentRazorML. ConsoleApp*: Aplikacja konsolowa platformy .NET Core, która zawiera model szkoleń i kodu przewidywania.</span><span class="sxs-lookup"><span data-stu-id="0c378-184">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="0c378-185">*SentimentRazorML. model*: biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych wejściowych i wyjściowych, a także zapisaną wersję najlepszego modelu podczas uczenia się.</span><span class="sxs-lookup"><span data-stu-id="0c378-185">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="0c378-186">W tym samouczku używany jest tylko projekt *SentimentRazorML. model* , ponieważ przewidywania zostaną wykonane w aplikacji sieci Web *SentimentRazor* , a nie w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="0c378-186">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="0c378-187">Chociaż *SentimentRazorML. ConsoleApp* nie będzie używany do oceniania, może służyć do ponownego uczenia modelu przy użyciu nowych danych w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="0c378-187">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="0c378-188">W tym samouczku przeszkolenie zostało przeprowadzone poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="0c378-188">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="0c378-189">Konfigurowanie puli PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="0c378-189">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="0c378-190">Aby wykonać pojedyncze prognozowanie, należy utworzyć [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="0c378-190">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="0c378-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczna wątkowo.</span><span class="sxs-lookup"><span data-stu-id="0c378-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="0c378-192">Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c378-192">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="0c378-193">Gdy aplikacja zostanie powiększona, ten proces może być niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="0c378-193">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="0c378-194">Aby zwiększyć wydajność i bezpieczeństwo wątków, należy użyć kombinacji iniekcji zależności i usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c378-194">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="0c378-195">Zainstaluj pakiet NuGet *Microsoft.Extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="0c378-195">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="0c378-196">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0c378-196">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="0c378-197">Wybierz pozycję "nuget.org" jako źródło pakietu.</span><span class="sxs-lookup"><span data-stu-id="0c378-197">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="0c378-198">Wybierz kartę **Przeglądaj** i wyszukaj ciąg **Microsoft.Extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="0c378-198">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="0c378-199">Wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="0c378-199">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="0c378-200">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian**</span><span class="sxs-lookup"><span data-stu-id="0c378-200">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="0c378-201">Jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów, **Wybierz przycisk Akceptuję w oknie** dialogowym **akceptacji licencji** .</span><span class="sxs-lookup"><span data-stu-id="0c378-201">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="0c378-202">Otwórz plik *Startup.cs* w projekcie *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="0c378-202">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="0c378-203">Dodaj następujące instrukcje using, aby odwołać się do pakietu NuGet *Microsoft.Extensions.ml* i projektu *SentimentRazorML. model* :</span><span class="sxs-lookup"><span data-stu-id="0c378-203">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="0c378-204">Utwórz zmienną globalną do przechowywania lokalizacji pliku z przeszkolonym modelem.</span><span class="sxs-lookup"><span data-stu-id="0c378-204">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="0c378-205">Plik modelu jest przechowywany w katalogu kompilacji obok plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c378-205">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="0c378-206">Aby ułatwić dostęp, należy utworzyć metodę pomocnika o nazwie `GetAbsolutePath` po metodzie `Configure`</span><span class="sxs-lookup"><span data-stu-id="0c378-206">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="0c378-207">Użyj metody `GetAbsolutePath` w konstruktorze klasy `Startup`, aby ustawić `_modelPath`.</span><span class="sxs-lookup"><span data-stu-id="0c378-207">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="0c378-208">Skonfiguruj `PredictionEnginePool` aplikacji w metodzie `ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="0c378-208">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="0c378-209">Utwórz procedurę obsługi analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="0c378-209">Create sentiment analysis handler</span></span>

<span data-ttu-id="0c378-210">Przewidywania zostaną wykonane wewnątrz strony głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c378-210">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="0c378-211">W związku z tym metoda, która pobiera dane wejściowe użytkownika i używa `PredictionEnginePool`, aby zwrócić prognozę, należy dodać.</span><span class="sxs-lookup"><span data-stu-id="0c378-211">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="0c378-212">Otwórz plik *index.cshtml.cs* znajdujący się w katalogu *Pages* i Dodaj następujące instrukcje using:</span><span class="sxs-lookup"><span data-stu-id="0c378-212">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="0c378-213">Aby można było używać `PredictionEnginePool` skonfigurowanych w klasie `Startup`, należy wstrzyknąć ją do konstruktora modelu, w którym ma być używany.</span><span class="sxs-lookup"><span data-stu-id="0c378-213">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="0c378-214">Dodaj zmienną, aby odwoływać się do `PredictionEnginePool` wewnątrz klasy `IndexModel`.</span><span class="sxs-lookup"><span data-stu-id="0c378-214">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="0c378-215">Utwórz konstruktora w klasie `IndexModel` i wstrzyknąć do niego usługę `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="0c378-215">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="0c378-216">Utwórz procedurę obsługi metody, która używa `PredictionEnginePool` do tworzenia prognoz z danych wejściowych użytkownika otrzymanych ze strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0c378-216">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="0c378-217">Poniżej metody `OnGet` Utwórz nową metodę o nazwie `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="0c378-217">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="0c378-218">Wewnątrz metody `OnGetAnalyzeSentiment` Zwróć *neutralną* tonacji, jeśli dane wejściowe użytkownika są puste lub mają wartość null.</span><span class="sxs-lookup"><span data-stu-id="0c378-218">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="0c378-219">Uwzględniając prawidłowe dane wejściowe, Utwórz nowe wystąpienie `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="0c378-219">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="0c378-220">Użyj `PredictionEnginePool` do przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="0c378-220">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="0c378-221">Przekonwertuj przewidywaną wartość `bool` na toksyczne lub nietoksyczne przy użyciu poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="0c378-221">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="0c378-222">Na koniec Zwróć tonacji z powrotem do strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0c378-222">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="0c378-223">Skonfiguruj stronę sieci Web</span><span class="sxs-lookup"><span data-stu-id="0c378-223">Configure the web page</span></span>

<span data-ttu-id="0c378-224">Wyniki zwrócone przez `OnGetAnalyzeSentiment` będą dynamicznie wyświetlane na stronie sieci Web `Index`.</span><span class="sxs-lookup"><span data-stu-id="0c378-224">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="0c378-225">Otwórz plik *index. cshtml* w katalogu *stron* i Zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="0c378-225">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="0c378-226">Następnie Dodaj kod stylów CSS do końca strony *site. css* w katalogu *wwwroot\css* :</span><span class="sxs-lookup"><span data-stu-id="0c378-226">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="0c378-227">Następnie Dodaj kod, aby wysłać dane wejściowe ze strony sieci Web do procedury obsługi `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="0c378-227">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="0c378-228">W pliku *site. js* znajdującym się w katalogu *wwwroot\js* utwórz funkcję o nazwie `getSentiment`, aby wykonać żądanie Get http przy użyciu danych wejściowych użytkownika do procedury obsługi `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="0c378-228">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="0c378-229">Poniżej można dodać kolejną funkcję o nazwie `updateMarker`, aby dynamicznie aktualizować pozycję znacznika na stronie sieci Web w miarę przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="0c378-229">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="0c378-230">Utwórz funkcję programu obsługi zdarzeń o nazwie `updateSentiment`, aby pobrać dane wejściowe od użytkownika, wyślij je do funkcji `OnGetAnalyzeSentiment` przy użyciu funkcji `getSentiment` i zaktualizuj znacznik za pomocą funkcji `updateMarker`.</span><span class="sxs-lookup"><span data-stu-id="0c378-230">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="0c378-231">Na koniec Zarejestruj program obsługi zdarzeń i powiąż go z elementem `textarea` z atrybutem `id=Message`.</span><span class="sxs-lookup"><span data-stu-id="0c378-231">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="0c378-232">Uruchom aplikację</span><span class="sxs-lookup"><span data-stu-id="0c378-232">Run the application</span></span>

<span data-ttu-id="0c378-233">Teraz, gdy aplikacja jest skonfigurowana, uruchom aplikację, która powinna być uruchamiana w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="0c378-233">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="0c378-234">Po uruchomieniu aplikacji, wprowadź *wartość Konstruktor modeli jest chłodna!*</span><span class="sxs-lookup"><span data-stu-id="0c378-234">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="0c378-235">w obszarze tekstu.</span><span class="sxs-lookup"><span data-stu-id="0c378-235">into the text area.</span></span> <span data-ttu-id="0c378-236">Wyświetlona tonacji nie powinna być *toksyczna*.</span><span class="sxs-lookup"><span data-stu-id="0c378-236">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Uruchamianie okna z przewidywanym oknem tonacji](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="0c378-238">Jeśli musisz odwołać się do projektów wygenerowanych przez konstruktora modeli w późniejszym czasie w innym rozwiązaniu, możesz je znaleźć w katalogu `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="0c378-238">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0c378-239">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0c378-239">Next steps</span></span>

<span data-ttu-id="0c378-240">W tym samouczku przedstawiono sposób wykonywania tych instrukcji:</span><span class="sxs-lookup"><span data-stu-id="0c378-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0c378-241">Tworzenie aplikacji Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0c378-241">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="0c378-242">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="0c378-242">Prepare and understand the data</span></span>
> - <span data-ttu-id="0c378-243">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="0c378-243">Choose a scenario</span></span>
> - <span data-ttu-id="0c378-244">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="0c378-244">Load the data</span></span>
> - <span data-ttu-id="0c378-245">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="0c378-245">Train the model</span></span>
> - <span data-ttu-id="0c378-246">Oceń model</span><span class="sxs-lookup"><span data-stu-id="0c378-246">Evaluate the model</span></span>
> - <span data-ttu-id="0c378-247">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="0c378-247">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0c378-248">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="0c378-248">Additional Resources</span></span>

<span data-ttu-id="0c378-249">Aby dowiedzieć się więcej na temat tematów wymienionych w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="0c378-249">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="0c378-250">Scenariusze konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="0c378-250">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="0c378-251">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="0c378-251">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="0c378-252">Metryki binarnego modelu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="0c378-252">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
