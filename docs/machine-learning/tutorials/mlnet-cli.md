---
title: Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia strukturze ML.NET
description: Automatyczne generowanie modelu uczenia Maszynowego i powiązane C# kod z przykładowym zestawie danych
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: feddafdd6becd676f4d18aa94bdfae50f02abc6e
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557955"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a><span data-ttu-id="fac1d-103">Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="fac1d-103">Auto generate a binary classifier using the CLI</span></span>

<span data-ttu-id="fac1d-104">Dowiedz się, jak używać interfejsu wiersza polecenia w strukturze ML.NET do automatycznego generowania na model w strukturze ML.NET i bazowych C# kodu.</span><span class="sxs-lookup"><span data-stu-id="fac1d-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="fac1d-105">Podaj swój zestaw danych i zadanie, które chcesz zaimplementować uczenia maszynowego i interfejsu wiersza polecenia używa aparatu AutoML w celu utworzenia Generowanie modelu i wdrożenie kodu źródłowego, a także modelu binarnego.</span><span class="sxs-lookup"><span data-stu-id="fac1d-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="fac1d-106">W tym samouczku wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fac1d-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="fac1d-107">Przygotowywanie danych dla wybranej maszyny zadania nauki</span><span class="sxs-lookup"><span data-stu-id="fac1d-107">Prepare your data for the selected machine learning task</span></span>
> * <span data-ttu-id="fac1d-108">Uruchom polecenie "mlnet auto-train" z interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="fac1d-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> * <span data-ttu-id="fac1d-109">Przejrzyj wyniki metryk jakości</span><span class="sxs-lookup"><span data-stu-id="fac1d-109">Review the quality metric results</span></span>
> * <span data-ttu-id="fac1d-110">Zrozumienie wygenerowany C# kodu w celu używania tego modelu w aplikacji</span><span class="sxs-lookup"><span data-stu-id="fac1d-110">Understand the generated C# code to use the model in your application</span></span>
> * <span data-ttu-id="fac1d-111">Zapoznaj się z wygenerowanym C# kod, który został użyty do nauczenia modelu</span><span class="sxs-lookup"><span data-stu-id="fac1d-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="fac1d-112">W tym temacie odnosi się do narzędzia interfejsu wiersza polecenia w strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="fac1d-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="fac1d-113">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="fac1d-113">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="fac1d-114">Interfejs wiersza polecenia strukturze ML.NET jest częścią strukturze ML.NET i ich głównym celem jest "zdemokratyzuj proces" strukturze ML.NET dla deweloperów platformy .NET po strukturze ML.NET uczenia, więc nie trzeba kodu od podstaw na rozpoczęcie pracy.</span><span class="sxs-lookup"><span data-stu-id="fac1d-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="fac1d-115">Strukturze ML.NET interfejsu wiersza polecenia można uruchomić na dowolnym wiersza polecenia (Windows, Mac lub Linux) do generowania modeli strukturze ML.NET dobrej jakości i kodu źródłowego, w oparciu o zestawów danych szkoleniowych, których udzielasz.</span><span class="sxs-lookup"><span data-stu-id="fac1d-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="fac1d-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fac1d-116">Pre-requisites</span></span>

