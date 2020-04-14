---
title: Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET
description: Automatyczne generowanie modelu ml i powiązanego kodu C# z przykładowego zestawu danych
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 832124e6d027b240c4d06692ee87c84f57b982d3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243339"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="b44f9-103">Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="b44f9-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="b44f9-104">Dowiedz się, jak używać ML.NET interfejsu wiersza polecenia do automatycznego generowania ML.NET modelu i podstawowego kodu języka C#.</span><span class="sxs-lookup"><span data-stu-id="b44f9-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="b44f9-105">Należy podać zestaw danych i zadanie uczenia maszynowego, które chcesz zaimplementować, a cli używa aparatu AutoML do tworzenia generowania modelu i wdrażania kodu źródłowego, a także modelu binarnego.</span><span class="sxs-lookup"><span data-stu-id="b44f9-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="b44f9-106">W tym samouczku wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b44f9-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b44f9-107">Przygotowywanie danych do wybranego zadania uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="b44f9-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="b44f9-108">Uruchom polecenie 'mlnet auto-train' z interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b44f9-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> - <span data-ttu-id="b44f9-109">Przejrzyj wyniki metryki jakości</span><span class="sxs-lookup"><span data-stu-id="b44f9-109">Review the quality metric results</span></span>
> - <span data-ttu-id="b44f9-110">Zrozumienie wygenerowanego kodu języka C# w celu użycia modelu w aplikacji</span><span class="sxs-lookup"><span data-stu-id="b44f9-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="b44f9-111">Eksploruj wygenerowany kod języka C#, który został użyty do przeszkolenia modelu</span><span class="sxs-lookup"><span data-stu-id="b44f9-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="b44f9-112">Ten temat odnosi się do narzędzia ML.NET interfejsu wiersza polecenia, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="b44f9-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b44f9-113">Aby uzyskać więcej informacji, odwiedź stronę [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="b44f9-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="b44f9-114">ML.NET interfejsu wiersza polecenia jest częścią ML.NET a jego głównym celem jest "demokratyzacja" ML.NET dla programistów platformy .NET podczas uczenia się ML.NET, więc nie trzeba kodować od podstaw, aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="b44f9-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="b44f9-115">Interfejs wiersza polecenia ML.NET można uruchomić w dowolnym wierszu polecenia (Windows, Mac lub Linux), aby wygenerować dobrej jakości modele ML.NET i kod źródłowy na podstawie podanych zestawów danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="b44f9-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b44f9-116">Pre-requisites</span></span>

