---
title: Automatycznie Generuj klasyfikator binarny przy użyciu interfejsu wiersza polecenia ML.NET
description: Automatycznie Generuj model ML i powiązany C# kod z przykładowego zestawu danych
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: c0e188286821f0e3822fde4af74a1561edfbb868
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107273"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a><span data-ttu-id="22003-103">Automatycznie Generuj klasyfikator binarny przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="22003-103">Auto generate a binary classifier using the CLI</span></span>

<span data-ttu-id="22003-104">Dowiedz się, jak używać interfejsu wiersza polecenia ML.NET, aby automatycznie generować C# model ml.NET i kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="22003-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="22003-105">Podajesz zestaw danych i zadanie uczenia maszynowego, które chcesz zaimplementować, a interfejs wiersza polecenia używa aparatu AutoML do tworzenia kodu źródłowego generacji i wdrożenia modelu, a także modelu binarnego.</span><span class="sxs-lookup"><span data-stu-id="22003-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="22003-106">W tym samouczku wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="22003-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="22003-107">Przygotuj dane dla wybranego zadania uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="22003-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="22003-108">Uruchom polecenie "mlnet autouczenie" w interfejsie wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="22003-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> - <span data-ttu-id="22003-109">Przejrzyj wyniki metryki jakości</span><span class="sxs-lookup"><span data-stu-id="22003-109">Review the quality metric results</span></span>
> - <span data-ttu-id="22003-110">Poznaj wygenerowany C# kod, aby użyć modelu w aplikacji</span><span class="sxs-lookup"><span data-stu-id="22003-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="22003-111">Eksploruj wygenerowany C# kod, który został użyty do uczenia modelu</span><span class="sxs-lookup"><span data-stu-id="22003-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="22003-112">Ten temat odnosi się do narzędzia interfejsu wiersza polecenia ML.NET, które jest obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="22003-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="22003-113">Aby uzyskać więcej informacji, zapoznaj [się z wprowadzeniem do ml.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="22003-113">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="22003-114">Interfejs wiersza polecenia ML.NET jest częścią ML.NET i jej głównym celem jest "zdemokratyzuj proces" ML.NET dla deweloperów platformy .NET, gdy uczysz się, że nie musisz uruchamiać kodu od podstaw, aby rozpocząć pracę.</span><span class="sxs-lookup"><span data-stu-id="22003-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="22003-115">Interfejs wiersza polecenia ML.NET można uruchomić we wszystkich wierszach poleceń (Windows, Mac lub Linux) w celu wygenerowania dobrej jakości modeli ML.NET i kodu źródłowego na podstawie podanych szkoleń.</span><span class="sxs-lookup"><span data-stu-id="22003-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="22003-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="22003-116">Pre-requisites</span></span>

