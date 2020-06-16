---
title: Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET
description: Automatycznie Generuj model ML i powiązany kod C# z przykładowego zestawu danych
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: aab59463daad30748277602b9ab1d8ca2f3fa1f5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767679"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="ab43a-103">Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="ab43a-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="ab43a-104">Dowiedz się, jak używać interfejsu wiersza polecenia ML.NET do automatycznego generowania modelu ML.NET i bazowego kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ab43a-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="ab43a-105">Podajesz zestaw danych i zadanie uczenia maszynowego, które chcesz zaimplementować, a interfejs wiersza polecenia używa aparatu AutoML do tworzenia kodu źródłowego generacji i wdrożenia modelu oraz modelu klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="ab43a-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the classification model.</span></span>

<span data-ttu-id="ab43a-106">W tym samouczku wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ab43a-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ab43a-107">Przygotuj dane dla wybranego zadania uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="ab43a-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="ab43a-108">Uruchom polecenie "mlnet klasyfikację" w interfejsie wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ab43a-108">Run the 'mlnet classification' command from the CLI</span></span>
> - <span data-ttu-id="ab43a-109">Przejrzyj wyniki metryki jakości</span><span class="sxs-lookup"><span data-stu-id="ab43a-109">Review the quality metric results</span></span>
> - <span data-ttu-id="ab43a-110">Poznaj wygenerowany kod C#, aby użyć modelu w aplikacji</span><span class="sxs-lookup"><span data-stu-id="ab43a-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="ab43a-111">Eksplorowanie wygenerowanego kodu w języku C#, który został użyty do uczenia modelu</span><span class="sxs-lookup"><span data-stu-id="ab43a-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="ab43a-112">Ten temat odnosi się do narzędzia interfejsu wiersza polecenia ML.NET, które jest obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ab43a-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ab43a-113">Aby uzyskać więcej informacji, odwiedź stronę [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="ab43a-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="ab43a-114">Interfejs wiersza polecenia ML.NET jest częścią ML.NET i jej głównym celem jest "zdemokratyzuj proces" ML.NET dla deweloperów platformy .NET, gdy uczysz się, że nie musisz uruchamiać kodu od podstaw, aby rozpocząć pracę.</span><span class="sxs-lookup"><span data-stu-id="ab43a-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="ab43a-115">Interfejs wiersza polecenia ML.NET można uruchomić we wszystkich wierszach poleceń (Windows, Mac lub Linux) w celu wygenerowania dobrej jakości modeli ML.NET i kodu źródłowego na podstawie podanych szkoleń.</span><span class="sxs-lookup"><span data-stu-id="ab43a-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ab43a-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ab43a-116">Pre-requisites</span></span>

