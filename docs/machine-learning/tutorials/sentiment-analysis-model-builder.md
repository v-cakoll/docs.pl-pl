---
title: 'Samouczek: Analizuj klasyfikację tonacji-Binary'
description: W tym samouczku przedstawiono sposób tworzenia aplikacji Razor Pages, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Tonacji klasyfikator binarny używa konstruktora modelu w programie Visual Studio.
ms.date: 09/13/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 375440d98fd728cc89c1ac620614067edbd3adf8
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216882"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="ee3b4-104">Samouczek: Analizowanie tonacji komentarzy witryny internetowej w aplikacji sieci Web przy użyciu konstruktora modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="ee3b4-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="ee3b4-105">Dowiedz się, jak analizować tonacji z komentarzy w czasie rzeczywistym w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="ee3b4-106">W tym samouczku pokazano, jak utworzyć aplikację Razor Pages ASP.NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="ee3b4-107">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ee3b4-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ee3b4-108">Tworzenie aplikacji Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ee3b4-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="ee3b4-109">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="ee3b4-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="ee3b4-110">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="ee3b4-110">Choose a scenario</span></span>
> - <span data-ttu-id="ee3b4-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="ee3b4-111">Load the data</span></span>
> - <span data-ttu-id="ee3b4-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ee3b4-112">Train the model</span></span>
> - <span data-ttu-id="ee3b4-113">Oceń model</span><span class="sxs-lookup"><span data-stu-id="ee3b4-113">Evaluate the model</span></span>
> - <span data-ttu-id="ee3b4-114">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="ee3b4-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="ee3b4-115">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="ee3b4-116">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ee3b4-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ee3b4-117">Pre-requisites</span></span>