- <span data-ttu-id="22003-117">[.NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="22003-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="22003-118">Obowiązkowe [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="22003-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="22003-119">INTERFEJS WIERSZA POLECENIA ML.NET</span><span class="sxs-lookup"><span data-stu-id="22003-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="22003-120">Można uruchomić wygenerowane C# projekty kodu z programu Visual Studio lub z `dotnet run` (interfejs wiersza polecenia platformy .NET Core).</span><span class="sxs-lookup"><span data-stu-id="22003-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="22003-121">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="22003-121">Prepare your data</span></span>

<span data-ttu-id="22003-122">Zamierzamy użyć istniejącego zestawu danych, który będzie używany dla scenariusza "analiza tonacji", czyli binarnego zadania uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="22003-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="22003-123">Możesz użyć własnego zestawu danych w podobny sposób, a model i kod zostanie wygenerowany dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="22003-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="22003-124">Pobierz [tonacji z oznaczeniem "UCI" (zobacz Cytaty w poniższej notatce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj go do wybranego folderu.</span><span class="sxs-lookup"><span data-stu-id="22003-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="22003-125">Zestawy danych, w tym samouczku, korzystają z zestawu DataSet z grupy "from" do poszczególnych etykiet przy użyciu funkcji głębokiej, Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="22003-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="22003-126">KDD 2015 i hostowana w repozytorium Machine Learning/Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="22003-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="22003-127">/Na Machine Learning repozytorium http://archive.ics.uci.edu/ml [].</span><span class="sxs-lookup"><span data-stu-id="22003-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="22003-128">Irvine, CA: University of Kalifornii, szkolna informacja i nauka komputerowe.</span><span class="sxs-lookup"><span data-stu-id="22003-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="22003-129">Skopiuj plik do folderu, który został wcześniej utworzony (na przykład `/cli-test`). `yelp_labelled.txt`</span><span class="sxs-lookup"><span data-stu-id="22003-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="22003-130">Otwórz preferowany wiersz polecenia i przejdź do folderu, do którego skopiowano plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="22003-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="22003-131">Przykład:</span><span class="sxs-lookup"><span data-stu-id="22003-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="22003-132">Za pomocą dowolnego edytora tekstu, takiego jak Visual Studio Code, można otworzyć i eksplorować `yelp_labelled.txt` plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="22003-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="22003-133">Można zobaczyć, że struktura jest:</span><span class="sxs-lookup"><span data-stu-id="22003-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="22003-134">Plik nie ma nagłówka.</span><span class="sxs-lookup"><span data-stu-id="22003-134">The file has no header.</span></span> <span data-ttu-id="22003-135">Będziesz używać indeksu kolumny.</span><span class="sxs-lookup"><span data-stu-id="22003-135">You will use the column's index.</span></span>

    - <span data-ttu-id="22003-136">Istnieją tylko dwie kolumny:</span><span class="sxs-lookup"><span data-stu-id="22003-136">There are just two columns:</span></span>

        | <span data-ttu-id="22003-137">Tekst (indeks kolumn 0)</span><span class="sxs-lookup"><span data-stu-id="22003-137">Text (Column index 0)</span></span> | <span data-ttu-id="22003-138">Etykieta (indeks kolumn 1)</span><span class="sxs-lookup"><span data-stu-id="22003-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="22003-139">Wow... Uwielbiane to miejsce.</span><span class="sxs-lookup"><span data-stu-id="22003-139">Wow... Loved this place.</span></span> | <span data-ttu-id="22003-140">1</span><span class="sxs-lookup"><span data-stu-id="22003-140">1</span></span> |
        | <span data-ttu-id="22003-141">Crust nie jest dobry.</span><span class="sxs-lookup"><span data-stu-id="22003-141">Crust is not good.</span></span> | <span data-ttu-id="22003-142">0</span><span class="sxs-lookup"><span data-stu-id="22003-142">0</span></span> |
        | <span data-ttu-id="22003-143">Nie Tasty, a tekstura była paskudnycha.</span><span class="sxs-lookup"><span data-stu-id="22003-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="22003-144">0</span><span class="sxs-lookup"><span data-stu-id="22003-144">0</span></span> |
        | <span data-ttu-id="22003-145">... WIELE WIĘCEJ WIERSZY TEKSTU...</span><span class="sxs-lookup"><span data-stu-id="22003-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="22003-146">... (1 lub 0)...</span><span class="sxs-lookup"><span data-stu-id="22003-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="22003-147">Upewnij się, że plik DataSet został zamknięty z edytora.</span><span class="sxs-lookup"><span data-stu-id="22003-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="22003-148">Teraz możesz zacząć korzystać z interfejsu wiersza polecenia dla tego scenariusza "analiza tonacji".</span><span class="sxs-lookup"><span data-stu-id="22003-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="22003-149">Po zakończeniu tego samouczka możesz również wypróbować własne zestawy danych, o ile są one gotowe do użycia dla dowolnego zadania w ML, które jest obecnie obsługiwane przez ML.NET interfejsu wiersza polecenia, które są *"klasyfikacją binarną", "klasyfikacją wieloklasową" i "regresja"* ).</span><span class="sxs-lookup"><span data-stu-id="22003-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="22003-150">Uruchom polecenie "mlnet autouczenie"</span><span class="sxs-lookup"><span data-stu-id="22003-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="22003-151">Uruchom następujące polecenie interfejsu wiersza polecenia ML.NET:</span><span class="sxs-lookup"><span data-stu-id="22003-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="22003-152">To polecenie uruchamia  **`mlnet auto-train` polecenie**:</span><span class="sxs-lookup"><span data-stu-id="22003-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="22003-153">dla **zadania ml** typu **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="22003-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="22003-154">używa **pliku `yelp_labelled.txt` DataSet** jako zestawu danych szkoleniowych i testowych (wewnętrznie w interfejsie wiersza polecenia będzie można użyć weryfikacji krzyżowej lub podzielić ją na dwa zestawy danych, jeden do szkolenia i jeden do testowania).</span><span class="sxs-lookup"><span data-stu-id="22003-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="22003-155">gdzie **kolumna cel/cel** , która ma zostać przewidywalna (zazwyczaj nazywana **"etykietą"** ) jest **kolumną o indeksie 1** (jest to druga kolumna, ponieważ indeks jest liczony od zera)</span><span class="sxs-lookup"><span data-stu-id="22003-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="22003-156">nie **używa nagłówka pliku** z nazwami kolumn, ponieważ ten określony plik zestawu danych nie ma nagłówka</span><span class="sxs-lookup"><span data-stu-id="22003-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="22003-157">przeznaczony dla eksperymentu **czas poszukiwania** to **10 sekund**</span><span class="sxs-lookup"><span data-stu-id="22003-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="22003-158">Zostaną wyświetlone dane wyjściowe z interfejsu wiersza polecenia, podobne do:</span><span class="sxs-lookup"><span data-stu-id="22003-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="22003-159">Windows</span><span class="sxs-lookup"><span data-stu-id="22003-159">Windows</span></span>](#tab/windows)

    ![Funkcja autouczenia interfejsu wiersza polecenia ML.NET w programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="22003-161">macOS bash</span><span class="sxs-lookup"><span data-stu-id="22003-161">macOS Bash</span></span>](#tab/macosbash)

    ![Funkcja autouczenia interfejsu wiersza polecenia ML.NET w programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="22003-163">W tym konkretnym przypadku, w ciągu zaledwie 10 sekund i z podanym małym zestawem danych, narzędzie interfejsu wiersza polecenia było w stanie uruchomić kilka iteracji, co oznacza szkolenie wiele razy na podstawie różnych kombinacji algorytmów/konfiguracji z różnymi danymi wewnętrznymi przekształcenia i parametry Hyper-Parameters algorytmu.</span><span class="sxs-lookup"><span data-stu-id="22003-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="22003-164">Na koniec model "Najlepsza jakość" znaleziony w ciągu 10 sekund jest modelem używającym określonego Trainer/algorytmu z dowolną określoną konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="22003-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="22003-165">W zależności od czasu eksploracji polecenie może generować inny wynik.</span><span class="sxs-lookup"><span data-stu-id="22003-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="22003-166">Wybór jest oparty na wielu pokazanych metrykach, takich `Accuracy`jak.</span><span class="sxs-lookup"><span data-stu-id="22003-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="22003-167">**Informacje o metrykach jakości modelu**</span><span class="sxs-lookup"><span data-stu-id="22003-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="22003-168">Pierwszą i najłatwiejszą metryką do oszacowania modelu klasyfikacji binarnej jest dokładność, która jest łatwa do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="22003-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="22003-169">"Dokładność to stosunek prawidłowych prognoz z zestawem danych testowych".</span><span class="sxs-lookup"><span data-stu-id="22003-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="22003-170">Im bliżej 100% (1,00), tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="22003-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="22003-171">Istnieją jednak przypadki, w których pomiar dokładności jest niewystarczający, szczególnie wtedy, gdy etykieta (0 i 1 w tym przypadku) jest niezrównoważona w zestawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="22003-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="22003-172">Aby uzyskać dodatkowe metryki i bardziej **szczegółowe informacje na temat metryk** , takich jak dokładność, AUC, AUCPR, F1-Score służące do oceny różnych modeli, można zapoznać się z [tematem informacje o metrykach ml.NET](../resources/metrics.md)</span><span class="sxs-lookup"><span data-stu-id="22003-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    > <span data-ttu-id="22003-173">Możesz wypróbować ten sam zestaw danych i określić kilka minut `--max-exploration-time` (na przykład przez trzy minuty, aby określić 180 sekund), który będzie lepszym najlepszym modelem dla tego zestawu danych. małe, 1000 wiersze).</span><span class="sxs-lookup"><span data-stu-id="22003-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="22003-174">Aby znaleźć model "Najlepsza/dobry", który jest "modelem gotowym do produkcji" przeznaczonym dla większych zestawów danych, należy przeprowadzić eksperymenty z interfejsem wiersza polecenia, zazwyczaj określając znacznie więcej czasu eksplorowania, w zależności od rozmiaru elementu DataSet.</span><span class="sxs-lookup"><span data-stu-id="22003-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="22003-175">W rzeczywistości w wielu przypadkach może być konieczne wielokrotne przeszukiwanie czasu, zwłaszcza jeśli zestaw danych jest duży dla wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="22003-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="22003-176">Poprzednie wykonanie polecenia spowodowało wygenerowanie następujących zasobów:</span><span class="sxs-lookup"><span data-stu-id="22003-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="22003-177">Serializowany model. zip ("najlepszy model") jest gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="22003-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="22003-178">C#kod do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych przy użyciu tego modelu).</span><span class="sxs-lookup"><span data-stu-id="22003-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="22003-179">C#kod szkoleniowy używany do generowania tego modelu (cele uczenia).</span><span class="sxs-lookup"><span data-stu-id="22003-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="22003-180">Plik dziennika ze wszystkimi iteracjami, które zostały zbadane, ze szczegółowymi informacjami na temat każdego z algorytmów, które podjęły kombinację parametrów i przekształceń danych funkcji Hyper-Parameters.</span><span class="sxs-lookup"><span data-stu-id="22003-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="22003-181">Pierwsze dwa elementy zawartości (. Model i C# kod pliku zip służący do uruchamiania tego modelu) mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu przeprowadzenia prognoz dla tego wygenerowanego modelu ml.</span><span class="sxs-lookup"><span data-stu-id="22003-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="22003-182">Trzeci element zawartości, kod szkoleniowy, pokazuje, w jaki sposób kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było sprawdzić, jakie konkretne Trainer/algorytm i parametry funkcji Hyper-Parameters zostały wybrane przez interfejs wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="22003-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="22003-183">Te wyliczane zasoby zostały wyjaśnione w poniższych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="22003-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="22003-184">Eksploruj wygenerowany C# kod, który ma być używany do uruchamiania modelu w celu wykonywania prognoz</span><span class="sxs-lookup"><span data-stu-id="22003-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="22003-185">W programie Visual Studio (2017 lub 2019) Otwórz rozwiązanie wygenerowane w folderze o `SampleBinaryClassification` nazwie w oryginalnym folderze docelowym (w samouczku określono nazwę `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="22003-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="22003-186">Powinno zostać wyświetlone rozwiązanie podobne do:</span><span class="sxs-lookup"><span data-stu-id="22003-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="22003-187">W samouczku zalecamy korzystanie z programu Visual Studio, ale możesz również eksplorować wygenerowany C# kod (dwa projekty) przy użyciu dowolnego edytora tekstów i uruchamiać wygenerowaną aplikację konsolową z `dotnet CLI` maszyną macOS, Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="22003-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Rozwiązanie VS generowane przez interfejs wiersza polecenia](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="22003-189">Wygenerowana **Biblioteka klas** zawierająca serializowany model ml (plik zip) i klasy danych (modele danych) to element, którego można bezpośrednio użyć w aplikacji użytkownika końcowego, nawet przez bezpośrednie odwołanie do tej biblioteki klas (lub przeniesienie kodu zgodnie z potrzebami ).</span><span class="sxs-lookup"><span data-stu-id="22003-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="22003-190">Wygenerowana **Aplikacja konsolowa** zawiera kod wykonywania, który należy przejrzeć, a następnie zazwyczaj ponownie użyjemy kodu oceniania (kod, który uruchamia model ml, aby dokonać prognoz), przenosząc ten prosty kod (zaledwie kilka wierszy) do aplikacji użytkownika końcowego, w której chcesz Wykonaj przewidywania.</span><span class="sxs-lookup"><span data-stu-id="22003-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="22003-191">Otwórz pliki klas **ModelInput.cs** i **ModelOutput.cs** w projekcie biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="22003-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="22003-192">Zobaczysz, że te klasy są "klasami danych" lub klasy POCO używane do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="22003-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="22003-193">Jest to "kod standardowy", ale przydatny do wygenerowania, jeśli zestaw danych ma dziesiątki lub nawet setki kolumn.</span><span class="sxs-lookup"><span data-stu-id="22003-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="22003-194">`ModelInput` Klasa jest używana podczas odczytywania danych z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="22003-194">The `ModelInput` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="22003-195">`ModelOutput` Klasa jest używana do uzyskiwania wyniku przewidywania (dane przewidywania).</span><span class="sxs-lookup"><span data-stu-id="22003-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="22003-196">Otwórz plik Program.cs i Eksploruj kod.</span><span class="sxs-lookup"><span data-stu-id="22003-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="22003-197">W zaledwie kilku wierszach można uruchomić model i utworzyć przykładowe przewidywania.</span><span class="sxs-lookup"><span data-stu-id="22003-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it 
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- <span data-ttu-id="22003-198">Pierwszy wiersz kodu po prostu tworzy `MLContext` obiekt wymagany za każdym razem, gdy uruchamiasz kod ml.NET.</span><span class="sxs-lookup"><span data-stu-id="22003-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="22003-199">Drugi wiersz kodu jest oznaczony jako komentarz, ponieważ nie ma potrzeby uczenia modelu, ponieważ został on już przeszkolony przez narzędzie interfejsu wiersza polecenia i zapisany w serializowanym modelu. Plik ZIP.</span><span class="sxs-lookup"><span data-stu-id="22003-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="22003-200">Jeśli jednak chcesz zobaczyć *"jak model został przeszkolony"* za pomocą interfejsu wiersza polecenia, możesz usunąć komentarz tego wiersza i uruchomić/debugować kod szkoleniowy używany dla danego modelu ml.</span><span class="sxs-lookup"><span data-stu-id="22003-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="22003-201">W trzecim wierszu kodu ładujesz model z serializowanego modelu. Plik zip z `mlContext.Model.Load()` interfejsem API przez podanie ścieżki do tego modelu. Plik ZIP.</span><span class="sxs-lookup"><span data-stu-id="22003-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="22003-202">W czwartym wierszu kodu ładowania należy utworzyć `PredictionEngine` obiekt `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` z interfejsem API.</span><span class="sxs-lookup"><span data-stu-id="22003-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="22003-203">Obiekt jest potrzebny `PredictionEngine` w każdym przypadku, gdy chcesz przeanalizować przeznaczenie pojedynczej próbki danych (w tym przypadku pojedynczy fragment tekstu do przewidywania jego tonacji).</span><span class="sxs-lookup"><span data-stu-id="22003-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="22003-204">Piąty wiersz kodu to miejsce, w którym tworzysz *pojedyncze przykładowe dane* , które mają być używane do prognozowania przez wywołanie `CreateSingleDataSample()`funkcji.</span><span class="sxs-lookup"><span data-stu-id="22003-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="22003-205">Ponieważ narzędzie interfejsu wiersza polecenia nie wie jakiego rodzaju przykładowych danych do użycia w ramach tej funkcji, ładuje pierwszy wiersz zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="22003-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="22003-206">Jednak w takim przypadku można także utworzyć własne "kodowane" dane, a nie bieżącą implementację `CreateSingleDataSample()` funkcji, aktualizując ten łatwiejszy kod implementujący tę funkcję:</span><span class="sxs-lookup"><span data-stu-id="22003-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="22003-207">Uruchom projekt, używając oryginalnych danych przykładowych załadowanych z pierwszego wiersza zestawu danych lub dostarczając własne, zakodowane Przykładowo dane.</span><span class="sxs-lookup"><span data-stu-id="22003-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="22003-208">Należy uzyskać prognozę, która jest porównywalna z:</span><span class="sxs-lookup"><span data-stu-id="22003-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="22003-209">Windows</span><span class="sxs-lookup"><span data-stu-id="22003-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="22003-210">Uruchom aplikację konsolową z programu Visual Studio, naciskając klawisz F5 (przycisk odtwarzania):</span><span class="sxs-lookup"><span data-stu-id="22003-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![Funkcja autouczenia interfejsu wiersza polecenia ML.NET w programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="22003-212">)</span><span class="sxs-lookup"><span data-stu-id="22003-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="22003-213">macOS bash</span><span class="sxs-lookup"><span data-stu-id="22003-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="22003-214">Uruchom aplikację konsolową z poziomu wiersza polecenia, wpisując następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="22003-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Funkcja autouczenia interfejsu wiersza polecenia ML.NET w programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="22003-216">)</span><span class="sxs-lookup"><span data-stu-id="22003-216">)</span></span>

    ---

1. <span data-ttu-id="22003-217">Spróbuj zmienić zakodowane przykładowe dane na inne zdania o różnych tonacji i zobaczyć, jak model przewiduje pozytywne lub ujemne tonacji.</span><span class="sxs-lookup"><span data-stu-id="22003-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="22003-218">Dodaj aplikacji użytkowników końcowych przy użyciu prognoz modelu ML</span><span class="sxs-lookup"><span data-stu-id="22003-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="22003-219">Możesz użyć podobnego kodu oceniania modelu "ML", aby uruchomić model w aplikacji użytkownika końcowego i wprowadzić przewidywania.</span><span class="sxs-lookup"><span data-stu-id="22003-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="22003-220">Na przykład można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznej systemu Windows, takiej jak **WPF** i **WinForms** , i uruchomić model w taki sam sposób, jak w przypadku aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="22003-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="22003-221">Jednak sposób implementacji tych wierszy kodu w celu uruchomienia modelu ML powinien zostać zoptymalizowany (to oznacza, że w pamięci podręcznej pliku model. zip jest załadowana) i ma pojedyncze obiekty zamiast tworzyć je na każdym żądaniu, zwłaszcza jeśli aplikacja musi być skalowalna, taka jak Aplikacja sieci Web lub usługa dystrybuowana, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="22003-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="22003-222">Uruchamianie modeli ML.NET w skalowalne ASP.NET Core aplikacje i usługi sieci Web (aplikacje wielowątkowe)</span><span class="sxs-lookup"><span data-stu-id="22003-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="22003-223">Tworzenie obiektu modelu (`ITransformer` załadowane z pliku zip modelu) `PredictionEngine` i obiekt powinien być zoptymalizowany szczególnie w przypadku uruchamiania na skalowalnych aplikacjach internetowych i usługach rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="22003-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="22003-224">Dla pierwszego przypadku obiekt modelu (`ITransformer`) Optymalizacja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="22003-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="22003-225">`ITransformer` Ponieważ obiekt jest bezpieczny wątkowo, obiekt można buforować jako obiekt pojedynczy lub statyczny, aby można było załadować model jeden raz.</span><span class="sxs-lookup"><span data-stu-id="22003-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="22003-226">W przypadku drugiego obiektu `PredictionEngine` obiekt nie jest tak prosty, `PredictionEngine` ponieważ obiekt nie jest bezpieczny wątkowo, dlatego nie można utworzyć wystąpienia tego obiektu jako pojedynczego lub statycznego obiektu w aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="22003-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="22003-227">Problem z bezpiecznym wątkem i skalowalnością został szczegółowo omówiony w tym wpisie w [blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="22003-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="22003-228">Jednak rzeczy znacznie się różnią od tego, co zostało wyjaśnione w tym wpisie w blogu.</span><span class="sxs-lookup"><span data-stu-id="22003-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="22003-229">Pracujemy nad prostszym podejściem i utworzyłem całkiem **"pakiet integracyjny platformy .NET Core"** , którego można łatwo używać w ASP.NET Core aplikacjach i usługach, rejestrując je w aplikacji di Services (usługi wtrysku zależności), a następnie bezpośrednio Użyj go z Twojego kodu.</span><span class="sxs-lookup"><span data-stu-id="22003-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="22003-230">Zapoznaj się z poniższym samouczkiem i przykładem, aby:</span><span class="sxs-lookup"><span data-stu-id="22003-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="22003-231">Samouczek: Uruchamianie modeli ML.NET na skalowalnych aplikacjach sieci Web i internetowych interfejsów API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22003-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="22003-232">Northwind Skalowalny model ML.NET na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="22003-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="22003-233">Eksploruj wygenerowany C# kod, który został użyty do uczenia modelu "Najlepsza jakość"</span><span class="sxs-lookup"><span data-stu-id="22003-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="22003-234">Aby uzyskać bardziej zaawansowane cele uczenia, możesz również poznać wygenerowany C# kod, który był używany przez narzędzie interfejsu wiersza polecenia do uczenia wygenerowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="22003-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="22003-235">Ten kod modelu szkoleniowego jest obecnie generowany w klasie niestandardowej generowanej o nazwie `ModelBuilder` , więc można zbadać ten kod szkoleniowy.</span><span class="sxs-lookup"><span data-stu-id="22003-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="22003-236">Dokładniej, w tym konkretnym scenariuszu (analiza tonacji model) można także porównać ten wygenerowany kod szkoleniowy z kodem opisanym w następującym samouczku:</span><span class="sxs-lookup"><span data-stu-id="22003-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="22003-237">Porównaniu [Samouczek: Użyj ML.NET w scenariuszu](sentiment-analysis.md)klasyfikacji binarnej analizy tonacji.</span><span class="sxs-lookup"><span data-stu-id="22003-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="22003-238">Należy porównać wybrane algorytmy i konfigurację potoku w samouczku z kodem wygenerowanym przez narzędzie interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="22003-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="22003-239">W zależności od ilości czasu poświęcanego na iterację i wyszukiwanie lepszych modeli wybrany algorytm może być różny wraz z konkretną konfiguracją parametrów i potoku.</span><span class="sxs-lookup"><span data-stu-id="22003-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="22003-240">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22003-240">See also</span></span>

- [<span data-ttu-id="22003-241">Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="22003-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="22003-242">Samouczek: Uruchamianie modeli ML.NET na skalowalnych aplikacjach sieci Web i internetowych interfejsów API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22003-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="22003-243">Northwind Skalowalny model ML.NET na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="22003-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="22003-244">Przewodnik dotyczący poleceń autouczenia interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="22003-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="22003-245">Jak zainstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="22003-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="22003-246">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="22003-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="22003-247">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="22003-247">Next steps</span></span>

<span data-ttu-id="22003-248">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="22003-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="22003-249">Przygotuj dane dla wybranego zadania ML (problem do rozwiązania)</span><span class="sxs-lookup"><span data-stu-id="22003-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="22003-250">Uruchom polecenie "mlnet autouczenie" w narzędziu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="22003-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> - <span data-ttu-id="22003-251">Przejrzyj wyniki metryki jakości</span><span class="sxs-lookup"><span data-stu-id="22003-251">Review the quality metric results</span></span>
> - <span data-ttu-id="22003-252">Poznaj wygenerowany C# kod, aby uruchomić model (kod do użycia w aplikacji użytkownika końcowego)</span><span class="sxs-lookup"><span data-stu-id="22003-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="22003-253">Eksploruj wygenerowany C# kod, który został użyty do uczenia modelu "Najlepsza jakość" (cele uczenia)</span><span class="sxs-lookup"><span data-stu-id="22003-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22003-254">Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="22003-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