- <span data-ttu-id="ab43a-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="ab43a-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) or later</span></span>
- <span data-ttu-id="ab43a-118">Obowiązkowe [Program Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="ab43a-118">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="ab43a-119">Interfejs wiersza polecenia struktury ML.NET</span><span class="sxs-lookup"><span data-stu-id="ab43a-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="ab43a-120">Można uruchomić wygenerowane projekty kodu C# z programu Visual Studio lub z `dotnet run` (interfejs wiersza polecenia platformy .NET Core).</span><span class="sxs-lookup"><span data-stu-id="ab43a-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="ab43a-121">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ab43a-121">Prepare your data</span></span>

<span data-ttu-id="ab43a-122">Zamierzamy użyć istniejącego zestawu danych, który będzie używany dla scenariusza "analiza tonacji", czyli binarnego zadania uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ab43a-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="ab43a-123">Możesz użyć własnego zestawu danych w podobny sposób, a model i kod zostanie wygenerowany dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="ab43a-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="ab43a-124">Pobierz [tonacji z oznaczeniem "UCI" (zobacz Cytaty w poniższej notatce)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj go do wybranego folderu.</span><span class="sxs-lookup"><span data-stu-id="ab43a-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab43a-125">Zestawy danych, w tym samouczku, korzystają z zestawu DataSet z grupy "from" do poszczególnych etykiet przy użyciu funkcji głębokiej, Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="ab43a-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="ab43a-126">KDD 2015 i hostowana w repozytorium Machine Learning/Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="ab43a-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="ab43a-127">/Na Machine Learning repozytorium [ http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="ab43a-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="ab43a-128">Irvine, CA: University of Kalifornii, szkolna informacja i nauka komputera.</span><span class="sxs-lookup"><span data-stu-id="ab43a-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="ab43a-129">Skopiuj `yelp_labelled.txt` plik do folderu, który został wcześniej utworzony (na przykład `/cli-test` ).</span><span class="sxs-lookup"><span data-stu-id="ab43a-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="ab43a-130">Otwórz preferowany wiersz polecenia i przejdź do folderu, do którego skopiowano plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ab43a-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="ab43a-131">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ab43a-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="ab43a-132">Za pomocą dowolnego edytora tekstu, takiego jak Visual Studio Code, można otworzyć i eksplorować `yelp_labelled.txt` plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ab43a-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="ab43a-133">Można zobaczyć, że struktura jest:</span><span class="sxs-lookup"><span data-stu-id="ab43a-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="ab43a-134">Plik nie ma nagłówka.</span><span class="sxs-lookup"><span data-stu-id="ab43a-134">The file has no header.</span></span> <span data-ttu-id="ab43a-135">Będziesz używać indeksu kolumny.</span><span class="sxs-lookup"><span data-stu-id="ab43a-135">You will use the column's index.</span></span>

    - <span data-ttu-id="ab43a-136">Istnieją tylko dwie kolumny:</span><span class="sxs-lookup"><span data-stu-id="ab43a-136">There are just two columns:</span></span>

        | <span data-ttu-id="ab43a-137">Tekst (indeks kolumn 0)</span><span class="sxs-lookup"><span data-stu-id="ab43a-137">Text (Column index 0)</span></span> | <span data-ttu-id="ab43a-138">Etykieta (indeks kolumn 1)</span><span class="sxs-lookup"><span data-stu-id="ab43a-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="ab43a-139">Wow... Uwielbiane to miejsce.</span><span class="sxs-lookup"><span data-stu-id="ab43a-139">Wow... Loved this place.</span></span> | <span data-ttu-id="ab43a-140">1</span><span class="sxs-lookup"><span data-stu-id="ab43a-140">1</span></span> |
        | <span data-ttu-id="ab43a-141">Crust nie jest dobry.</span><span class="sxs-lookup"><span data-stu-id="ab43a-141">Crust is not good.</span></span> | <span data-ttu-id="ab43a-142">0</span><span class="sxs-lookup"><span data-stu-id="ab43a-142">0</span></span> |
        | <span data-ttu-id="ab43a-143">Nie Tasty, a tekstura była paskudnycha.</span><span class="sxs-lookup"><span data-stu-id="ab43a-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="ab43a-144">0</span><span class="sxs-lookup"><span data-stu-id="ab43a-144">0</span></span> |
        | <span data-ttu-id="ab43a-145">... WIELE WIĘCEJ WIERSZY TEKSTU...</span><span class="sxs-lookup"><span data-stu-id="ab43a-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="ab43a-146">... (1 lub 0)...</span><span class="sxs-lookup"><span data-stu-id="ab43a-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="ab43a-147">Upewnij się, że plik DataSet został zamknięty z edytora.</span><span class="sxs-lookup"><span data-stu-id="ab43a-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="ab43a-148">Teraz możesz zacząć korzystać z interfejsu wiersza polecenia dla tego scenariusza "analiza tonacji".</span><span class="sxs-lookup"><span data-stu-id="ab43a-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab43a-149">Po ukończeniu tego samouczka możesz również wypróbować własne zestawy danych, o ile są one gotowe do użycia dla każdego z zadań w ML, które są obecnie obsługiwane przez ML.NET interfejsu wiersza polecenia, które są *"klasyfikacją binarną", "Klasyfikacja", "regresja* " i *"rekomendacja"*.</span><span class="sxs-lookup"><span data-stu-id="ab43a-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Classification', 'Regression',* and *'Recommendation'*.</span></span>

## <a name="run-the-mlnet-classification-command"></a><span data-ttu-id="ab43a-150">Uruchom polecenie "mlnet klasyfikację"</span><span class="sxs-lookup"><span data-stu-id="ab43a-150">Run the 'mlnet classification' command</span></span>

1. <span data-ttu-id="ab43a-151">Uruchom następujące polecenie interfejsu wiersza polecenia ML.NET:</span><span class="sxs-lookup"><span data-stu-id="ab43a-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    <span data-ttu-id="ab43a-152">To polecenie uruchamia \*\* `mlnet classification` polecenie\*\*:</span><span class="sxs-lookup"><span data-stu-id="ab43a-152">This command runs the **`mlnet classification` command**:</span></span>
    - <span data-ttu-id="ab43a-153">dla **zadania ml** *klasyfikacji*</span><span class="sxs-lookup"><span data-stu-id="ab43a-153">for the **ML task** of *classification*</span></span>
    - <span data-ttu-id="ab43a-154">używa **pliku `yelp_labelled.txt` DataSet** jako zestawu danych szkoleniowych i testowych (wewnętrznie w interfejsie wiersza polecenia będzie można użyć weryfikacji krzyżowej lub podzielić ją na dwa zestawy danych, jeden do szkolenia i jeden do testowania).</span><span class="sxs-lookup"><span data-stu-id="ab43a-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="ab43a-155">gdzie **kolumna cel/cel** , która ma zostać przewidywalna (zazwyczaj nazywana **"etykietą"**) jest **kolumną o indeksie 1** (jest to druga kolumna, ponieważ indeks jest liczony od zera)</span><span class="sxs-lookup"><span data-stu-id="ab43a-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="ab43a-156">nie **używa nagłówka pliku** z nazwami kolumn, ponieważ ten określony plik zestawu danych nie ma nagłówka</span><span class="sxs-lookup"><span data-stu-id="ab43a-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="ab43a-157">**przekierowany czas eksploracji/uczenia** dla eksperymentu wynosi **10 sekund**</span><span class="sxs-lookup"><span data-stu-id="ab43a-157">the **targeted exploration/train time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="ab43a-158">Zostaną wyświetlone dane wyjściowe z interfejsu wiersza polecenia, podobne do:</span><span class="sxs-lookup"><span data-stu-id="ab43a-158">You will see output from the CLI, similar to:</span></span>

    ![Klasyfikacja interfejsu wiersza polecenia ML.NET w programie PowerShell](./media/mlnet-cli/mlnet-classification-powershell.gif)

    <span data-ttu-id="ab43a-160">W tym konkretnym przypadku, w ciągu zaledwie 10 sekund i z podanym małym zestawem danych, narzędzie interfejsu wiersza polecenia było w stanie wykonać dość kilka iteracji, co oznacza szkolenie wiele razy na podstawie różnych kombinacji algorytmów/konfiguracji z różnymi wewnętrznymi transformacjami danych i parametrami funkcji Hyper-Parameters algorytmu.</span><span class="sxs-lookup"><span data-stu-id="ab43a-160">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="ab43a-161">Na koniec model "Najlepsza jakość" znaleziony w ciągu 10 sekund jest modelem używającym określonego Trainer/algorytmu z dowolną określoną konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="ab43a-161">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="ab43a-162">W zależności od czasu eksploracji polecenie może generować inny wynik.</span><span class="sxs-lookup"><span data-stu-id="ab43a-162">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="ab43a-163">Wybór jest oparty na wielu pokazanych metrykach, takich jak `Accuracy` .</span><span class="sxs-lookup"><span data-stu-id="ab43a-163">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="ab43a-164">**Informacje o metrykach jakości modelu**</span><span class="sxs-lookup"><span data-stu-id="ab43a-164">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="ab43a-165">Pierwszą i najłatwiejszą metryką do oszacowania modelu klasyfikacji binarnej jest dokładność, która jest łatwa do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="ab43a-165">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="ab43a-166">"Dokładność to stosunek prawidłowych prognoz z zestawem danych testowych".</span><span class="sxs-lookup"><span data-stu-id="ab43a-166">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="ab43a-167">Im bliżej 100% (1,00), tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="ab43a-167">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="ab43a-168">Istnieją jednak przypadki, w których pomiar dokładności jest niewystarczający, szczególnie wtedy, gdy etykieta (0 i 1 w tym przypadku) jest niezrównoważona w zestawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ab43a-168">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="ab43a-169">Aby uzyskać dodatkowe metryki i bardziej **szczegółowe informacje na temat metryk** , takich jak dokładność, AUC, AUCPR i F1-Score używane do oceny różnych modeli, zobacz [Opis metryk ml.NET](../resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="ab43a-169">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab43a-170">Możesz wypróbować ten sam zestaw danych i określić kilka minut `--max-exploration-time` (na przykład przez trzy minuty, aby określić 180 sekund), co umożliwi znalezienie lepszego "najlepszego modelu" z inną konfiguracją potoku szkolenia dla tego zestawu danych (który jest bardzo mały, 1000 wiersze).</span><span class="sxs-lookup"><span data-stu-id="ab43a-170">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="ab43a-171">Aby znaleźć model "Najlepsza/dobry", który jest "modelem gotowym do produkcji" przeznaczonym dla większych zestawów danych, należy przeprowadzić eksperymenty z interfejsem wiersza polecenia, zazwyczaj określając znacznie więcej czasu eksplorowania, w zależności od rozmiaru elementu DataSet.</span><span class="sxs-lookup"><span data-stu-id="ab43a-171">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="ab43a-172">W rzeczywistości w wielu przypadkach może być konieczne wielokrotne przeszukiwanie czasu, zwłaszcza jeśli zestaw danych jest duży dla wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="ab43a-172">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="ab43a-173">Poprzednie wykonanie polecenia spowodowało wygenerowanie następujących zasobów:</span><span class="sxs-lookup"><span data-stu-id="ab43a-173">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="ab43a-174">Serializowany model. zip ("najlepszy model") jest gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="ab43a-174">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="ab43a-175">Kod w języku C# do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych z tym modelem).</span><span class="sxs-lookup"><span data-stu-id="ab43a-175">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="ab43a-176">Kod szkoleniowy języka C# używany do generowania tego modelu (cele uczenia).</span><span class="sxs-lookup"><span data-stu-id="ab43a-176">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="ab43a-177">Plik dziennika ze wszystkimi iteracjami, które zostały zbadane, ze szczegółowymi informacjami na temat każdego z algorytmów, które podjęły kombinację parametrów i przekształceń danych funkcji Hyper-Parameters.</span><span class="sxs-lookup"><span data-stu-id="ab43a-177">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="ab43a-178">Pierwsze dwa elementy zawartości (. Model pliku ZIP i kod C# do uruchomienia tego modelu) mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu przeprowadzenia prognoz dla tego wygenerowanego modelu ML.</span><span class="sxs-lookup"><span data-stu-id="ab43a-178">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="ab43a-179">Trzeci element zawartości, kod szkoleniowy, pokazuje, w jaki sposób kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było sprawdzić, jakie konkretne Trainer/algorytm i parametry funkcji Hyper-Parameters zostały wybrane przez interfejs wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ab43a-179">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="ab43a-180">Te wyliczane zasoby zostały wyjaśnione w poniższych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="ab43a-180">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="ab43a-181">Eksploruj wygenerowany kod C#, który ma być używany do uruchamiania modelu w celu wykonywania prognoz</span><span class="sxs-lookup"><span data-stu-id="ab43a-181">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="ab43a-182">W programie Visual Studio (2017 lub 2019) Otwórz rozwiązanie wygenerowane w folderze o nazwie w `SampleClassification` oryginalnym folderze docelowym (w samouczku określono nazwę `/cli-test` ).</span><span class="sxs-lookup"><span data-stu-id="ab43a-182">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="ab43a-183">Powinno zostać wyświetlone rozwiązanie podobne do:</span><span class="sxs-lookup"><span data-stu-id="ab43a-183">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab43a-184">W samouczku zalecamy korzystanie z programu Visual Studio, ale możesz również eksplorować wygenerowany kod C# (dwa projekty) przy użyciu dowolnego edytora tekstów i uruchomić wygenerowaną aplikację konsolową z `dotnet CLI` maszyną z systemem macOS, Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="ab43a-184">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Rozwiązanie VS generowane przez interfejs wiersza polecenia](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - <span data-ttu-id="ab43a-186">Wygenerowanej **biblioteki klas** zawierającej serializowany model ml (plik. zip) i klasy danych (modele danych) to element, którego można bezpośrednio użyć w aplikacji użytkownika końcowego, nawet przez bezpośredni odwołujący się do tej biblioteki klas (lub przeniesienie kodu, zgodnie z potrzebami).</span><span class="sxs-lookup"><span data-stu-id="ab43a-186">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="ab43a-187">Wygenerowana **Aplikacja konsolowa** zawiera kod wykonywania, który należy przejrzeć, a następnie zazwyczaj ponownie użyjemy kodu oceniania (kod, który uruchamia model ml, aby dokonać prognoz), przenosząc ten prosty kod (zaledwie kilka wierszy) do aplikacji użytkownika końcowego, w której chcesz dokonać prognoz.</span><span class="sxs-lookup"><span data-stu-id="ab43a-187">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="ab43a-188">Otwórz pliki klas **ModelInput.cs** i **ModelOutput.cs** w projekcie biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="ab43a-188">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="ab43a-189">Zobaczysz, że te klasy są "klasami danych" lub klasy POCO używane do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="ab43a-189">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="ab43a-190">Jest to "kod standardowy", ale przydatny do wygenerowania, jeśli zestaw danych ma dziesiątki lub nawet setki kolumn.</span><span class="sxs-lookup"><span data-stu-id="ab43a-190">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="ab43a-191">`ModelInput`Klasa jest używana podczas odczytywania danych z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ab43a-191">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="ab43a-192">`ModelOutput`Klasa jest używana do uzyskiwania wyniku przewidywania (dane przewidywania).</span><span class="sxs-lookup"><span data-stu-id="ab43a-192">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="ab43a-193">Otwórz plik Program.cs i Eksploruj kod.</span><span class="sxs-lookup"><span data-stu-id="ab43a-193">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="ab43a-194">W zaledwie kilku wierszach można uruchomić model i utworzyć przykładowe przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ab43a-194">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - Pierwsze wiersze kodu tworzą *pojedyncze przykładowe dane*, w tym przypadku na podstawie pierwszego wiersza zestawu danych, który będzie używany do prognozowania. <span data-ttu-id="ab43a-196">Możesz również utworzyć własne "kodowane" dane, aktualizując kod:</span><span class="sxs-lookup"><span data-stu-id="ab43a-196">You can also create you own 'hard-coded' data by updating the code:</span></span>

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - <span data-ttu-id="ab43a-197">Następny wiersz kodu używa `ConsumeModel.Predict()` metody dla określonych danych wejściowych, aby utworzyć prognozę i zwrócić wyniki (na podstawie schematu ModelOutput.cs).</span><span class="sxs-lookup"><span data-stu-id="ab43a-197">The next line of code uses the `ConsumeModel.Predict()` method on the specified input data to make a prediction and return the results (based on the ModelOutput.cs schema).</span></span>
    - <span data-ttu-id="ab43a-198">Ostatni wiersz kodu drukuje proprties danych przykładowych (w tym przypadku komentarz), a także prognozowanie tonacji i odpowiadające im wyniki dla pozytywnych tonacji (1) i negatywnych tonacji (2).</span><span class="sxs-lookup"><span data-stu-id="ab43a-198">The last lines of code print out the proprties of the sample data (in this case the Comment) as well as the Sentiment prediction and corresponding Scores for positive sentiment (1) and negative sentiment (2).</span></span>

1. <span data-ttu-id="ab43a-199">Uruchom projekt, używając oryginalnych danych przykładowych załadowanych z pierwszego wiersza zestawu danych lub dostarczając własne, zakodowane Przykładowo dane.</span><span class="sxs-lookup"><span data-stu-id="ab43a-199">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="ab43a-200">Należy uzyskać prognozę, która jest porównywalna z:</span><span class="sxs-lookup"><span data-stu-id="ab43a-200">You should get a prediction comparable to:</span></span>

![Interfejs wiersza polecenia ML.NET uruchamia aplikację z programu Visual Studio](./media/mlnet-cli/mlnet-cli-console-app.png)<span data-ttu-id="ab43a-202">)</span><span class="sxs-lookup"><span data-stu-id="ab43a-202">)</span></span>

