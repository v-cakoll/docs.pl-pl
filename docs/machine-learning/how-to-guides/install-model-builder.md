---
title: Jak zainstalować program model Builder
description: Dowiedz się, jak zainstalować narzędzie ML.NET model Builder
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b87f712ad7a8b2229c1d42db4bad1fe511475ac7
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552943"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="03366-103">Jak zainstalować program ML.NET model Builder</span><span class="sxs-lookup"><span data-stu-id="03366-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="03366-104">Dowiedz się, jak zainstalować program ML.NET model Builder, aby dodać Uczenie maszynowe do aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="03366-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="03366-105">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="03366-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03366-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="03366-106">Prerequisites</span></span>

- <span data-ttu-id="03366-107">Visual Studio 2017 w wersji 15.9.12 lub nowszej/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="03366-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="03366-108">.NET Core 2,1 SDK lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="03366-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="03366-109">Zestaw SDK platformy .NET Core 3,0 nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="03366-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="03366-110">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="03366-110">Limitations</span></span>

- <span data-ttu-id="03366-111">Rozszerzenie konstruktora modelu ML.NET aktualnie działa tylko w programie Visual Studio w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="03366-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="03366-112">Limit zestawu danych szkolenia wynoszący 1 GB</span><span class="sxs-lookup"><span data-stu-id="03366-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="03366-113">SQL Server ma limit 100 000 wierszy na potrzeby szkolenia</span><span class="sxs-lookup"><span data-stu-id="03366-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="03366-114">Narzędzia Microsoft SQL Server Data Tools for Visual Studio 2017 nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="03366-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="03366-115">Instalacja programu</span><span class="sxs-lookup"><span data-stu-id="03366-115">Install</span></span>

<span data-ttu-id="03366-116">Konstruktora modelu ML.NET można zainstalować za pośrednictwem Visual Studio Marketplace lub z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03366-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="03366-117">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="03366-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="03366-118">Pobierz z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="03366-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="03366-119">Postępuj zgodnie z monitami, aby zainstalować odpowiednie wersje programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03366-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="03366-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="03366-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="03366-121">Na pasku menu wybierz kolejno opcje **narzędzia** > **rozszerzenia i aktualizacje** .</span><span class="sxs-lookup"><span data-stu-id="03366-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń program VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="03366-123">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .</span><span class="sxs-lookup"><span data-stu-id="03366-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="03366-124">Na pasku wyszukiwania Wyszukaj pozycję *ml.NET model Builder* i z wyników wybierz pozycję ml.NET model Builder (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="03366-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![Program VS2017 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="03366-126">Postępuj zgodnie z monitami, aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="03366-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="03366-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="03366-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="03366-128">Na pasku menu wybierz pozycję **rozszerzenia** > **Zarządzanie rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="03366-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="03366-130">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .</span><span class="sxs-lookup"><span data-stu-id="03366-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="03366-131">Wpisz *ml.NET model Builder* na pasku wyszukiwania wybierz pozycję ml.NET model Builder (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="03366-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="03366-133">Postępuj zgodnie z monitami, aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="03366-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="03366-134">Odinstaluj</span><span class="sxs-lookup"><span data-stu-id="03366-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="03366-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="03366-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="03366-136">Na pasku menu wybierz kolejno opcje **narzędzia** > **rozszerzenia i aktualizacje** .</span><span class="sxs-lookup"><span data-stu-id="03366-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Program VS2017 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="03366-138">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="03366-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="03366-139">Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .</span><span class="sxs-lookup"><span data-stu-id="03366-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Rozszerzenie program VS2017 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="03366-141">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="03366-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="03366-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="03366-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="03366-143">Na pasku menu wybierz pozycję **rozszerzenia** > **Zarządzanie rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="03366-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="03366-145">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="03366-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="03366-146">Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .</span><span class="sxs-lookup"><span data-stu-id="03366-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Rozszerzenie VS2019 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="03366-148">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="03366-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="03366-149">Uaktualniony</span><span class="sxs-lookup"><span data-stu-id="03366-149">Upgrade</span></span>

<span data-ttu-id="03366-150">Proces uaktualniania jest podobny do procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="03366-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="03366-151">Pobierz najnowszą wersję z programu Visual Studio Marketplace lub użyj Menedżera rozszerzeń w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03366-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
