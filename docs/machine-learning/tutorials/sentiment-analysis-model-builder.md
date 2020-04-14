---
title: 'Samouczek: Analizowanie tonacji - klasyfikacja binarna'
description: W tym samouczku pokazano, jak utworzyć aplikację Razor Pages, która klasyfikuje tonację z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Klasyfikator tonacji binarnych używa kreatora modelu w programie Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 7761240055c90ae9c713b1c460e9e83316d256f9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278954"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="738aa-104">Samouczek: Analizowanie tonacji komentarzy witryn sieci Web w aplikacji internetowej przy użyciu ML.NET Kreatora modeli</span><span class="sxs-lookup"><span data-stu-id="738aa-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="738aa-105">Dowiedz się, jak analizować tonację z komentarzy w czasie rzeczywistym wewnątrz aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="738aa-105">Learn how to analyze sentiment from comments in real time inside a web application.</span></span>

<span data-ttu-id="738aa-106">W tym samouczku pokazano, jak utworzyć aplikację ASP.NET Core Razor Pages, która klasyfikuje tonację z komentarzy witryny w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="738aa-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real time.</span></span>

<span data-ttu-id="738aa-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="738aa-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="738aa-108">Tworzenie aplikacji ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="738aa-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="738aa-109">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="738aa-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="738aa-110">Wybieranie scenariusza</span><span class="sxs-lookup"><span data-stu-id="738aa-110">Choose a scenario</span></span>
> - <span data-ttu-id="738aa-111">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="738aa-111">Load the data</span></span>
> - <span data-ttu-id="738aa-112">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="738aa-112">Train the model</span></span>
> - <span data-ttu-id="738aa-113">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="738aa-113">Evaluate the model</span></span>
> - <span data-ttu-id="738aa-114">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="738aa-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="738aa-115">Kreator modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="738aa-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="738aa-116">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples)</span><span class="sxs-lookup"><span data-stu-id="738aa-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="738aa-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="738aa-117">Pre-requisites</span></span>

