---
title: Załaduj dane szkoleniowe dla konstruktora modeli
description: Dowiedz się, jak załadować dane szkoleniowe z bazy danych programu SQL Server lub pliku do użycia w jednym ze scenariuszy Konstruktora modeli dla ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849162"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="e2bec-103">Załaduj dane szkoleniowe do konstruktora modeli</span><span class="sxs-lookup"><span data-stu-id="e2bec-103">Load training data into Model Builder</span></span>

<span data-ttu-id="e2bec-104">Dowiedz się, jak załadować zestawy danych szkoleniowych z pliku lub bazy danych programu SQL Server do użycia w jednym ze scenariuszy Konstruktora modeli dla ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e2bec-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="e2bec-105">Scenariusze Programu Model Builder mogą używać baz danych programu SQL Server, plików obrazów oraz formatów plików CSV lub TSV jako danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="e2bec-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="e2bec-106">Ograniczenia zestawu danych szkoleniowych w Konstruktorze modeli</span><span class="sxs-lookup"><span data-stu-id="e2bec-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="e2bec-107">Konstruktor modeli ogranicza ilość i typ danych, których można używać w modelach szkoleniowych:</span><span class="sxs-lookup"><span data-stu-id="e2bec-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="e2bec-108">Dane programu SQL Server: 100 000 wierszy</span><span class="sxs-lookup"><span data-stu-id="e2bec-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="e2bec-109">Pliki CSV i TSV: Brak limitu rozmiaru</span><span class="sxs-lookup"><span data-stu-id="e2bec-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="e2bec-110">Obrazy: tylko PNG i JPG.</span><span class="sxs-lookup"><span data-stu-id="e2bec-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="e2bec-111">Scenariusze konstruktora modeli</span><span class="sxs-lookup"><span data-stu-id="e2bec-111">Model Builder scenarios</span></span>

<span data-ttu-id="e2bec-112">Program Model Builder ułatwia tworzenie modeli dla następujących scenariuszy uczenia maszynowego:</span><span class="sxs-lookup"><span data-stu-id="e2bec-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="e2bec-113">Analiza tonacji (klasyfikacja binarna): Klasyfikowanie danych tekstowych do dwóch kategorii.</span><span class="sxs-lookup"><span data-stu-id="e2bec-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="e2bec-114">Klasyfikacja problemów (klasyfikacja wieloklasowa): Zaklasyfikowanie danych tekstowych do 3 lub więcej kategorii.</span><span class="sxs-lookup"><span data-stu-id="e2bec-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="e2bec-115">Przewidywanie cen (regresja): Przewidywanie wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="e2bec-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="e2bec-116">Klasyfikacja obrazów (uczenie głębokie): Kategoryzuj obrazy na podstawie cech.</span><span class="sxs-lookup"><span data-stu-id="e2bec-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="e2bec-117">Scenariusz niestandardowy: Tworzenie scenariuszy niestandardowych na podstawie danych przy użyciu regresji, klasyfikacji i innych zadań.</span><span class="sxs-lookup"><span data-stu-id="e2bec-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="e2bec-118">W tym artykule omówiono scenariusze klasyfikacji i regresji z danymi tekstowymi lub liczbowymi oraz scenariuszami klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="e2bec-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="e2bec-119">Ładowanie tekstu lub danych liczbowych z pliku</span><span class="sxs-lookup"><span data-stu-id="e2bec-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="e2bec-120">Do Konstruktora modeli można załadować dane tekstowe lub liczbowe z pliku.</span><span class="sxs-lookup"><span data-stu-id="e2bec-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="e2bec-121">Akceptuje formaty plików rozdzielanych przecinkami (CSV) lub rozdzielanych kartami (TSV).</span><span class="sxs-lookup"><span data-stu-id="e2bec-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="e2bec-122">W kroku danych Konstruktora modeli wybierz **pozycję Plik** z listy rozwijanej źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e2bec-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="e2bec-123">Zaznacz przycisk obok pola **tekstowego Wybierz plik** i użyj Eksploratora plików, aby przeglądać i wybierać plik danych.</span><span class="sxs-lookup"><span data-stu-id="e2bec-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="e2bec-124">Wybierz kategorię z listy rozwijanej **Kolumna do przewidzenia (etykieta).**</span><span class="sxs-lookup"><span data-stu-id="e2bec-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="e2bec-125">Z listy **rozwijanej Kolumny wejściowe (Funkcje)** upewnij się, że kolumny danych, które chcesz uwzględnić, są zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="e2bec-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="e2bec-126">Gotowe skonfigurowanie pliku źródła danych dla Konstruktora modeli.</span><span class="sxs-lookup"><span data-stu-id="e2bec-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="e2bec-127">Wybierz **łącze Pociąg,** aby przejść do następnego kroku w konstruktorze modeli.</span><span class="sxs-lookup"><span data-stu-id="e2bec-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="e2bec-128">Ładowanie danych z bazy danych programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="e2bec-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="e2bec-129">Program Model Builder obsługuje ładowanie danych z lokalnych i zdalnych baz danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e2bec-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="e2bec-130">Aby załadować dane z bazy danych programu SQL Server do konstruktora modułów:</span><span class="sxs-lookup"><span data-stu-id="e2bec-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="e2bec-131">W kroku tworzenia danych konstruktora modeli wybierz pozycję **SQL Server** z listy rozwijanej źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e2bec-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="e2bec-132">Zaznacz przycisk obok pola tekstowego Połącz z **bazą danych programu SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="e2bec-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="e2bec-133">W oknie dialogowym **Wybieranie danych** wybierz pozycję **Plik bazy danych programu Microsoft SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="e2bec-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="e2bec-134">Wyczyść zaznaczenie pola wyboru **Zawsze używaj tego zaznaczenia** i wybierz **pozycję Kontynuuj**</span><span class="sxs-lookup"><span data-stu-id="e2bec-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="e2bec-135">W oknie dialogowym **Właściwości połączenia** wybierz pozycję **Przeglądaj** i wybierz pobraną opcję . MDF.</span><span class="sxs-lookup"><span data-stu-id="e2bec-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="e2bec-136">Wybierz **OK**</span><span class="sxs-lookup"><span data-stu-id="e2bec-136">Select **OK**</span></span>
1. <span data-ttu-id="e2bec-137">Wybierz nazwę zestawu danych z **listy rozwijanej Nazwa tabeli.**</span><span class="sxs-lookup"><span data-stu-id="e2bec-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="e2bec-138">Z listy rozwijanej **Kolumna do przewidywania (etykieta)** wybierz kategorię danych, w której chcesz dokonać przewidywania.</span><span class="sxs-lookup"><span data-stu-id="e2bec-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="e2bec-139">Z listy **rozwijanej Kolumny wejściowe (Funkcje)** upewnij się, że kolumny, które chcesz uwzględnić, są zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="e2bec-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="e2bec-140">Gotowe skonfigurowanie pliku źródła danych dla Konstruktora modeli.</span><span class="sxs-lookup"><span data-stu-id="e2bec-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="e2bec-141">Wybierz **łącze Pociąg,** aby przejść do następnego kroku w konstruktorze modeli.</span><span class="sxs-lookup"><span data-stu-id="e2bec-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="e2bec-142">Konfigurowanie plików danych obrazu</span><span class="sxs-lookup"><span data-stu-id="e2bec-142">Set up image data files</span></span>