<span data-ttu-id="ee3b4-118">Listę wymagań wstępnych i instrukcji instalacji można znaleźć w [podręczniku instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="ee3b4-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="ee3b4-119">Tworzenie aplikacji Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ee3b4-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="ee3b4-120">Utwórz **aplikację Razor Pages ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="ee3b4-121">Otwórz program Visual Studio i wybierz pozycję **plik > nowy > projekt** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="ee3b4-122">W oknie dialogowym Nowy projekt wybierz węzeł **wizualizacji C#**  , a następnie węzeł **sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="ee3b4-123">Następnie wybierz szablon projektu **aplikacji sieci Web ASP.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="ee3b4-124">W polu tekstowym **Nazwa** wpisz "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="ee3b4-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="ee3b4-125">Pole wyboru **Utwórz katalog dla rozwiązania** powinno być domyślnie zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="ee3b4-126">Jeśli tak nie jest, należy go sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-126">If that's not the case, check it.</span></span>
    1. <span data-ttu-id="ee3b4-127">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="ee3b4-128">W oknie Wybierz **aplikację sieci Web** , która wyświetla różne typy projektów ASP.NET Core, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="ee3b4-129">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="ee3b4-129">Prepare and understand the data</span></span>

<span data-ttu-id="ee3b4-130">Pobierz [zestaw danych detox Wikipedia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="ee3b4-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="ee3b4-131">Gdy zostanie otwarta strona sieci Web, kliknij prawym przyciskiem myszy na stronie, wybierz polecenie **Zapisz jako** i Zapisz plik w dowolnym miejscu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="ee3b4-132">Każdy wiersz w zestawie danych *Wikipedia-detox-250-line-Data. tsv* reprezentuje inny przegląd, który został pozostawiony przez użytkownika w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="ee3b4-133">Pierwsza kolumna reprezentuje tonacji tekstu (0 to nietoksyczne, 1 jest toksyczny), a druga kolumna reprezentuje komentarz, który został pozostawiony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="ee3b4-134">Kolumny są oddzielane znakami tabulacji.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-134">The columns are separated by tabs.</span></span> <span data-ttu-id="ee3b4-135">Dane wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="ee3b4-135">The data looks like the following:</span></span>

| <span data-ttu-id="ee3b4-136">Tonacji</span><span class="sxs-lookup"><span data-stu-id="ee3b4-136">Sentiment</span></span> | <span data-ttu-id="ee3b4-137">SentimentText</span><span class="sxs-lookup"><span data-stu-id="ee3b4-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="ee3b4-138">1</span><span class="sxs-lookup"><span data-stu-id="ee3b4-138">1</span></span> | <span data-ttu-id="ee3b4-139">= = Prosta = = informatyku, prosta to Carl Picture lub else.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="ee3b4-140">1</span><span class="sxs-lookup"><span data-stu-id="ee3b4-140">1</span></span> | <span data-ttu-id="ee3b4-141">= = OK!</span><span class="sxs-lookup"><span data-stu-id="ee3b4-141">== OK!</span></span> <span data-ttu-id="ee3b4-142">= = BŁYSKAWICZNE PRZECHODZENIE DO VANDALIZE DZIKICH WITRYN TYPU WIKI, A NASTĘPNIE!!!</span><span class="sxs-lookup"><span data-stu-id="ee3b4-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="ee3b4-143">0</span><span class="sxs-lookup"><span data-stu-id="ee3b4-143">0</span></span> | <span data-ttu-id="ee3b4-144">Mam nadzieję, że to pomoże.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="ee3b4-145">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="ee3b4-145">Choose a scenario</span></span>

![](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="ee3b4-146">Aby szkolić model, musisz wybrać z listy dostępnych scenariuszy uczenia maszynowego udostępnianych przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="ee3b4-147">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *SentimentRazor* , a następnie wybierz pozycję **Dodaj** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="ee3b4-148">Na potrzeby tego przykładu scenariusz jest tonacji analizy.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="ee3b4-149">W kroku *scenariusz* narzędzia model Builder wybierz scenariusz **Analiza tonacji** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="ee3b4-150">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="ee3b4-150">Load the data</span></span>

<span data-ttu-id="ee3b4-151">Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych SQL Server lub lokalnego pliku w `csv` formacie lub. `tsv`</span><span class="sxs-lookup"><span data-stu-id="ee3b4-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="ee3b4-152">W kroku dane narzędzia model Builder wybierz pozycję **plik** z listy rozwijanej Źródło danych.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="ee3b4-153">Wybierz przycisk obok pola tekstowego **Wybierz plik** i Użyj Eksploratora plików, aby przeglądać i wybrać plik *Wikipedia-detox-250-line-Data. tsv* .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="ee3b4-154">Wybierz **tonacji** w **etykiecie lub kolumnie do** listy rozwijanej przewidywania</span><span class="sxs-lookup"><span data-stu-id="ee3b4-154">Choose **Sentiment** in the **Label or Column to Predict** dropdown</span></span>
1. <span data-ttu-id="ee3b4-155">Wybierz łącze **uczenie** , aby przejść do następnego kroku w narzędziu model Builder.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-155">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="ee3b4-156">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ee3b4-156">Train the model</span></span>

<span data-ttu-id="ee3b4-157">Zadanie uczenia maszynowego używane do uczenia modelu prognozowania cen w tym samouczku jest klasyfikacją binarną.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-157">The machine learning task used to train the price prediction model in this tutorial is binary classification.</span></span> <span data-ttu-id="ee3b4-158">Podczas procesu uczenia modelowego, Konstruktor modelu pociąga za siebie różne modele przy użyciu różnych binarnych algorytmów klasyfikacji i ustawień, aby znaleźć najlepszy model dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-158">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="ee3b4-159">Czas wymagany przez model do uczenia jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-159">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="ee3b4-160">Konstruktor modelu automatycznie wybiera wartość domyślną dla **czasu do uczenia (w sekundach)** na podstawie rozmiaru źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-160">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="ee3b4-161">Chociaż Konstruktor modelu ustawia wartość **czasu do uczenia (sekundy)** do 10 sekund, zwiększ go do 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-161">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="ee3b4-162">Szkolenie przez dłuższy czas umożliwia konstruktorowi modelu Eksplorowanie większej liczby algorytmów i kombinacji parametrów podczas wyszukiwania najlepszego modelu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-162">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="ee3b4-163">Wybierz pozycję **Rozpocznij szkolenie**.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-163">Select **Start Training**.</span></span>

    <span data-ttu-id="ee3b4-164">W trakcie całego procesu szkolenia dane o postępie są wyświetlane `Progress` w sekcji kroku uczenie.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-164">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="ee3b4-165">Stan przedstawia stan zakończenia procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-165">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="ee3b4-166">Najlepsza dokładność przedstawia dokładność najlepszego modelu, który został znaleziony przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-166">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="ee3b4-167">Większa dokładność oznacza, że model przewidywalno dokładniej na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-167">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="ee3b4-168">Najlepszym algorytmem jest wyświetlana nazwa najlepszego wykonywania algorytmu, który został wykonany przez konstruktora modelu do tej pory.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-168">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="ee3b4-169">Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-169">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="ee3b4-170">Po zakończeniu szkolenia wybierz łącze **Oceń** , aby przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-170">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="ee3b4-171">Oceń model</span><span class="sxs-lookup"><span data-stu-id="ee3b4-171">Evaluate the model</span></span>

<span data-ttu-id="ee3b4-172">Wynikiem kroku szkolenia będzie jeden model, który miał najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-172">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="ee3b4-173">W kroku szacowania narzędzia model Builder sekcja Output będzie zawierać algorytm używany przez model najlepszego wykonywania w najlepszym wpisie **modelu** oraz metryki w **najlepszej jakości modelu (RSquared)** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-173">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Quality (RSquared)**.</span></span> <span data-ttu-id="ee3b4-174">Ponadto tabela podsumowująca zawierająca pięć najważniejszych modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-174">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="ee3b4-175">Jeśli Twoje metryki dokładności nie są zadowalające, niektóre proste sposoby wypróbowania i poprawienia dokładności modelu mają na celu zwiększenie ilości czasu na nauczenie modelu lub użycie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-175">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="ee3b4-176">W przeciwnym razie wybierz łącze **kod** , aby przejść do ostatniego kroku w narzędziu model Builder.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-176">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="ee3b4-177">Dodaj kod, aby tworzyć przewidywania</span><span class="sxs-lookup"><span data-stu-id="ee3b4-177">Add the code to make predictions</span></span>

<span data-ttu-id="ee3b4-178">W wyniku procesu szkolenia zostaną utworzone dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-178">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="ee3b4-179">Odwołuje się do przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="ee3b4-179">Reference the trained model</span></span>

1. <span data-ttu-id="ee3b4-180">W kroku *Code* narzędzia model Builder wybierz pozycję **Dodaj projekty** , aby dodać automatycznie generowane projekty do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-180">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="ee3b4-181">Następujące projekty powinny pojawić się w **Eksplorator rozwiązań**:</span><span class="sxs-lookup"><span data-stu-id="ee3b4-181">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="ee3b4-182">*SentimentRazorML. ConsoleApp*: Aplikacja konsolowa platformy .NET Core, która zawiera model szkoleń i kodu przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-182">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="ee3b4-183">*SentimentRazorML. model*: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych wejściowych i wyjściowych, a także utrwalaną wersję najlepszego modelu podczas uczenia.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-183">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

    <span data-ttu-id="ee3b4-184">W tym samouczku używany jest tylko projekt *SentimentRazorML. model* , ponieważ przewidywania zostaną wykonane w aplikacji sieci Web *SentimentRazor* , a nie w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-184">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="ee3b4-185">Chociaż *SentimentRazorML. ConsoleApp* nie będzie używany do oceniania, może służyć do ponownego uczenia modelu przy użyciu nowych danych w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-185">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="ee3b4-186">W tym samouczku przeszkolenie zostało przeprowadzone poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-186">Retraining is outside the scope of this tutorial though.</span></span>

1. <span data-ttu-id="ee3b4-187">Aby użyć nauczonego modelu w aplikacji Razor Pages, Dodaj odwołanie do projektu *SentimentRazorML. model* .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-187">To use the trained model inside your Razor Pages application, add a reference to the *SentimentRazorML.Model* project.</span></span>

    1. <span data-ttu-id="ee3b4-188">Kliknij prawym przyciskiem myszy projekt **SentimentRazor** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-188">Right-click **SentimentRazor** project.</span></span>
    1. <span data-ttu-id="ee3b4-189">Wybierz pozycję **Dodaj odwołanie >** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-189">Select **Add > Reference**.</span></span>
    1. <span data-ttu-id="ee3b4-190">Wybierz węzeł **projekty > rozwiązanie** i z listy Sprawdź projekt **SentimentRazorML. model** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-190">Choose the **Projects > Solution** node and from the list, check the **SentimentRazorML.Model** project.</span></span>
    1. <span data-ttu-id="ee3b4-191">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-191">Select **OK**.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="ee3b4-192">Konfigurowanie puli PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="ee3b4-192">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="ee3b4-193">Aby wykonać pojedyncze prognozowanie, użyj [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="ee3b4-193">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="ee3b4-194">Aby można było korzystać [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) z aplikacji, należy ją utworzyć w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-194">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application, you must create it when it's needed.</span></span> <span data-ttu-id="ee3b4-195">W takim przypadku najlepszym rozwiązaniem jest wstrzyknięcie zależności.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-195">In that case, a best practice to consider is dependency injection.</span></span>

> [!WARNING]
> <span data-ttu-id="ee3b4-196">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-196">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ee3b4-197">Aby zwiększyć wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługi, która [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) tworzy `PredictionEngine` obiekty do użycia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-197">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="ee3b4-198">Przeczytaj następujący wpis w blogu, aby dowiedzieć się więcej na temat [tworzenia i używania `PredictionEngine` pul obiektów w ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="ee3b4-198">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

1. <span data-ttu-id="ee3b4-199">Zainstaluj pakiet NuGet *Microsoft.Extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="ee3b4-199">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="ee3b4-200">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-200">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="ee3b4-201">Wybierz pozycję "nuget.org" jako źródło pakietu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-201">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="ee3b4-202">Wybierz kartę **Przeglądaj** i wyszukaj ciąg **Microsoft.Extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-202">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="ee3b4-203">Wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-203">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="ee3b4-204">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian**</span><span class="sxs-lookup"><span data-stu-id="ee3b4-204">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="ee3b4-205">Jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów, **Wybierz przycisk Akceptuję w oknie** dialogowym **akceptacji licencji** .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-205">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ee3b4-206">Otwórz plik *Startup.cs* w projekcie *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="ee3b4-206">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="ee3b4-207">Dodaj następujące instrukcje using, aby odwołać się do pakietu NuGet *Microsoft.Extensions.ml* i projektu *SentimentRazorML. model* :</span><span class="sxs-lookup"><span data-stu-id="ee3b4-207">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L12-L14)]

1. <span data-ttu-id="ee3b4-208">Utwórz zmienną globalną do przechowywania lokalizacji pliku z przeszkolonym modelem.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-208">Create a global variable to store the location of the trained model file.</span></span>

    [!code-csharp [ModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L20)]

1. <span data-ttu-id="ee3b4-209">Plik modelu jest przechowywany w katalogu kompilacji obok plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-209">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="ee3b4-210">Aby ułatwić dostęp, należy utworzyć metodę pomocnika wywołana `GetAbsolutePath` `Configure` po metodzie</span><span class="sxs-lookup"><span data-stu-id="ee3b4-210">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    [!code-csharp [GetAbsolutePathMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L66-L73)]

1. <span data-ttu-id="ee3b4-211">Użyj metody z konstruktora`_modelPath`klasy, aby ustawić. `Startup` `GetAbsolutePath`</span><span class="sxs-lookup"><span data-stu-id="ee3b4-211">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    [!code-csharp [InitModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L25)]

1. <span data-ttu-id="ee3b4-212">Skonfiguruj aplikację `ConfigureServices` dla aplikacji w metodzie: `PredictionEnginePool`</span><span class="sxs-lookup"><span data-stu-id="ee3b4-212">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    [!code-csharp [InitPredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L42)]

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="ee3b4-213">Utwórz procedurę obsługi analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="ee3b4-213">Create sentiment analysis handler</span></span>

<span data-ttu-id="ee3b4-214">Przewidywania zostaną wykonane wewnątrz strony głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-214">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="ee3b4-215">W związku z tym metoda, która pobiera dane wejściowe użytkownika i `PredictionEnginePool` używa do zwrócenia prognozy, musi zostać dodana.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-215">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="ee3b4-216">Otwórz plik *index.cshtml.cs* znajdujący się w katalogu *Pages* i Dodaj następujące instrukcje using:</span><span class="sxs-lookup"><span data-stu-id="ee3b4-216">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    [!code-csharp [IndexUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L7-L8)]

    <span data-ttu-id="ee3b4-217">Aby można było użyć `PredictionEnginePool` skonfigurowanej `Startup` klasy w klasie, należy wstrzyknąć ją do konstruktora modelu, w którym ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-217">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="ee3b4-218">Dodaj zmienną, aby odwołać `PredictionEnginePool` się do `IndexModel` wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-218">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    [!code-csharp [PredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L14)]

1. <span data-ttu-id="ee3b4-219">Utwórz konstruktora w `IndexModel` klasie i `PredictionEnginePool` wstrzyknąć do niego usługę.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-219">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    [!code-csharp [IndexConstructor](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L16-L19)]

1. <span data-ttu-id="ee3b4-220">Utwórz procedurę obsługi metody, która używa `PredictionEnginePool` do tworzenia prognoz z danych wejściowych użytkownika otrzymanych ze strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-220">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="ee3b4-221">`OnGet` Poniżej metody Utwórz nową metodę o nazwie`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="ee3b4-221">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="ee3b4-222">Wewnątrz metody Zwróć neutralną tonacji, jeśli dane wejściowe użytkownika są puste lub mają wartość null. `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="ee3b4-222">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L28)]

    1. <span data-ttu-id="ee3b4-223">Podaje prawidłowe dane wejściowe, Utwórz nowe wystąpienie `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-223">Given a valid input, create a new instance of `ModelInput`.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L29)]

    1. <span data-ttu-id="ee3b4-224">`PredictionEnginePool` Użyj do przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-224">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        [!code-csharp [MakePrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L30)]

    1. <span data-ttu-id="ee3b4-225">Przekonwertuj przewidywaną `bool` wartość na toksyczną lub nietoksyczną przy użyciu poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-225">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        [!code-csharp [ConvertPrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L31)]

    1. <span data-ttu-id="ee3b4-226">Na koniec Zwróć tonacji z powrotem do strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-226">Finally, return the sentiment back to the web page.</span></span>

        [!code-csharp [ReturnSentiment](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L32)]

### <a name="configure-the-web-page"></a><span data-ttu-id="ee3b4-227">Skonfiguruj stronę sieci Web</span><span class="sxs-lookup"><span data-stu-id="ee3b4-227">Configure the web page</span></span>

<span data-ttu-id="ee3b4-228">Wyniki zwrócone przez `OnGetAnalyzeSentiment` program będą dynamicznie wyświetlane `Index` na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-228">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="ee3b4-229">Otwórz plik *index. cshtml* w katalogu *stron* i Zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ee3b4-229">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="ee3b4-230">Następnie Dodaj kod stylów CSS do końca strony *site. css* w katalogu *wwwroot\css* :</span><span class="sxs-lookup"><span data-stu-id="ee3b4-230">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="ee3b4-231">Następnie Dodaj kod, aby wysłać dane wejściowe ze strony sieci Web do `OnGetAnalyzeSentiment` procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-231">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="ee3b4-232">W pliku *site. js* znajdującym się w katalogu *wwwroot\js* Utwórz funkcję o nazwie `getSentiment` , aby wykonać żądanie Get http `OnGetAnalyzeSentiment` z danymi wejściowymi użytkownika do programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-232">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="ee3b4-233">Poniżej można dodać kolejną funkcję o nazwie `updateMarker` , aby dynamicznie aktualizować pozycję znacznika na stronie sieci Web w miarę przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-233">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="ee3b4-234">Utwórz funkcję programu obsługi zdarzeń o `updateSentiment` nazwie, aby pobrać dane wejściowe od użytkownika, wysłać je `OnGetAnalyzeSentiment` do funkcji przy użyciu `getSentiment` funkcji i zaktualizować znacznik przy `updateMarker` użyciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-234">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="ee3b4-235">Na koniec Zarejestruj program obsługi zdarzeń i powiąż go `textarea` `id=Message` z elementem z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-235">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="ee3b4-236">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ee3b4-236">Run the application</span></span>

<span data-ttu-id="ee3b4-237">Teraz, gdy aplikacja jest skonfigurowana, uruchom aplikację, która powinna być uruchamiana w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-237">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="ee3b4-238">Po uruchomieniu aplikacji, wprowadź *wartość Konstruktor modeli jest chłodna!*</span><span class="sxs-lookup"><span data-stu-id="ee3b4-238">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="ee3b4-239">w obszarze tekstu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-239">into the text area.</span></span> <span data-ttu-id="ee3b4-240">Wyświetlona tonacji nie powinna być *toksyczna*.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-240">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="ee3b4-241">Jeśli musisz odwołać się do projektów wygenerowanych przez konstruktora modeli w późniejszym czasie w innym rozwiązaniu, możesz je znaleźć `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` w katalogu.</span><span class="sxs-lookup"><span data-stu-id="ee3b4-241">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ee3b4-242">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ee3b4-242">Next steps</span></span>

<span data-ttu-id="ee3b4-243">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ee3b4-243">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ee3b4-244">Tworzenie aplikacji Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ee3b4-244">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="ee3b4-245">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="ee3b4-245">Prepare and understand the data</span></span>
> - <span data-ttu-id="ee3b4-246">Wybierz scenariusz</span><span class="sxs-lookup"><span data-stu-id="ee3b4-246">Choose a scenario</span></span>
> - <span data-ttu-id="ee3b4-247">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="ee3b4-247">Load the data</span></span>
> - <span data-ttu-id="ee3b4-248">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="ee3b4-248">Train the model</span></span>
> - <span data-ttu-id="ee3b4-249">Oceń model</span><span class="sxs-lookup"><span data-stu-id="ee3b4-249">Evaluate the model</span></span>
> - <span data-ttu-id="ee3b4-250">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="ee3b4-250">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ee3b4-251">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="ee3b4-251">Additional Resources</span></span>

<span data-ttu-id="ee3b4-252">Aby dowiedzieć się więcej na temat tematów wymienionych w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="ee3b4-252">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="ee3b4-253">Scenariusze konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="ee3b4-253">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="ee3b4-254">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="ee3b4-254">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="ee3b4-255">Metryki binarnego modelu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="ee3b4-255">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