<span data-ttu-id="738aa-118">Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, zapoznaj się z [podręcznikiem instalacji Kreatora modeli.](../how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="738aa-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="738aa-119">Tworzenie aplikacji Razor Pages</span><span class="sxs-lookup"><span data-stu-id="738aa-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="738aa-120">Utwórz **aplikację ASP.NET Core Razor Pages**.</span><span class="sxs-lookup"><span data-stu-id="738aa-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="738aa-121">Otwórz program Visual Studio i wybierz **polecenie Plik > Nowy projekt >** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="738aa-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="738aa-122">W oknie dialogowym Nowy projekt wybierz węzeł **Visual C#,** po którym następuje węzeł **sieci Web.**</span><span class="sxs-lookup"><span data-stu-id="738aa-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="738aa-123">Następnie wybierz szablon projektu **ASP.NET Core Web Application.**</span><span class="sxs-lookup"><span data-stu-id="738aa-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="738aa-124">W polu **tekstowym Nazwa** wpisz "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="738aa-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="738aa-125">Upewnij **się,** że rozwiązanie i projekt Umieść w tym samym katalogu **nie są zaznaczone** (VS 2019) lub **Sprawdź katalog** Create **dla rozwiązania** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="738aa-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="738aa-126">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="738aa-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="738aa-127">Wybierz **pozycję Aplikacja sieci Web** w oknie, w które są wyświetlane różne typy ASP.NET projektów podstawowych, a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="738aa-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="738aa-128">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="738aa-128">Prepare and understand the data</span></span>

<span data-ttu-id="738aa-129">Pobierz [zestaw danych Detox Wikipedia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="738aa-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="738aa-130">Po otwarciu strony sieci Web kliknij prawym przyciskiem myszy stronę, wybierz pozycję **Zapisz jako** i zapisz plik w dowolnym miejscu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="738aa-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="738aa-131">Każdy wiersz w zestawie danych *wikipedia-detox-250-line-data.tsv* reprezentuje inną recenzję pozostawioną przez użytkownika w Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="738aa-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="738aa-132">Pierwsza kolumna reprezentuje tonację tekstu (0 jest nietoksyczna, 1 jest toksyczna), a druga kolumna reprezentuje komentarz pozostawiony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="738aa-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="738aa-133">Kolumny są oddzielone kartami.</span><span class="sxs-lookup"><span data-stu-id="738aa-133">The columns are separated by tabs.</span></span> <span data-ttu-id="738aa-134">Dane wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="738aa-134">The data looks like the following:</span></span>

| <span data-ttu-id="738aa-135">Opinia</span><span class="sxs-lookup"><span data-stu-id="738aa-135">Sentiment</span></span> | <span data-ttu-id="738aa-136">SentimentText (Tekst sentymentu)</span><span class="sxs-lookup"><span data-stu-id="738aa-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="738aa-137">1</span><span class="sxs-lookup"><span data-stu-id="738aa-137">1</span></span> | <span data-ttu-id="738aa-138">==RUDE== Koleś, jesteś niegrzeczny przesłać, że carl zdjęcie z powrotem, albo inaczej.</span><span class="sxs-lookup"><span data-stu-id="738aa-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="738aa-139">1</span><span class="sxs-lookup"><span data-stu-id="738aa-139">1</span></span> | <span data-ttu-id="738aa-140">== OK!</span><span class="sxs-lookup"><span data-stu-id="738aa-140">== OK!</span></span> <span data-ttu-id="738aa-141">== IM BĘDZIE VANDALIZE WILD ONES WIKI NASTĘPNIE!!!</span><span class="sxs-lookup"><span data-stu-id="738aa-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="738aa-142">0</span><span class="sxs-lookup"><span data-stu-id="738aa-142">0</span></span> | <span data-ttu-id="738aa-143">Mam nadzieję, że to pomaga.</span><span class="sxs-lookup"><span data-stu-id="738aa-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="738aa-144">Wybieranie scenariusza</span><span class="sxs-lookup"><span data-stu-id="738aa-144">Choose a scenario</span></span>

![Kreator konstruktora modeli w programie Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="738aa-146">Aby uszkolić model, należy wybrać z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez program Model Builder.</span><span class="sxs-lookup"><span data-stu-id="738aa-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="738aa-147">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *SentimentRazor* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.</span><span class="sxs-lookup"><span data-stu-id="738aa-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="738aa-148">W tym przykładzie scenariusz jest analiza tonacji.</span><span class="sxs-lookup"><span data-stu-id="738aa-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="738aa-149">W kroku *scenariusza* narzędzia Konstruktor modelu wybierz scenariusz **analizy tonacji.**</span><span class="sxs-lookup"><span data-stu-id="738aa-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="738aa-150">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="738aa-150">Load the data</span></span>

<span data-ttu-id="738aa-151">Kreator modeli akceptuje dane z dwóch źródeł: bazy danych programu `csv` `tsv` SQL Server lub pliku lokalnego w formacie lub w formacie.</span><span class="sxs-lookup"><span data-stu-id="738aa-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="738aa-152">W kroku danych narzędzia Konstruktor modelu wybierz pozycję **Plik** z listy rozwijanej źródła danych.</span><span class="sxs-lookup"><span data-stu-id="738aa-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="738aa-153">Wybierz przycisk obok pola **tekstowego Wybierz plik** i użyj Eksploratora plików do przeglądania i wybierz plik *wikipedia-detox-250-line-data.tsv.*</span><span class="sxs-lookup"><span data-stu-id="738aa-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="738aa-154">Wybierz **pozycję Ton w** **kolumnie do wytyczenia (etykieta).**</span><span class="sxs-lookup"><span data-stu-id="738aa-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="738aa-155">Pozostaw wartości domyślne dla listy **rozwijanej Kolumny wejściowe (Funkcje).**</span><span class="sxs-lookup"><span data-stu-id="738aa-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="738aa-156">Wybierz **łącze Pociąg,** aby przejść do następnego kroku w narzędziu Kreator modeli.</span><span class="sxs-lookup"><span data-stu-id="738aa-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="738aa-157">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="738aa-157">Train the model</span></span>

<span data-ttu-id="738aa-158">Zadanie uczenia maszynowego używane do uczenia modelu analizy tonacji w tym samouczku jest klasyfikacja binarna.</span><span class="sxs-lookup"><span data-stu-id="738aa-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="738aa-159">Podczas procesu szkolenia modelu Model Builder trenuje oddzielne modele przy użyciu różnych algorytmów klasyfikacji binarnej i ustawień, aby znaleźć model o najwyższej wydajności dla zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="738aa-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="738aa-160">Czas wymagany do szkolenia modelu jest proporcjonalny do ilości danych.</span><span class="sxs-lookup"><span data-stu-id="738aa-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="738aa-161">Kreator modelu automatycznie wybiera wartość domyślną **dla czasu do wytrenowania (sekundy)** na podstawie rozmiaru źródła danych.</span><span class="sxs-lookup"><span data-stu-id="738aa-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="738aa-162">Chociaż Kreator modeli ustawia wartość **czas do pociągu (sekundy)** do 10 sekund, należy zwiększyć go do 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="738aa-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="738aa-163">Szkolenie przez dłuższy okres czasu pozwala Programowi Model Builder eksplorować większą liczbę algorytmów i kombinacji parametrów w poszukiwaniu najlepszego modelu.</span><span class="sxs-lookup"><span data-stu-id="738aa-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="738aa-164">Wybierz **pozycję Rozpocznij szkolenie**.</span><span class="sxs-lookup"><span data-stu-id="738aa-164">Select **Start Training**.</span></span>

    <span data-ttu-id="738aa-165">W trakcie całego procesu szkolenia dane o `Progress` postępach są wyświetlane w sekcji kroku pociągu.</span><span class="sxs-lookup"><span data-stu-id="738aa-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="738aa-166">Stan wyświetla stan ukończenia procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="738aa-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="738aa-167">Najlepsza dokładność wyświetla dokładność najlepszego modelu znalezionego do tej pory przez Model Builder.</span><span class="sxs-lookup"><span data-stu-id="738aa-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="738aa-168">Większa dokładność oznacza, że model przewidział bardziej poprawnie na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="738aa-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="738aa-169">Najlepszy algorytm wyświetla nazwę najlepiej działającego algorytmu wykonywanego do tej pory przez Model Builder.</span><span class="sxs-lookup"><span data-stu-id="738aa-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="738aa-170">Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez program Model Builder do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="738aa-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="738aa-171">Po zakończeniu szkolenia wybierz łącze **oceny,** aby przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="738aa-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="738aa-172">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="738aa-172">Evaluate the model</span></span>

<span data-ttu-id="738aa-173">Wynikiem etapu szkolenia będzie jeden model, który ma najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="738aa-173">The result of the training step will be one model that has the best performance.</span></span> <span data-ttu-id="738aa-174">W kroku oceny narzędzia Model Builder sekcja wyjściowa będzie zawierać algorytm używany przez model o najlepszej wydajności we wpisie **Najlepszy model** wraz z metrykami w **sekcji Najlepsza dokładność modelu**.</span><span class="sxs-lookup"><span data-stu-id="738aa-174">In the evaluate step of the Model Builder tool, the output section will contain the algorithm used by the best-performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="738aa-175">Ponadto wyświetlana jest tabela podsumowania zawierająca pięć najlepszych modeli i ich metryki.</span><span class="sxs-lookup"><span data-stu-id="738aa-175">Additionally, a summary table containing the top five models and their metrics is shown.</span></span>

<span data-ttu-id="738aa-176">Jeśli nie jesteś zadowolony z metryk dokładności, niektóre proste sposoby, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych.</span><span class="sxs-lookup"><span data-stu-id="738aa-176">If you're not satisfied with your accuracy metrics, some easy ways to try to improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="738aa-177">W przeciwnym razie wybierz łącze **kodu,** aby przejść do ostatniego kroku w narzędziu Konstruktor modelu.</span><span class="sxs-lookup"><span data-stu-id="738aa-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="738aa-178">Dodaj kod, aby przewidywać</span><span class="sxs-lookup"><span data-stu-id="738aa-178">Add the code to make predictions</span></span>

<span data-ttu-id="738aa-179">W wyniku procesu szkolenia zostaną utworzone dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="738aa-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="738aa-180">Odwoływanie się do wyszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="738aa-180">Reference the trained model</span></span>

1. <span data-ttu-id="738aa-181">W kroku *kodu* narzędzia Kreator modelu wybierz pozycję **Dodaj projekty,** aby dodać projekty z autogenerowanymi do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="738aa-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="738aa-182">W **Eksploratorze rozwiązań**powinny pojawić się następujące projekty:</span><span class="sxs-lookup"><span data-stu-id="738aa-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="738aa-183">*SentimentRazorML.ConsoleApp*: Aplikacja .NET Core Console, która zawiera kod szkolenia i przewidywania modelu.</span><span class="sxs-lookup"><span data-stu-id="738aa-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="738aa-184">*SentimentRazorML.Model*: Biblioteka klas .NET Standard zawierająca modele danych definiujące schemat danych modelu wejściowego i wyjściowego, a także zapisaną wersję modelu o najwyższej wydajności podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="738aa-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="738aa-185">W tym samouczku używany jest tylko projekt *SentimentRazorML.Model,* ponieważ prognozy będą dokonywane w aplikacji internetowej *SentimentRazor,* a nie w konsoli.</span><span class="sxs-lookup"><span data-stu-id="738aa-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="738aa-186">Mimo *że SentimentRazorML.ConsoleApp* nie będzie używany do oceniania, może służyć do ponownego przeszkolenia modelu przy użyciu nowych danych w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="738aa-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="738aa-187">Przekwalifikowanie jest jednak poza zakresem tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="738aa-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="738aa-188">Konfigurowanie puli predictionengine</span><span class="sxs-lookup"><span data-stu-id="738aa-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="738aa-189">Aby dokonać pojedynczego przewidywania, należy <xref:Microsoft.ML.PredictionEngine%602>utworzyć plik .</span><span class="sxs-lookup"><span data-stu-id="738aa-189">To make a single prediction, you have to create a <xref:Microsoft.ML.PredictionEngine%602>.</span></span> <span data-ttu-id="738aa-190"><xref:Microsoft.ML.PredictionEngine%602>nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="738aa-190"><xref:Microsoft.ML.PredictionEngine%602> is not thread-safe.</span></span> <span data-ttu-id="738aa-191">Ponadto należy utworzyć wystąpienie wszędzie tam, gdzie jest to potrzebne w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="738aa-191">Additionally, you have to create an instance of it everywhere it's needed within your application.</span></span> <span data-ttu-id="738aa-192">W miarę rozwoju aplikacji proces ten może stać się nie do opanowania.</span><span class="sxs-lookup"><span data-stu-id="738aa-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="738aa-193">Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji iniekcji zależności i usługi, która tworzy <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601> obiekty <xref:Microsoft.ML.PredictionEngine%602> do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="738aa-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601> of <xref:Microsoft.ML.PredictionEngine%602> objects for use throughout your application.</span></span>

1. <span data-ttu-id="738aa-194">Zainstaluj pakiet *Microsoft.Extensions.ML* NuGet:</span><span class="sxs-lookup"><span data-stu-id="738aa-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="738aa-195">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="738aa-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="738aa-196">Wybierz "nuget.org" jako źródło pakietu.</span><span class="sxs-lookup"><span data-stu-id="738aa-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="738aa-197">Wybierz kartę **Przeglądaj** i wyszukaj **Microsoft.Extensions.ML**.</span><span class="sxs-lookup"><span data-stu-id="738aa-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="738aa-198">Wybierz pakiet na liście i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="738aa-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="738aa-199">Wybieranie przycisku **OK** w oknie dialogowym **Podgląd zmian**</span><span class="sxs-lookup"><span data-stu-id="738aa-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="738aa-200">Wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="738aa-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="738aa-201">Otwórz plik *Startup.cs* w projekcie *SentimentRazor.*</span><span class="sxs-lookup"><span data-stu-id="738aa-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="738aa-202">Dodaj następujące instrukcje przy użyciu odwołań do *Microsoft.Extensions.ML* pakietu NuGet i projektu *SentimentRazorML.Model:*</span><span class="sxs-lookup"><span data-stu-id="738aa-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="738aa-203">Utwórz zmienną globalną do przechowywania lokalizacji pliku modelu uczonego.</span><span class="sxs-lookup"><span data-stu-id="738aa-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="738aa-204">Plik modelu jest przechowywany w katalogu kompilacji obok plików zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="738aa-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="738aa-205">Aby ułatwić dostęp, należy utworzyć metodę pomocnika `GetAbsolutePath` wywołaną `Configure` po</span><span class="sxs-lookup"><span data-stu-id="738aa-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="738aa-206">Użyj `GetAbsolutePath` metody w `Startup` konstruktorze `_modelPath`klasy, aby ustawić .</span><span class="sxs-lookup"><span data-stu-id="738aa-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="738aa-207">Skonfiguruj `PredictionEnginePool` dla `ConfigureServices` aplikacji w metodzie:</span><span class="sxs-lookup"><span data-stu-id="738aa-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="738aa-208">Tworzenie programu obsługi analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="738aa-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="738aa-209">Prognozy zostaną dokonane wewnątrz głównej strony aplikacji.</span><span class="sxs-lookup"><span data-stu-id="738aa-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="738aa-210">W związku z tym metoda, która przyjmuje `PredictionEnginePool` dane wejściowe użytkownika i używa do zwrócenia prognozowania musi zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="738aa-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="738aa-211">Otwórz plik *Index.cshtml.cs* znajdujący się w katalogu *Pages* i dodaj następujące elementy za pomocą instrukcji:</span><span class="sxs-lookup"><span data-stu-id="738aa-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="738aa-212">Aby użyć `PredictionEnginePool` skonfigurowane w `Startup` klasie, należy wstrzyknąć go do konstruktora modelu, w którym chcesz go używać.</span><span class="sxs-lookup"><span data-stu-id="738aa-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="738aa-213">Dodaj zmienną, `PredictionEnginePool` aby `IndexModel` odwołać się do wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="738aa-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="738aa-214">Utwórz konstruktora `IndexModel` w `PredictionEnginePool` klasie i wstrzyknąć do niej usługę.</span><span class="sxs-lookup"><span data-stu-id="738aa-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="738aa-215">Utwórz program obsługi metody, który używa `PredictionEnginePool` do przewidywania z danych wejściowych użytkownika otrzymanych ze strony sieci web.</span><span class="sxs-lookup"><span data-stu-id="738aa-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="738aa-216">Poniżej `OnGet` metody utwórz nową metodę o nazwie`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="738aa-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="738aa-217">Wewnątrz `OnGetAnalyzeSentiment` metody *zwracane nastroje neutralne,* jeśli dane wejściowe od użytkownika jest puste lub null.</span><span class="sxs-lookup"><span data-stu-id="738aa-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="738aa-218">Biorąc pod uwagę prawidłowe dane `ModelInput`wejściowe, utwórz nowe wystąpienie .</span><span class="sxs-lookup"><span data-stu-id="738aa-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="738aa-219">Użyj `PredictionEnginePool` do przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="738aa-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="738aa-220">Przekonwertować `bool` przewidywaną wartość na toksyczną lub nietoksyną za pomocą następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="738aa-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="738aa-221">Na koniec wróć do sentymentu na stronie internetowej.</span><span class="sxs-lookup"><span data-stu-id="738aa-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="738aa-222">Konfigurowanie strony internetowej</span><span class="sxs-lookup"><span data-stu-id="738aa-222">Configure the web page</span></span>

<span data-ttu-id="738aa-223">Wyniki zwracane `OnGetAnalyzeSentiment` przez będą dynamicznie wyświetlane `Index` na stronie internetowej.</span><span class="sxs-lookup"><span data-stu-id="738aa-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="738aa-224">Otwórz plik *Index.cshtml* w katalogu *Pages* i zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="738aa-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="738aa-225">Następnie dodaj kod stylizacj css na końcu strony *site.css* w katalogu *wwwroot\css:*</span><span class="sxs-lookup"><span data-stu-id="738aa-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="738aa-226">Następnie dodaj kod, aby wysłać dane wejściowe ze strony sieci web do `OnGetAnalyzeSentiment` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="738aa-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="738aa-227">W pliku *site.js* znajdującym się w katalogu *wwwroot\js* utwórz funkcję wywoływaną `getSentiment` w `OnGetAnalyzeSentiment` celu utworzenia żądania GET HTTP z wprowadzeniem danych użytkownika do programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="738aa-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="738aa-228">Poniżej dodaj inną `updateMarker` funkcję wywoływanej w celu dynamicznej aktualizacji położenia znacznika na stronie internetowej w miarę przewidywania tonacji.</span><span class="sxs-lookup"><span data-stu-id="738aa-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="738aa-229">Utwórz funkcję obsługi `updateSentiment` zdarzeń wywoływaną w celu uzyskania `OnGetAnalyzeSentiment` danych wejściowych od użytkownika, wyślij je do funkcji za pomocą `getSentiment` funkcji i zaktualizuj znacznik za `updateMarker` pomocą funkcji.</span><span class="sxs-lookup"><span data-stu-id="738aa-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="738aa-230">Na koniec zarejestruj program obsługi zdarzeń `textarea` i powiąż go z elementem z atrybutem. `id=Message`</span><span class="sxs-lookup"><span data-stu-id="738aa-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="738aa-231">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="738aa-231">Run the application</span></span>

<span data-ttu-id="738aa-232">Teraz, gdy aplikacja jest skonfigurowana, uruchom aplikację, która powinna zostać uruchomiona w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="738aa-232">Now that your application is set up, run the application, which should launch in your browser.</span></span>

<span data-ttu-id="738aa-233">Po uruchomieniu aplikacji, wprowadź *Model Builder jest cool!*</span><span class="sxs-lookup"><span data-stu-id="738aa-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="738aa-234">w obszarze tekstowym.</span><span class="sxs-lookup"><span data-stu-id="738aa-234">into the text area.</span></span> <span data-ttu-id="738aa-235">Przewidywany sentyment wyświetlany powinien być *nie toksyczny*.</span><span class="sxs-lookup"><span data-stu-id="738aa-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Okno uruchomione z przewidywanym oknem tonacji](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="738aa-237">Jeśli chcesz odwołać się do projektów generowanych przez program Model Builder w `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` późniejszym czasie wewnątrz innego rozwiązania, można je znaleźć w katalogu.</span><span class="sxs-lookup"><span data-stu-id="738aa-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="738aa-238">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="738aa-238">Next steps</span></span>

<span data-ttu-id="738aa-239">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="738aa-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="738aa-240">Tworzenie aplikacji ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="738aa-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="738aa-241">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="738aa-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="738aa-242">Wybieranie scenariusza</span><span class="sxs-lookup"><span data-stu-id="738aa-242">Choose a scenario</span></span>
> - <span data-ttu-id="738aa-243">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="738aa-243">Load the data</span></span>
> - <span data-ttu-id="738aa-244">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="738aa-244">Train the model</span></span>
> - <span data-ttu-id="738aa-245">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="738aa-245">Evaluate the model</span></span>
> - <span data-ttu-id="738aa-246">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="738aa-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="738aa-247">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="738aa-247">Additional Resources</span></span>

<span data-ttu-id="738aa-248">Aby dowiedzieć się więcej o tematach wymienionych w tym samouczku, odwiedź następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="738aa-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="738aa-249">Scenariusze konstruktora modeli</span><span class="sxs-lookup"><span data-stu-id="738aa-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="738aa-250">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="738aa-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="738aa-251">Metryki modelu klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="738aa-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