- <span data-ttu-id="fac1d-117">[Zestaw SDK programu .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="fac1d-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="fac1d-118">(Opcjonalnie) [Visual Studio 2017 lub 2019 r](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="fac1d-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="fac1d-119">INTERFEJS WIERSZA POLECENIA W STRUKTURZE ML.NET</span><span class="sxs-lookup"><span data-stu-id="fac1d-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="fac1d-120">Aplikację możesz uruchomić wygenerowany C# projekty w programie Visual Studio lub za pomocą kodu `dotnet run` (.NET Core interfejsu wiersza polecenia).</span><span class="sxs-lookup"><span data-stu-id="fac1d-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="fac1d-121">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="fac1d-121">Prepare your data</span></span>

<span data-ttu-id="fac1d-122">Firma Microsoft będzie używany istniejący zestaw danych używany w scenariuszu "Analiza tonacji" jest zadaniem uczenia maszynowego klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="fac1d-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="fac1d-123">Można użyć własnego zestawu danych w podobny sposób i modelu a kod zostanie wygenerowany dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="fac1d-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="fac1d-124">Pobierz [pliku zip zestawu danych na wskaźniki nastrojów klientów etykietą zdań (patrz cytaty poniżej)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i Rozpakuj go w dowolnym folderze, możesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="fac1d-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fac1d-125">Zestawy danych w tym samouczku korzysta z zestawu danych z "From grupy do poszczególnych etykiet korzystanie z funkcji głębokiego" Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="fac1d-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="fac1d-126">KDD 2015 i hostowanej na Machine Learning repozytorium — Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="fac1d-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="fac1d-127">UCI usługi Machine Learning repozytorium [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="fac1d-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="fac1d-128">Irvine, CA: Uniwersytet kalifornijski School informacji i informatyki.</span><span class="sxs-lookup"><span data-stu-id="fac1d-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="fac1d-129">Kopiuj `yelp_labelled.txt` plik do dowolnego folderu utworzonego wcześniej (takie jak `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="fac1d-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="fac1d-130">Otwórz preferowaną wiersza polecenia i przejdź do folderu, do którego skopiowano plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="fac1d-131">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fac1d-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="fac1d-132">Za pomocą dowolnego edytora tekstów, takiego jak Visual Studio Code, możesz otworzyć i Poznaj `yelp_labelled.txt` plik zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="fac1d-133">Możesz zobaczyć, że struktura jest:</span><span class="sxs-lookup"><span data-stu-id="fac1d-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="fac1d-134">Plik nie ma nagłówka.</span><span class="sxs-lookup"><span data-stu-id="fac1d-134">The file has no header.</span></span> <span data-ttu-id="fac1d-135">Będziesz używać indeksu w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="fac1d-135">You will use the column's index.</span></span>

    - <span data-ttu-id="fac1d-136">Dostępne są tylko dwie kolumny:</span><span class="sxs-lookup"><span data-stu-id="fac1d-136">There are just two columns:</span></span>

        | <span data-ttu-id="fac1d-137">Tekst (indeks kolumny 0)</span><span class="sxs-lookup"><span data-stu-id="fac1d-137">Text (Column index 0)</span></span> | <span data-ttu-id="fac1d-138">Etykieta (indeks kolumna 1)</span><span class="sxs-lookup"><span data-stu-id="fac1d-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="fac1d-139">WOW... Pracowałem z tego miejsca.</span><span class="sxs-lookup"><span data-stu-id="fac1d-139">Wow... Loved this place.</span></span> | <span data-ttu-id="fac1d-140">1</span><span class="sxs-lookup"><span data-stu-id="fac1d-140">1</span></span> |
        | <span data-ttu-id="fac1d-141">Skórki nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="fac1d-141">Crust is not good.</span></span> | <span data-ttu-id="fac1d-142">0</span><span class="sxs-lookup"><span data-stu-id="fac1d-142">0</span></span> |
        | <span data-ttu-id="fac1d-143">Nie tasty i po prostu paskudnych tekstury.</span><span class="sxs-lookup"><span data-stu-id="fac1d-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="fac1d-144">0</span><span class="sxs-lookup"><span data-stu-id="fac1d-144">0</span></span> |
        | <span data-ttu-id="fac1d-145">... WIELE WIERSZY TEKSTU WIĘCEJ...</span><span class="sxs-lookup"><span data-stu-id="fac1d-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="fac1d-146">... (1 lub 0)...</span><span class="sxs-lookup"><span data-stu-id="fac1d-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="fac1d-147">Upewnij się, że można zamknąć pliku zestawu danych za pomocą edytora.</span><span class="sxs-lookup"><span data-stu-id="fac1d-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="fac1d-148">Teraz można przystąpić do uruchomienia przy użyciu interfejsu wiersza polecenia w tym scenariuszu "Analiza tonacji".</span><span class="sxs-lookup"><span data-stu-id="fac1d-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fac1d-149">Po zakończeniu tego samouczka możesz także spróbować z własne zestawy danych tak długo, jak są one gotowe do użycia dla każdego zadania uczenia Maszynowego aktualnie obsługiwana w strukturze ML.NET interfejsu wiersza polecenia w wersji zapoznawczej, które są *"Klasyfikacji binarnej", "Wieloklasowej klasyfikacji" i " Regresja "*).</span><span class="sxs-lookup"><span data-stu-id="fac1d-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="fac1d-150">Uruchom polecenie "mlnet auto-train"</span><span class="sxs-lookup"><span data-stu-id="fac1d-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="fac1d-151">Uruchom następujące polecenie interfejsu wiersza polecenia w strukturze ML.NET:</span><span class="sxs-lookup"><span data-stu-id="fac1d-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="fac1d-152">To polecenie uruchamia  **`mlnet auto-train` polecenia**:</span><span class="sxs-lookup"><span data-stu-id="fac1d-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="fac1d-153">Aby uzyskać **zadania uczenia Maszynowego** typu **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="fac1d-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="fac1d-154">używa **plik zestawu danych `yelp_labelled.txt`**  jako szkolenie i testowanie zestawu danych (wewnętrznie interfejsu wiersza polecenia będzie używać krzyżowego sprawdzania poprawności lub Podziel ją w dwóch zestawów danych, jeden dla szkolenia i jeden do testowania)</span><span class="sxs-lookup"><span data-stu-id="fac1d-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="fac1d-155">gdzie **kolumna docelowa cel** chcesz przewidzieć (często nazywane **"etykieta"**) jest **kolumnę z indeksem 1** (to znaczy drugiej kolumny, ponieważ indeks jest liczony od zera )</span><span class="sxs-lookup"><span data-stu-id="fac1d-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="fac1d-156">jest **używaj nagłówka pliku** przy użyciu nazwy kolumn, ponieważ ten plik do określonego zestawu danych nie ma nagłówka</span><span class="sxs-lookup"><span data-stu-id="fac1d-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="fac1d-157">**docelowe czasu eksploracji** jest eksperyment **10 sekund**</span><span class="sxs-lookup"><span data-stu-id="fac1d-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="fac1d-158">Zostaną wyświetlone dane wyjściowe, interfejs wiersza polecenia, podobnie do:</span><span class="sxs-lookup"><span data-stu-id="fac1d-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="fac1d-159">Windows</span><span class="sxs-lookup"><span data-stu-id="fac1d-159">Windows</span></span>](#tab/windows)

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="fac1d-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="fac1d-161">macOS Bash</span></span>](#tab/macosbash)

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="fac1d-163">W tym konkretnym przypadku zaledwie 10 sekund i przy użyciu małego zestawu danych, pod warunkiem, narzędzie interfejsu wiersza polecenia była w stanie uruchomić kilka iteracji, co oznacza wiele razy na podstawie różnych kombinacji algorytmów/konfiguracji z różnymi danymi wewnętrznego szkolenia przekształcenia i hiper parametrami przez algorytm.</span><span class="sxs-lookup"><span data-stu-id="fac1d-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="fac1d-164">Na koniec modelu "najwyższa jakość", znaleziono w ciągu 10 sekund jest model przy użyciu określonego trainer/algorytmu przy użyciu żadnej określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fac1d-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="fac1d-165">Zależnie od godziny eksploracji polecenie może tworzyć różne wyniki.</span><span class="sxs-lookup"><span data-stu-id="fac1d-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="fac1d-166">Wybór zależy od wielu metryk pokazano, takich jak `Accuracy`.</span><span class="sxs-lookup"><span data-stu-id="fac1d-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="fac1d-167">**Omówienie modelu metryk jakości**</span><span class="sxs-lookup"><span data-stu-id="fac1d-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="fac1d-168">Pierwszy i najprostszy metrykę do oceny, model klasyfikacji danych binarnych jest dokładności, który jest łatwy do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="fac1d-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="fac1d-169">"Dokładności jest część poprawne prognozy przy użyciu testowego zestawu danych".</span><span class="sxs-lookup"><span data-stu-id="fac1d-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="fac1d-170">Bliżej do 100% (1,00), tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="fac1d-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="fac1d-171">Istnieją jednak przypadki, gdzie tylko pomiaru z metryką dokładność nie jest wystarczająco dużo, zwłaszcza w przypadku, gdy etykiety (0 i 1, w tym przypadku) jest niezrównoważone w zestawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="fac1d-172">Dodatkowe metryki i innym **szczegółowe informacje na temat metryk** takich jak dokładność, AUC AUCPR, wynik F1 używane do oceny różne modele, możesz przeczytać [metryki opis strukturze ML.NET](../resources/metrics.md)</span><span class="sxs-lookup"><span data-stu-id="fac1d-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    >  <span data-ttu-id="fac1d-173">Można spróbować tego samego zestawu danych i określić kilka minut, zanim `--max-exploration-time` (na przykład trzy minuty, określ 180 sekund), które znajdzie lepsze "najlepszy model" dla Ciebie za pomocą różnych szkolenia konfiguracji potoku dla tego zestawu danych (jest to łatwa małe, 1000 wierszy).</span><span class="sxs-lookup"><span data-stu-id="fac1d-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="fac1d-174">Aby można było znaleźć model "najlepiej/dobrej jakości", który jest "model gotowe do produkcji" przeznaczonych dla większych zestawów danych, należy eksperymentów przy użyciu interfejsu wiersza polecenia zwykle określenie znacznie więcej eksploracji czasu w zależności od rozmiaru zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="fac1d-175">W rzeczywistości w wielu przypadkach możesz wymagać wiele godzin czasu eksploracji zwłaszcza, jeśli zestaw danych jest duży na wiersze i kolumny.</span><span class="sxs-lookup"><span data-stu-id="fac1d-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="fac1d-176">Poprzednie wykonanie polecenia wygenerowała następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="fac1d-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="fac1d-177">Zserializowany model plik zip ("najlepszy model") gotowych do użycia.</span><span class="sxs-lookup"><span data-stu-id="fac1d-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="fac1d-178">C#kod w celu uruchomienia/wynik, który jest generowany modelu (w celu prognozowania w aplikacji użytkownika końcowego za pomocą modelu).</span><span class="sxs-lookup"><span data-stu-id="fac1d-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="fac1d-179">C#szkolenie kodu służącego do generowania modelu (Learning celów).</span><span class="sxs-lookup"><span data-stu-id="fac1d-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="fac1d-180">Plik dziennika o wszystkich iteracji zbadane, o określonym szczegółowe informacje na temat każdego algorytm próbowała z jego kombinacją przekształcenia danych i hiper parametrami.</span><span class="sxs-lookup"><span data-stu-id="fac1d-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="fac1d-181">Pierwsze dwa zasoby (. Model pliku ZIP i C# kod wymagany do uruchomienia tego modelu) mogą być używane bezpośrednio w aplikacji użytkownika końcowego (aplikacji internetowej ASP.NET Core, usług, aplikacji klasycznej, itp.), tworzyć prognozy przy użyciu wygenerowanych przez model usługi uczenie Maszynowe.</span><span class="sxs-lookup"><span data-stu-id="fac1d-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="fac1d-182">Trzeci zasobu, kod szkolenia, dowiesz się, jaki kod interfejsu API w strukturze ML.NET był używany przez interfejs wiersza polecenia do trenowania wygenerowane, dzięki czemu możesz zbadać, jakie określonego trainer/algorytmu i hiper parametrami zostały wybrane przez interfejs wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fac1d-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="fac1d-183">Te zasoby wyliczany zostały wyjaśnione w poniższych krokach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="fac1d-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="fac1d-184">Zapoznaj się z wygenerowanym C# kodu służące do uruchamiania modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="fac1d-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="fac1d-185">W programie Visual Studio (2017 lub 2019) otwórz rozwiązanie wygenerowane w folderze o nazwie `SampleBinaryClassification` w oryginalnym folderu docelowego (w tym samouczku nosiła nazwę `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="fac1d-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="fac1d-186">Powinny zostać wyświetlone podobne do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="fac1d-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="fac1d-187">W tym samouczku zalecamy używanie programu Visual Studio, ale możesz też zapoznać się z wygenerowanym C# kodu (dwa projekty) za pomocą dowolnego edytora tekstów, a następnie uruchom aplikację konsoli wygenerowany przy użyciu `dotnet CLI` w systemie macOS, maszyny z systemem Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="fac1d-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Rozwiązania VS generowane przez interfejs wiersza polecenia](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="fac1d-189">Wygenerowany **biblioteki klas** zawierająca Zserializowany model uczenia Maszynowego i klas danych jest coś, co jest bezpośrednio użyć w aplikacji użytkownika końcowego, nawet bezpośrednio odwołuje się do tej biblioteki klas (lub przenoszenia kodu, ponieważ użytkownik sobie tego życzy).</span><span class="sxs-lookup"><span data-stu-id="fac1d-189">The generated **class library** containing the serialized ML model and the data classes is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="fac1d-190">Wygenerowany **aplikacja konsolowa** zawiera wykonywania kodu, należy przejrzeć, a następnie zwykle ponownego użycia kodu oceniania (kod, który uruchamia model uczenia Maszynowego do przewidywania przyszłych zdarzeń), przenosząc tego prostego kodu (zaledwie kilku wierszy) do użytkownika końcowego Aplikacja, której chcesz tworzyć prognozy.</span><span class="sxs-lookup"><span data-stu-id="fac1d-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="fac1d-191">Otwórz **Observation.cs** i **Prediction.cs** klasy pliki znajdujące się w projekcie biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="fac1d-191">Open the **Observation.cs** and **Prediction.cs** class files within the class library project.</span></span> <span data-ttu-id="fac1d-192">Zobaczysz, że te klasy są "klas danych" lub klasy POCO używana do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="fac1d-193">Jest "standardowy kod", ale warto mieć on generowany, gdy zestaw danych zawiera dziesiątki lub nawet setki kolumn.</span><span class="sxs-lookup"><span data-stu-id="fac1d-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="fac1d-194">`SampleObservation` Klasa jest używana podczas odczytywania danych z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-194">The `SampleObservation` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="fac1d-195">`SamplePrediction` Klasy lub</span><span class="sxs-lookup"><span data-stu-id="fac1d-195">The `SamplePrediction` class or when</span></span>

1. <span data-ttu-id="fac1d-196">Otwórz plik Program.cs i zapoznaj się z kodu.</span><span class="sxs-lookup"><span data-stu-id="fac1d-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="fac1d-197">W zaledwie kilku wierszach jesteś w stanie uruchomić model i przewiduje próbki.</span><span class="sxs-lookup"><span data-stu-id="fac1d-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<SampleObservation, SamplePrediction>(mlModel);

        // Create sample data to do a single prediction with it 
        SampleObservation sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        SamplePrediction predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- <span data-ttu-id="fac1d-198">Pierwszy wiersz kodu po prostu tworzy `MLContext` obiektów potrzebnych przy każdym uruchomieniu strukturze ML.NET kodu.</span><span class="sxs-lookup"><span data-stu-id="fac1d-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="fac1d-199">Drugi wiersz kodu jest ujęta, ponieważ nie trzeba uczyć że modelu, ponieważ był już uczony dla Ciebie za pomocą narzędzia interfejsu wiersza polecenia i zapisywane w modelu serializowane. Plik ZIP.</span><span class="sxs-lookup"><span data-stu-id="fac1d-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="fac1d-200">Ale jeśli chcesz zobaczyć *"jak model został uczony"* przez interfejs wiersza polecenia, można usuń znaczniki komentarza tego wiersza i uruchomienia/debugowania do kodu szkolenie modelu uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="fac1d-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="fac1d-201">Trzeci wiersz kodu należy załadować modelu z modelu serializowane. Plik ZIP z `mlContext.Model.Load()` interfejsu API, podając ścieżkę do tego modelu. Plik ZIP.</span><span class="sxs-lookup"><span data-stu-id="fac1d-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="fac1d-202">W czwartym wierszu kodu, należy załadować tworzenie `PredictionEngine` obiekt z `mlContext.Model.CreatePredictionEngine<TObservation, TPrediction>()` interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="fac1d-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TObservation, TPrediction>()` API.</span></span> <span data-ttu-id="fac1d-203">Potrzebujesz `PredictionEngine` obiektu służy do prognozowania przeznaczonych dla pojedynczej próbki danych (w tym przypadku pojedynczy fragment tekstu do prognozowania jego tonacji).</span><span class="sxs-lookup"><span data-stu-id="fac1d-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="fac1d-204">Piąty wiersz kodu służy do tworzenia, *jednego źródła danych przykładowych* do użycia przez wywołanie funkcji prognozowania `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="fac1d-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="fac1d-205">Ponieważ narzędzie interfejsu wiersza polecenia nie wie, jakiego rodzaju przykładowych danych do użycia, w ramach tej funkcji ładowania pierwszy wiersz z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="fac1d-206">Jednak dla tego przypadku możesz można również utworzyć własne dane "zakodowane" zamiast bieżąca implementacja parametru `CreateSingleDataSample()` funkcji, aktualizując ten kod prostsze Implementowanie tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="fac1d-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static SampleObservation CreateSingleDataSample()
    {
        SampleObservation sampleForPrediction = new SampleObservation() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="fac1d-207">Uruchom projekt, oryginalnym przykładowe dane przy użyciu załadowane z pierwszy wiersz z zestawu danych lub, podając własne niestandardowe ustaloną przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="fac1d-208">Pobieraj porównywalne do prognozowania:</span><span class="sxs-lookup"><span data-stu-id="fac1d-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="fac1d-209">Windows</span><span class="sxs-lookup"><span data-stu-id="fac1d-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="fac1d-210">Uruchamianie aplikacji konsolowej w programie Visual Studio przez naciskać klawisz F5 (przycisk odtwarzania):</span><span class="sxs-lookup"><span data-stu-id="fac1d-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="fac1d-212">)</span><span class="sxs-lookup"><span data-stu-id="fac1d-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="fac1d-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="fac1d-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="fac1d-214">Uruchamianie aplikacji konsolowej w wierszu polecenia, wpisując następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="fac1d-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="fac1d-216">)</span><span class="sxs-lookup"><span data-stu-id="fac1d-216">)</span></span>

    ---

1. <span data-ttu-id="fac1d-217">Spróbuj zmienić ustaloną przykładowych danych do innych zdań przy użyciu różnych tonacji i zobacz, jak model przewiduje tonacji dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="fac1d-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="fac1d-218">Sprawić, że aplikacje użytkownika końcowego z określane są przewidywania modelu uczenia Maszynowego</span><span class="sxs-lookup"><span data-stu-id="fac1d-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="fac1d-219">Możesz użyć podobnych "ML modelu kodu oceniania" uruchomić model w prognozy marki i aplikacji przez użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="fac1d-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="fac1d-220">Na przykład, można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznych Windows takich jak **WPP** i **WinForms** i uruchomić model w taki sam sposób, niż zostało to zrobione w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="fac1d-220">For instance, you could directly move that code to any Windows desktop application such as **WPP** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="fac1d-221">Jednak sposób zaimplementować te wiersze kodu, aby uruchomić model uczenia Maszynowego optymalizacji (który jest plik zip modelu w pamięci podręcznej, a następnie załaduj raz) i ma pojedyncze obiekty, zamiast tworzyć je na każde żądanie, zwłaszcza, jeśli aplikacja musi być skalowalne, takich jak Aplikacja sieci web lub usługę rozproszonej, jak wyjaśniono w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="fac1d-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="fac1d-222">Uruchamianie strukturze ML.NET modeli w usługach (wielowątkowe aplikacje) i skalowalnych aplikacji sieci web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fac1d-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="fac1d-223">Tworzenie obiektu modelu (`ITransformer` załadowanego z pliku zip modelu) i `PredictionEngine` zoptymalizowane obiektu, szczególnie w przypadku korzystania na skalowalnych aplikacji sieci web i usług rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="fac1d-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="fac1d-224">W przypadku pierwszy obiekt modelu (`ITransformer`) Optymalizacja jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="fac1d-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="fac1d-225">Ponieważ `ITransformer` obiektu jest bezpieczna dla wątków, można buforować obiektu jako pojedyncze lub obiektu statycznego, więc raz załadować modelu.</span><span class="sxs-lookup"><span data-stu-id="fac1d-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="fac1d-226">Dla drugiego obiektu `PredictionEngine` obiektu nie jest tak proste ponieważ `PredictionEngine` obiekt nie jest bezpieczna dla wątków, w związku z tym nie możesz utworzyć wystąpienia tego obiektu jako pojedyncze lub statycznych obiektów w aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fac1d-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="fac1d-227">Ten problem metodą o bezpiecznych wątkach i skalowalność głęboko została omówiona w tym [wpis w blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="fac1d-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="fac1d-228">Jednak rzeczy stało się znacznie łatwiejsze dla Ciebie niż co zostało wyjaśnione w tym wpisie.</span><span class="sxs-lookup"><span data-stu-id="fac1d-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="fac1d-229">Firma Microsoft pracuje prostszej metody dla Ciebie i utworzono nieuprzywilejowany **"Pakiet integracyjny platformy .NET Core"** można łatwo użycie w swoje aplikacje platformy ASP.NET Core i usługi przez zarejestrowanie go w usługach aplikacji DI (wstrzykiwanie zależności usługi) i następnie bezpośrednio korzystać z niego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fac1d-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="fac1d-230">Sprawdź następujące samouczek i przykład tych czynności:</span><span class="sxs-lookup"><span data-stu-id="fac1d-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="fac1d-231">Samouczek: Systemem modeli strukturze ML.NET skalowalnej platformy ASP.NET Core WebAPIs i aplikacji sieci web</span><span class="sxs-lookup"><span data-stu-id="fac1d-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="fac1d-232">Przykład: Skalowalna modelu strukturze ML.NET na platformy ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="fac1d-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="fac1d-233">Zapoznaj się z wygenerowanym C# kod, który został użyty do nauczenia modelu "najwyższa jakość"</span><span class="sxs-lookup"><span data-stu-id="fac1d-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="fac1d-234">Bardziej zaawansowane celów szkoleniowych, możesz również zapoznać się z wygenerowanym C# kod, który był używany przez narzędzie interfejsu wiersza polecenia do nauczenia modelu wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="fac1d-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="fac1d-235">"Szkolenie modelu kodu" jest obecnie generowany w niestandardowej klasy, które są generowane o nazwie `ModelBuilder` dzięki którym możesz zbadać kod szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fac1d-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="fac1d-236">Co ważniejsze dla tego konkretnego scenariusza (analiza tonacji model) można również porównać, szkolenie wygenerowany kod kodem szczegółowo następującego samouczka:</span><span class="sxs-lookup"><span data-stu-id="fac1d-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="fac1d-237">Porównaj: [Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).</span><span class="sxs-lookup"><span data-stu-id="fac1d-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).</span></span>

<span data-ttu-id="fac1d-238">Jest to interesujące do porównania wybranego konfigurację algorytmu i potoku w tym samouczku kod wygenerowany przez narzędzie interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fac1d-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="fac1d-239">Zależności od tego, ile czasu wydania iteracja i wyszukiwania dla sprawniejszych modeli wybrany algorytm może różnić się wraz z jego określonego hiper parametrami i konfiguracja potoku.</span><span class="sxs-lookup"><span data-stu-id="fac1d-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="fac1d-240">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fac1d-240">See also</span></span>

- [<span data-ttu-id="fac1d-241">Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="fac1d-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="fac1d-242">Samouczek: Systemem modeli strukturze ML.NET skalowalnej platformy ASP.NET Core WebAPIs i aplikacji sieci web</span><span class="sxs-lookup"><span data-stu-id="fac1d-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="fac1d-243">Przykład: Skalowalna modelu strukturze ML.NET na platformy ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="fac1d-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="fac1d-244">Podręcznik interfejsu wiersza polecenia w strukturze ML.NET train automatycznie poleceń</span><span class="sxs-lookup"><span data-stu-id="fac1d-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="fac1d-245">Jak zainstalować narzędzie strukturze ML.NET interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="fac1d-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="fac1d-246">Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="fac1d-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="fac1d-247">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fac1d-247">Next steps</span></span>

<span data-ttu-id="fac1d-248">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="fac1d-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="fac1d-249">Przygotowywanie danych dla wybranego zadania uczenia Maszynowego (problemu do rozwiązania)</span><span class="sxs-lookup"><span data-stu-id="fac1d-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> * <span data-ttu-id="fac1d-250">Uruchom polecenie "mlnet auto-train" za pomocą narzędzia interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="fac1d-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> * <span data-ttu-id="fac1d-251">Przejrzyj wyniki metryk jakości</span><span class="sxs-lookup"><span data-stu-id="fac1d-251">Review the quality metric results</span></span>
> * <span data-ttu-id="fac1d-252">Zrozumienie wygenerowany C# kod, aby uruchomić model (kod do użycia w aplikacji użytkownika końcowego)</span><span class="sxs-lookup"><span data-stu-id="fac1d-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> * <span data-ttu-id="fac1d-253">Zapoznaj się z wygenerowanym C# kod, który został użyty do nauczenia modelu "najwyższa jakość" (uczenie celów)</span><span class="sxs-lookup"><span data-stu-id="fac1d-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fac1d-254">Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="fac1d-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