1. <span data-ttu-id="ab43a-203">Spróbuj zmienić zakodowane przykładowe dane na inne zdania o różnych tonacji i zobaczyć, jak model przewiduje pozytywne lub ujemne tonacji.</span><span class="sxs-lookup"><span data-stu-id="ab43a-203">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="ab43a-204">Dodaj aplikacji użytkowników końcowych przy użyciu prognoz modelu ML</span><span class="sxs-lookup"><span data-stu-id="ab43a-204">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="ab43a-205">Możesz użyć podobnego kodu oceniania modelu "ML", aby uruchomić model w aplikacji użytkownika końcowego i wprowadzić przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ab43a-205">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="ab43a-206">Na przykład można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznej systemu Windows, takiej jak **WPF** i **WinForms** , i uruchomić model w taki sam sposób, jak w przypadku aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="ab43a-206">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="ab43a-207">Jednak sposób implementacji tych wierszy kodu w celu uruchomienia modelu ML powinien zostać zoptymalizowany (to oznacza, że w pamięci podręcznej pliku model. zip jest załadowana) i ma pojedyncze obiekty zamiast tworzyć je w każdym żądaniu, zwłaszcza jeśli aplikacja musi być skalowalna, taka jak aplikacja sieci Web lub usługa rozproszona, zgodnie z opisem w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ab43a-207">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="ab43a-208">Uruchamianie modeli ML.NET w skalowalne ASP.NET Core aplikacje i usługi sieci Web (aplikacje wielowątkowe)</span><span class="sxs-lookup"><span data-stu-id="ab43a-208">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="ab43a-209">Tworzenie obiektu modelu ( `ITransformer` załadowane z pliku zip modelu) i `PredictionEngine` obiekt powinien być zoptymalizowany szczególnie w przypadku uruchamiania na skalowalnych aplikacjach internetowych i usługach rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="ab43a-209">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="ab43a-210">Dla pierwszego przypadku obiekt modelu ( `ITransformer` ) Optymalizacja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="ab43a-210">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="ab43a-211">Ponieważ `ITransformer` obiekt jest bezpieczny wątkowo, obiekt można buforować jako obiekt pojedynczy lub statyczny, aby można było załadować model jeden raz.</span><span class="sxs-lookup"><span data-stu-id="ab43a-211">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="ab43a-212">W przypadku drugiego obiektu obiekt `PredictionEngine` nie jest tak prosty, ponieważ `PredictionEngine` obiekt nie jest bezpieczny wątkowo, dlatego nie można utworzyć wystąpienia tego obiektu jako pojedynczego lub statycznego obiektu w aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab43a-212">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="ab43a-213">Problem z bezpiecznym wątkem i skalowalnością został szczegółowo omówiony w tym [wpisie w blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="ab43a-213">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="ab43a-214">Jednak rzeczy znacznie się różnią od tego, co zostało wyjaśnione w tym wpisie w blogu.</span><span class="sxs-lookup"><span data-stu-id="ab43a-214">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="ab43a-215">Pracujemy nad prostszym podejściem i utworzyłem całkiem **"pakiet integracyjny platformy .NET Core"** , którego można łatwo użyć w ASP.NET Core aplikacjach i usługach, rejestrując go w usłudze Application di Services (usługi wtrysku zależności), a następnie bezpośrednio z poziomu kodu.</span><span class="sxs-lookup"><span data-stu-id="ab43a-215">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="ab43a-216">Zapoznaj się z poniższym samouczkiem i przykładem, aby:</span><span class="sxs-lookup"><span data-stu-id="ab43a-216">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="ab43a-217">Samouczek: uruchamianie modeli ML.NET na skalowalnych aplikacjach internetowych i interfejsach API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ab43a-217">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="ab43a-218">Przykład: skalowalny model ML.NET na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="ab43a-218">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="ab43a-219">Eksplorowanie wygenerowanego kodu w języku C#, który został użyty do uczenia modelu "Najlepsza jakość"</span><span class="sxs-lookup"><span data-stu-id="ab43a-219">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="ab43a-220">Aby uzyskać bardziej zaawansowaną naukę, możesz również poznać wygenerowany kod C#, który był używany przez narzędzie interfejsu wiersza polecenia do uczenia wygenerowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="ab43a-220">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="ab43a-221">Ten kod modelu szkoleniowego jest obecnie generowany w klasie niestandardowej generowanej o nazwie `ModelBuilder` , więc można zbadać ten kod szkoleniowy.</span><span class="sxs-lookup"><span data-stu-id="ab43a-221">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="ab43a-222">Dokładniej, w tym konkretnym scenariuszu (analiza tonacji model) można także porównać ten wygenerowany kod szkoleniowy z kodem opisanym w następującym samouczku:</span><span class="sxs-lookup"><span data-stu-id="ab43a-222">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="ab43a-223">Porównanie: [Samouczek: używanie ml.NET w scenariuszu klasyfikacji binarnej analizy tonacji](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="ab43a-223">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="ab43a-224">Należy porównać wybrane algorytmy i konfigurację potoku w samouczku z kodem wygenerowanym przez narzędzie interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ab43a-224">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="ab43a-225">W zależności od ilości czasu poświęcanego na iterację i wyszukiwanie lepszych modeli wybrany algorytm może być różny wraz z konkretną konfiguracją parametrów i potoku.</span><span class="sxs-lookup"><span data-stu-id="ab43a-225">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="ab43a-226">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ab43a-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ab43a-227">Przygotuj dane dla wybranego zadania ML (problem do rozwiązania)</span><span class="sxs-lookup"><span data-stu-id="ab43a-227">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="ab43a-228">Uruchom polecenie "mlnet klasyfikacyjn" w narzędziu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ab43a-228">Run the 'mlnet classification' command in the CLI tool</span></span>
> - <span data-ttu-id="ab43a-229">Przejrzyj wyniki metryki jakości</span><span class="sxs-lookup"><span data-stu-id="ab43a-229">Review the quality metric results</span></span>
> - <span data-ttu-id="ab43a-230">Opis wygenerowanego kodu C# w celu uruchomienia modelu (kod do użycia w aplikacji użytkownika końcowego)</span><span class="sxs-lookup"><span data-stu-id="ab43a-230">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="ab43a-231">Eksplorowanie wygenerowanego kodu w języku C#, który został użyty do uczenia modelu "Najlepsza jakość" (cele zdobywania)</span><span class="sxs-lookup"><span data-stu-id="ab43a-231">Explore the generated C# code that was used to train the "best quality" model (earning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="ab43a-232">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab43a-232">See also</span></span>

- [<span data-ttu-id="ab43a-233">Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="ab43a-233">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="ab43a-234">Samouczek: uruchamianie modeli ML.NET na skalowalnych aplikacjach internetowych i interfejsach API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ab43a-234">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="ab43a-235">Przykład: skalowalny model ML.NET na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="ab43a-235">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="ab43a-236">Przewodnik dotyczący poleceń autouczenia interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="ab43a-236">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="ab43a-237">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="ab43a-237">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