<span data-ttu-id="e2bec-143">Model Builder oczekuje, że dane obrazu będą plikami JPG lub PNG zorganizowanymi w foldery odpowiadające kategoriom klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e2bec-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="e2bec-144">Aby załadować obrazy do Konstruktora modeli, należy podać ścieżkę do jednego katalogu najwyższego poziomu:</span><span class="sxs-lookup"><span data-stu-id="e2bec-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="e2bec-145">Ten katalog najwyższego poziomu zawiera jeden podfolder dla każdej z kategorii do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="e2bec-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="e2bec-146">Każdy podfolder zawiera pliki obrazów należące do jego kategorii.</span><span class="sxs-lookup"><span data-stu-id="e2bec-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="e2bec-147">W strukturze folderów przedstawionej poniżej katalog najwyższego poziomu jest *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="e2bec-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="e2bec-148">Istnieje pięć podkatalogów odpowiadających kategoriom, które chcesz przewidzieć: stokrotki, mniszka lekarskiego, róż, słoneczników i tulipanów.</span><span class="sxs-lookup"><span data-stu-id="e2bec-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="e2bec-149">Każdy z tych podkatalogów zawiera obrazy należące do odpowiedniej kategorii.</span><span class="sxs-lookup"><span data-stu-id="e2bec-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a><span data-ttu-id="e2bec-150">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e2bec-150">Next steps</span></span>

<span data-ttu-id="e2bec-151">Wykonaj następujące samouczki, aby tworzyć aplikacje do uczenia maszynowego za pomocą programu Model Builder:</span><span class="sxs-lookup"><span data-stu-id="e2bec-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="e2bec-152">Przewidywanie cen za pomocą regresji</span><span class="sxs-lookup"><span data-stu-id="e2bec-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="e2bec-153">Analizowanie opinii w aplikacji sieci web przy użyciu klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="e2bec-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="e2bec-154">Jeśli szkolisz model przy użyciu kodu, [dowiedz się, jak załadować dane przy użyciu ML.NET interfejsu API](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="e2bec-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