- <span data-ttu-id="b44f9-117">[Net Core 2.2 SDK lub nowszy](https://dotnet.microsoft.com/download/dotnet-core/2.2)</span><span class="sxs-lookup"><span data-stu-id="b44f9-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="b44f9-118">(Opcjonalnie) [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="b44f9-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="b44f9-119">Interfejs wiersza polecenia struktury ML.NET</span><span class="sxs-lookup"><span data-stu-id="b44f9-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="b44f9-120">Można uruchomić wygenerowane projekty kodu Języka C# `dotnet run` z programu Visual Studio lub z (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="b44f9-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="b44f9-121">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="b44f9-121">Prepare your data</span></span>

<span data-ttu-id="b44f9-122">Będziemy używać istniejącego zestawu danych używanego w scenariuszu "Analiza tonacji", który jest zadaniem uczenia maszynowego klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="b44f9-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="b44f9-123">Można użyć własnego zestawu danych w podobny sposób, a model i kod zostaną wygenerowane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="b44f9-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="b44f9-124">Pobierz [plik zip zestawu danych UCI Sentiment Labeled Sentences (patrz cytaty w poniższej notatce)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpatruj go w dowolnym folderze.</span><span class="sxs-lookup"><span data-stu-id="b44f9-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b44f9-125">Zestawy danych w tym samouczku używa zestawu danych z "Od grupy do poszczególnych etykiet przy użyciu funkcji głębokich", Kotzias et al.The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="b44f9-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="b44f9-126">KDD 2015 i gościł w repozytorium uczenia maszynowego UCI - Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="b44f9-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="b44f9-127">Repozytorium uczenia maszynowego UCI [ ].http://archive.ics.uci.edu/ml</span><span class="sxs-lookup"><span data-stu-id="b44f9-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="b44f9-128">Irvine, CA: Uniwersytet Kalifornijski, Szkoła Informatyki i Informatyki.</span><span class="sxs-lookup"><span data-stu-id="b44f9-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="b44f9-129">Skopiuj `yelp_labelled.txt` plik do dowolnego folderu, który został wcześniej utworzony `/cli-test`(np.</span><span class="sxs-lookup"><span data-stu-id="b44f9-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="b44f9-130">Otwórz preferowany wiersz polecenia i przejdź do folderu, w którym skopiowano plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="b44f9-131">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b44f9-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="b44f9-132">Za pomocą dowolnego edytora tekstu, takich jak Visual `yelp_labelled.txt` Studio Code, można otworzyć i eksplorować plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="b44f9-133">Widać, że struktura jest:</span><span class="sxs-lookup"><span data-stu-id="b44f9-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="b44f9-134">Plik nie ma nagłówka.</span><span class="sxs-lookup"><span data-stu-id="b44f9-134">The file has no header.</span></span> <span data-ttu-id="b44f9-135">Użyjesz indeksu kolumny.</span><span class="sxs-lookup"><span data-stu-id="b44f9-135">You will use the column's index.</span></span>

    - <span data-ttu-id="b44f9-136">Istnieją tylko dwie kolumny:</span><span class="sxs-lookup"><span data-stu-id="b44f9-136">There are just two columns:</span></span>

        | <span data-ttu-id="b44f9-137">Tekst (indeks kolumny 0)</span><span class="sxs-lookup"><span data-stu-id="b44f9-137">Text (Column index 0)</span></span> | <span data-ttu-id="b44f9-138">Etykieta (indeks kolumny 1)</span><span class="sxs-lookup"><span data-stu-id="b44f9-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="b44f9-139">Wow... Bardzo dobre miejsce na życie.</span><span class="sxs-lookup"><span data-stu-id="b44f9-139">Wow... Loved this place.</span></span> | <span data-ttu-id="b44f9-140">1</span><span class="sxs-lookup"><span data-stu-id="b44f9-140">1</span></span> |
        | <span data-ttu-id="b44f9-141">Skorupa nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="b44f9-141">Crust is not good.</span></span> | <span data-ttu-id="b44f9-142">0</span><span class="sxs-lookup"><span data-stu-id="b44f9-142">0</span></span> |
        | <span data-ttu-id="b44f9-143">Nie smaczne i tekstury był po prostu paskudny.</span><span class="sxs-lookup"><span data-stu-id="b44f9-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="b44f9-144">0</span><span class="sxs-lookup"><span data-stu-id="b44f9-144">0</span></span> |
        | <span data-ttu-id="b44f9-145">... WIELE WIĘCEJ WIERSZY TEKSTU...</span><span class="sxs-lookup"><span data-stu-id="b44f9-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="b44f9-146">... (1 lub 0)...</span><span class="sxs-lookup"><span data-stu-id="b44f9-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="b44f9-147">Upewnij się, że plik zestawu danych został zamknięty z edytora.</span><span class="sxs-lookup"><span data-stu-id="b44f9-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="b44f9-148">Teraz można przystąpić do rozpoczęcia korzystania z interfejsu wiersza polecenia dla tego scenariusza "Analiza tonacji".</span><span class="sxs-lookup"><span data-stu-id="b44f9-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b44f9-149">Po zakończeniu tego samouczka można również spróbować z własnych zestawów danych, tak długo, jak są one gotowe do użycia dla każdego z zadań ML obecnie obsługiwane przez ML.NET podglądu interfejsu wiersza polecenia, które są *"Klasyfikacja binarna", "Klasyfikacja wieloklasowa" i "Regresja").*</span><span class="sxs-lookup"><span data-stu-id="b44f9-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="b44f9-150">Uruchom polecenie 'mlnet auto-train'</span><span class="sxs-lookup"><span data-stu-id="b44f9-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="b44f9-151">Uruchom następujące polecenie ML.NET interfejsu wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="b44f9-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="b44f9-152">To polecenie uruchamia \*\* `mlnet auto-train` polecenie:\*\*</span><span class="sxs-lookup"><span data-stu-id="b44f9-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="b44f9-153">dla **zadania typu ML\*\*\*\*`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="b44f9-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="b44f9-154">używa **pliku zestawu `yelp_labelled.txt` danych** jako zestawu danych szkoleniowych i testowych (wewnętrznie cli użyje weryfikacji krzyżowej lub podzieli go na dwa zestawy danych, jeden do szkolenia i jeden do testowania)</span><span class="sxs-lookup"><span data-stu-id="b44f9-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="b44f9-155">gdzie **kolumna celu/docelowa,** którą chcesz przewidzieć (powszechnie nazywana **"etykietą"**) jest **kolumną z indeksem 1** (czyli drugą kolumną, ponieważ indeks jest oparty na wartości zero)</span><span class="sxs-lookup"><span data-stu-id="b44f9-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="b44f9-156">**nie używa nagłówka pliku** z nazwami kolumn, ponieważ ten konkretny plik zestawu danych nie ma nagłówka</span><span class="sxs-lookup"><span data-stu-id="b44f9-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="b44f9-157">**docelowy czas eksploracji** eksperymentu wynosi **10 sekund**</span><span class="sxs-lookup"><span data-stu-id="b44f9-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="b44f9-158">Zobaczysz dane wyjściowe z interfejsu wiersza polecenia, podobne do:</span><span class="sxs-lookup"><span data-stu-id="b44f9-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[<span data-ttu-id="b44f9-159">Windows</span><span class="sxs-lookup"><span data-stu-id="b44f9-159">Windows</span></span>](#tab/windows)

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[<span data-ttu-id="b44f9-161">MacOS Bash (macOS Bash)</span><span class="sxs-lookup"><span data-stu-id="b44f9-161">macOS Bash</span></span>](#tab/macosbash)

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="b44f9-163">W tym konkretnym przypadku, w ciągu zaledwie 10 sekund i z małym zestawem danych, narzędzie CLI było w stanie uruchomić sporo iteracji, co oznacza szkolenie wiele razy w oparciu o różne kombinacje algorytmów / konfiguracji z różnymi wewnętrznymi przekształceniami danych i hiperwymiętami algorytmu.</span><span class="sxs-lookup"><span data-stu-id="b44f9-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="b44f9-164">Wreszcie, "najlepszej jakości" model znaleziony w 10 sekund jest model przy użyciu konkretnego trenera / algorytm z dowolnej konkretnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b44f9-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="b44f9-165">W zależności od czasu eksploracji polecenie może uzyskać inny wynik.</span><span class="sxs-lookup"><span data-stu-id="b44f9-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="b44f9-166">Zaznaczenie jest oparte na wielu pokazanych `Accuracy`metrykach, takich jak .</span><span class="sxs-lookup"><span data-stu-id="b44f9-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="b44f9-167">**Opis wskaźników jakości modelu**</span><span class="sxs-lookup"><span data-stu-id="b44f9-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="b44f9-168">Pierwszą i najłatwiejszą metryką do oceny modelu klasyfikacji binarnej jest dokładność, która jest prosta do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="b44f9-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="b44f9-169">"Dokładność jest proporcją prawidłowych prognoz z zestawem danych testowych.".</span><span class="sxs-lookup"><span data-stu-id="b44f9-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="b44f9-170">Im bliżej 100% (1,00), tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="b44f9-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="b44f9-171">Jednak zdążyń, w których tylko pomiar z metryki dokładność nie wystarczy, zwłaszcza gdy etykieta (0 i 1 w tym przypadku) jest niezrównoważony w zestawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="b44f9-172">Aby uzyskać dodatkowe metryki i bardziej **szczegółowe informacje na temat metryk,** takich jak dokładność, AUC, AUCPR i F1-score używane do oceny różnych modeli, zobacz Opis [metryk ML.NET](../resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="b44f9-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b44f9-173">Możesz wypróbować ten sam zestaw danych i `--max-exploration-time` określić kilka minut dla (na przykład trzy minuty, aby określić 180 sekund), który znajdzie lepszy "najlepszy model" dla Ciebie z inną konfiguracją potoku szkoleniowego dla tego zestawu danych (który jest dość mały, 1000 wierszy).</span><span class="sxs-lookup"><span data-stu-id="b44f9-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="b44f9-174">Aby znaleźć model "najlepszej/dobrej jakości", który jest "modelem gotowym do produkcji" skierowanym na większe zestawy danych, należy wykonać eksperymenty z wierszem polecenia, zwykle określając znacznie więcej czasu eksploracji w zależności od rozmiaru zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="b44f9-175">W rzeczywistości w wielu przypadkach może wymagać wielu godzin czasu eksploracji, zwłaszcza jeśli zestaw danych jest duży w wierszach i kolumnach.</span><span class="sxs-lookup"><span data-stu-id="b44f9-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="b44f9-176">Poprzednie wykonanie polecenia wygenerowało następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="b44f9-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="b44f9-177">Serializowany model .zip ("najlepszy model") gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="b44f9-177">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="b44f9-178">Kod C# do uruchamiania/oceniania, który wygenerował model (Aby prognozować w aplikacjach użytkownika końcowego z tym modelem).</span><span class="sxs-lookup"><span data-stu-id="b44f9-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="b44f9-179">Kod szkoleniowy języka C# używany do generowania tego modelu (cele uczenia się).</span><span class="sxs-lookup"><span data-stu-id="b44f9-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="b44f9-180">Plik dziennika ze wszystkimi iteracjami zbadane o określonych szczegółowych informacji o każdym algorytm wypróbowany z jego kombinacji hiper-parametrów i przekształceń danych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="b44f9-181">Pierwsze dwa aktywa (. Model pliku ZIP i kod C#, aby uruchomić ten model) mogą być bezpośrednio używane w aplikacjach użytkownika końcowego (ASP.NET core aplikacji sieci web, usług, aplikacji klasycznej itp.), aby prognozowania z tego modelu uczenia maszynowego generowane.</span><span class="sxs-lookup"><span data-stu-id="b44f9-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="b44f9-182">Trzeci zasób, kod szkolenia, pokazuje, co ML.NET kod interfejsu API został użyty przez interfejs wiersza polecenia do szkolenia wygenerowanego modelu, dzięki czemu można zbadać, jakie konkretne trenera/algorytmu i hiper-parametrów zostały wybrane przez interfejs wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b44f9-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="b44f9-183">Te wyliczone zasoby są wyjaśnione w poniższych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="b44f9-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="b44f9-184">Eksploruj wygenerowany kod języka C#, który ma być używany do uruchamiania modelu w celu tworzenia prognoz</span><span class="sxs-lookup"><span data-stu-id="b44f9-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="b44f9-185">W programie Visual Studio (2017 lub 2019) `SampleBinaryClassification` otwórz rozwiązanie wygenerowane w folderze `/cli-test`o nazwie w oryginalnym folderze docelowym (w samouczku został nazwany ).</span><span class="sxs-lookup"><span data-stu-id="b44f9-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="b44f9-186">Powinien zostać wyświetlony rozwiązanie podobne do:</span><span class="sxs-lookup"><span data-stu-id="b44f9-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="b44f9-187">W samouczku sugerujemy użycie programu Visual Studio, ale można również eksplorować wygenerowany kod C# (dwa projekty) za pomocą dowolnego edytora tekstu i uruchomić wygenerowaną aplikację konsoli `dotnet CLI` na komputerze macOS, Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="b44f9-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Rozwiązanie VS generowane przez interfejs wiersza polecenia](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="b44f9-189">Wygenerowana **biblioteka klas** zawierająca serializowany model ML (plik zip) i klasy danych (modele danych) jest czymś, czego można bezpośrednio używać w aplikacji użytkownika końcowego, nawet bezpośrednio odwołując się do tej biblioteki klas (lub przenosząc kod, jak wolisz).</span><span class="sxs-lookup"><span data-stu-id="b44f9-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="b44f9-190">Wygenerowana **aplikacja konsoli** zawiera kod wykonania, który należy przejrzeć, a następnie zwykle ponownie użyć "kod oceniania" (kod, który uruchamia model ML, aby przewidywanie) przez przeniesienie tego prostego kodu (tylko kilka wierszy) do aplikacji użytkownika końcowego, gdzie chcesz dokonać prognoz.</span><span class="sxs-lookup"><span data-stu-id="b44f9-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="b44f9-191">Otwórz **pliki ModelInput.cs** i **ModelOutput.cs** klas w projekcie biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="b44f9-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="b44f9-192">Zobaczysz, że te klasy są "klasy danych" lub POCO używane do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="b44f9-193">Jest to "kod standardowy", ale przydatne, aby go wygenerowane, jeśli zestaw danych ma dziesiątki lub nawet setki kolumn.</span><span class="sxs-lookup"><span data-stu-id="b44f9-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="b44f9-194">Klasa `ModelInput` jest używana podczas odczytywania danych z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-194">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="b44f9-195">Klasa `ModelOutput` jest używana do uzyskania wyniku prognozowania (dane przewidywania).</span><span class="sxs-lookup"><span data-stu-id="b44f9-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="b44f9-196">Otwórz plik Program.cs i eksploruj kod.</span><span class="sxs-lookup"><span data-stu-id="b44f9-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="b44f9-197">W zaledwie kilku wierszach można uruchomić model i dokonać prognozowania próbki.</span><span class="sxs-lookup"><span data-stu-id="b44f9-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

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

    - <span data-ttu-id="b44f9-198">Pierwszy wiersz kodu po `MLContext` prostu tworzy obiekt potrzebny przy każdym uruchomieniu kodu ML.NET.</span><span class="sxs-lookup"><span data-stu-id="b44f9-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span>

    - <span data-ttu-id="b44f9-199">Drugi wiersz kodu jest komentowany, ponieważ nie trzeba trenować modelu, ponieważ został już przeszkolony dla Ciebie przez narzędzie CLI i zapisane w modelu serializowane . zip.</span><span class="sxs-lookup"><span data-stu-id="b44f9-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="b44f9-200">Ale jeśli chcesz zobaczyć *"jak model został przeszkolony"* przez interfejsu wiersza polecenia, można odkomentować tej linii i uruchomić/debug kod szkolenia używany dla danego modelu ml.</span><span class="sxs-lookup"><span data-stu-id="b44f9-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

    - <span data-ttu-id="b44f9-201">W trzecim wierszu kodu należy załadować model z modelem serializowanym . zip z `mlContext.Model.Load()` interfejsem API, udostępniając ścieżkę do tego modelu . zip.</span><span class="sxs-lookup"><span data-stu-id="b44f9-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

    - <span data-ttu-id="b44f9-202">W czwartym wierszu kodu można `PredictionEngine` załadować `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` utworzyć obiekt z interfejsem API.</span><span class="sxs-lookup"><span data-stu-id="b44f9-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="b44f9-203">Obiekt jest `PredictionEngine` potrzebny za każdym razem, gdy chcesz dokonać prognozowania kierowanego na pojedynczą próbkę danych (W tym przypadku pojedynczy fragment tekstu do przewidzenia jego tonacji).</span><span class="sxs-lookup"><span data-stu-id="b44f9-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

    - <span data-ttu-id="b44f9-204">Piąty wiersz kodu jest, gdzie można utworzyć, że *pojedyncze przykładowe dane,* które mają być używane do przewidywania przez wywołanie funkcji `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="b44f9-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="b44f9-205">Ponieważ narzędzie cli nie wie, jakiego rodzaju przykładowych danych do użycia, w ramach tej funkcji jest ładowanie pierwszego wiersza zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="b44f9-206">Jednak w tym przypadku można również utworzyć własne "zakodowane" dane zamiast `CreateSingleDataSample()` bieżącej implementacji funkcji, aktualizując ten prostszy kod implementując tę funkcję:</span><span class="sxs-lookup"><span data-stu-id="b44f9-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. <span data-ttu-id="b44f9-207">Uruchom projekt przy użyciu oryginalnych przykładowych danych załadowanych z pierwszego wiersza zestawu danych lub przez podanie własnych niestandardowych danych przykładowych zakodowanych na własne zamówienie.</span><span class="sxs-lookup"><span data-stu-id="b44f9-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="b44f9-208">Powinieneś uzyskać prognozę porównywalną do:</span><span class="sxs-lookup"><span data-stu-id="b44f9-208">You should get a prediction comparable to:</span></span>

    # <a name="windows"></a>[<span data-ttu-id="b44f9-209">Windows</span><span class="sxs-lookup"><span data-stu-id="b44f9-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="b44f9-210">Uruchom aplikację konsoli z programu Visual Studio, naciskając klawisz F5 (przycisk Odtwórz):</span><span class="sxs-lookup"><span data-stu-id="b44f9-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="b44f9-212">)</span><span class="sxs-lookup"><span data-stu-id="b44f9-212">)</span></span>

    # <a name="macos-bash"></a>[<span data-ttu-id="b44f9-213">MacOS Bash (macOS Bash)</span><span class="sxs-lookup"><span data-stu-id="b44f9-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="b44f9-214">Uruchom aplikację konsoli z wiersza polecenia, wpisując następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="b44f9-214">Run the console app from the command-prompt by typing the following commands:</span></span>

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="b44f9-216">)</span><span class="sxs-lookup"><span data-stu-id="b44f9-216">)</span></span>

    ---

1. <span data-ttu-id="b44f9-217">Spróbuj zmienić zakodowane dane przykładowe na inne zdania o różnych tonacji i zobacz, jak model przewiduje pozytywne lub negatywne nastroje.</span><span class="sxs-lookup"><span data-stu-id="b44f9-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="b44f9-218">Napełnij aplikacje użytkowników końcowych prognozami modelu ML</span><span class="sxs-lookup"><span data-stu-id="b44f9-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="b44f9-219">Można użyć podobnego "kod oceniania modelu ML", aby uruchomić model w aplikacji użytkownika końcowego i dokonać prognoz.</span><span class="sxs-lookup"><span data-stu-id="b44f9-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="b44f9-220">Na przykład można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznej systemu Windows, takich jak **WPF** I **WinForms** i uruchomić model w taki sam sposób, jak to zostało zrobione w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="b44f9-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="b44f9-221">Jednak sposób zaimplementowania tych wierszy kodu do uruchomienia modelu ml powinny być zoptymalizowane (czyli pamięci podręcznej pliku .zip modelu i załadować go raz) i mają singleton obiektów zamiast tworzenia ich na każde żądanie, zwłaszcza jeśli aplikacja musi być skalowalne, takie jak aplikacja sieci web lub usługi rozproszonej, jak wyjaśniono w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b44f9-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="b44f9-222">Uruchamianie modeli ML.NET w skalowalnych ASP.NET core aplikacji i usług internetowych (aplikacje wielowątkowe)</span><span class="sxs-lookup"><span data-stu-id="b44f9-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="b44f9-223">Tworzenie obiektu modelu (załadowany`ITransformer` z pliku zip modelu) `PredictionEngine` i obiekt powinien być zoptymalizowany szczególnie podczas uruchamiania w skalowalnych aplikacji sieci web i usług rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="b44f9-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="b44f9-224">W pierwszym przypadku obiekt modelu`ITransformer`( ) optymalizacja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="b44f9-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="b44f9-225">Ponieważ `ITransformer` obiekt jest bezpieczny dla wątków, można buforować obiekt jako obiekt singleton lub statyczny, dzięki czemu można załadować model raz.</span><span class="sxs-lookup"><span data-stu-id="b44f9-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="b44f9-226">Dla drugiego `PredictionEngine` obiektu, obiektu nie jest tak `PredictionEngine` łatwe, ponieważ obiekt nie jest bezpieczny dla wątków, w związku z tym nie można utworzyć wystąpienia tego obiektu jako obiektu singleton lub statycznego w aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b44f9-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="b44f9-227">Ten problem bezpieczny dla wątków i skalowalności jest głęboko omówiony w tym [blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="b44f9-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="b44f9-228">Jednak rzeczy zrobiły ci o wiele łatwiej niż to, co zostało wyjaśnione w tym poście na blogu.</span><span class="sxs-lookup"><span data-stu-id="b44f9-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="b44f9-229">Pracowaliśmy nad prostszym podejściem dla Ciebie i stworzyliśmy ładny **pakiet integracji ".NET Core Integration Package",** którego można łatwo używać w swoich ASP.NET podstawowych aplikacji i usług, rejestrując je w usługach DI aplikacji (usługi iniekcji zależności), a następnie bezpośrednio z kodu.</span><span class="sxs-lookup"><span data-stu-id="b44f9-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="b44f9-230">Sprawdź następujący samouczek i przykład, aby to zrobić:</span><span class="sxs-lookup"><span data-stu-id="b44f9-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="b44f9-231">Samouczek: Uruchamianie modeli ML.NET skalowalnych aplikacji internetowych ASP.NET Core i webapi</span><span class="sxs-lookup"><span data-stu-id="b44f9-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="b44f9-232">Przykład: Skalowalny model ML.NET w ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="b44f9-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="b44f9-233">Zapoznaj się z wygenerowanym kodem języka C#, który został użyty do szkolenia modelu "najlepszej jakości"</span><span class="sxs-lookup"><span data-stu-id="b44f9-233">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="b44f9-234">Aby uzyskać bardziej zaawansowane cele uczenia się, można również eksplorować wygenerowany kod Języka C#, który został użyty przez narzędzie interfejsu wiersza polecenia do uczenia wygenerowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="b44f9-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="b44f9-235">Ten "kod modelu szkolenia" jest obecnie generowany `ModelBuilder` w klasie niestandardowej o nazwie, dzięki czemu można zbadać ten kod szkolenia.</span><span class="sxs-lookup"><span data-stu-id="b44f9-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="b44f9-236">Co ważniejsze, w tym konkretnym scenariuszu (model analizy tonacji) można również porównać wygenerowany kod szkolenia z kodem wyjaśnionym w poniższym samouczku:</span><span class="sxs-lookup"><span data-stu-id="b44f9-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="b44f9-237">Porównaj: [Samouczek: Użyj ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="b44f9-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="b44f9-238">Interesujące jest porównanie wybranego algorytmu i konfiguracji potoku w samouczku z kodem wygenerowanym przez narzędzie CLI.</span><span class="sxs-lookup"><span data-stu-id="b44f9-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="b44f9-239">W zależności od tego, ile czasu spędzasz iteracji i poszukiwania lepszych modeli, wybrany algorytm może być różny wraz z jego poszczególnych hiper-parametrów i konfiguracji potoku.</span><span class="sxs-lookup"><span data-stu-id="b44f9-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="b44f9-240">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b44f9-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b44f9-241">Przygotowanie danych do wybranego zadania uczenia maszynowego (problem do rozwiązania)</span><span class="sxs-lookup"><span data-stu-id="b44f9-241">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="b44f9-242">Uruchom polecenie 'mlnet auto-train' w narzędziu CLI</span><span class="sxs-lookup"><span data-stu-id="b44f9-242">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> - <span data-ttu-id="b44f9-243">Przejrzyj wyniki metryki jakości</span><span class="sxs-lookup"><span data-stu-id="b44f9-243">Review the quality metric results</span></span>
> - <span data-ttu-id="b44f9-244">Zrozumieć wygenerowany kod języka C#, aby uruchomić model (Kod do użycia w aplikacji użytkownika końcowego)</span><span class="sxs-lookup"><span data-stu-id="b44f9-244">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="b44f9-245">Poznaj wygenerowany kod C#, który został użyty do uczenia modelu "najlepszej jakości" (cele szkoleniowe)</span><span class="sxs-lookup"><span data-stu-id="b44f9-245">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="b44f9-246">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b44f9-246">See also</span></span>

- [<span data-ttu-id="b44f9-247">Automatyzacja treningu modelu za pomocą ML.NET interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b44f9-247">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="b44f9-248">Samouczek: Uruchamianie modeli ML.NET skalowalnych aplikacji internetowych ASP.NET Core i webapi</span><span class="sxs-lookup"><span data-stu-id="b44f9-248">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="b44f9-249">Przykład: Skalowalny model ML.NET w ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="b44f9-249">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="b44f9-250">ML.NET przewodnik po poleceniach automatycznego pociągu CLI</span><span class="sxs-lookup"><span data-stu-id="b44f9-250">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="b44f9-251">Telemetria w ML.NET interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b44f9-251">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
