---
title: Jak zainstalować program model Builder
description: Dowiedz się, jak zainstalować narzędzie ML.NET model Builder
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b0d45ab7807bf84b98c58e85580d5aa04d0c5f7d
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306325"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="eacca-103">Jak zainstalować program ML.NET model Builder</span><span class="sxs-lookup"><span data-stu-id="eacca-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="eacca-104">Dowiedz się, jak zainstalować program ML.NET model Builder, aby dodać Uczenie maszynowe do aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="eacca-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="eacca-105">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="eacca-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="eacca-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="eacca-106">Pre-requisites</span></span>

- <span data-ttu-id="eacca-107">Visual Studio 2017 15.9.12 lub nowszy/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="eacca-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="eacca-108">Zestaw SDK platformy .NET Core 2,1 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="eacca-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="eacca-109">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="eacca-109">Limitations</span></span>

- <span data-ttu-id="eacca-110">Rozszerzenie konstruktora modelu ML.NET aktualnie działa tylko w programie Visual Studio w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="eacca-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="eacca-111">Limit zestawu danych szkolenia wynoszący 1 GB</span><span class="sxs-lookup"><span data-stu-id="eacca-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="eacca-112">SQL Server ma limit 100 000 wierszy na potrzeby szkolenia</span><span class="sxs-lookup"><span data-stu-id="eacca-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="eacca-113">Narzędzia Microsoft SQL Server Data Tools for Visual Studio 2017 nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="eacca-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="eacca-114">Instalowanie</span><span class="sxs-lookup"><span data-stu-id="eacca-114">Install</span></span>

<span data-ttu-id="eacca-115">Konstruktora modelu ML.NET można zainstalować za pośrednictwem Visual Studio Marketplace lub z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eacca-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="eacca-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="eacca-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="eacca-117">Pobierz z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="eacca-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="eacca-118">Postępuj zgodnie z monitami, aby zainstalować odpowiednie wersje programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eacca-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="eacca-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="eacca-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="eacca-120">Na pasku menu wybierz kolejno opcje **Narzędzia** > **rozszerzenia i aktualizacje** .</span><span class="sxs-lookup"><span data-stu-id="eacca-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń program VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="eacca-122">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .</span><span class="sxs-lookup"><span data-stu-id="eacca-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="eacca-123">Na pasku wyszukiwania Wyszukaj pozycję *ml.NET model Builder* i z wyników wybierz pozycję ml.NET model Builder (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="eacca-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![Program VS2017 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="eacca-125">Postępuj zgodnie z monitami, aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="eacca-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="eacca-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="eacca-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="eacca-127">Na pasku menu wybierz **rozszerzenia** > **Zarządzanie rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="eacca-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="eacca-129">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .</span><span class="sxs-lookup"><span data-stu-id="eacca-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="eacca-130">Wpisz *ml.NET model Builder* na pasku wyszukiwania wybierz pozycję ml.NET model Builder (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="eacca-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="eacca-132">Postępuj zgodnie z monitami, aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="eacca-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="eacca-133">Odinstaluj</span><span class="sxs-lookup"><span data-stu-id="eacca-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="eacca-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="eacca-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="eacca-135">Na pasku menu wybierz kolejno opcje **Narzędzia** > **rozszerzenia i aktualizacje** .</span><span class="sxs-lookup"><span data-stu-id="eacca-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Program VS2017 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="eacca-137">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="eacca-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="eacca-138">Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .</span><span class="sxs-lookup"><span data-stu-id="eacca-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Rozszerzenie program VS2017 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="eacca-140">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="eacca-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="eacca-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="eacca-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="eacca-142">Na pasku menu wybierz **rozszerzenia** > **Zarządzanie rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="eacca-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="eacca-144">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="eacca-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="eacca-145">Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .</span><span class="sxs-lookup"><span data-stu-id="eacca-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Rozszerzenie VS2019 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="eacca-147">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="eacca-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="eacca-148">Uaktualniony</span><span class="sxs-lookup"><span data-stu-id="eacca-148">Upgrade</span></span>

<span data-ttu-id="eacca-149">Proces uaktualniania jest podobny do procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="eacca-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="eacca-150">Pobierz najnowszą wersję z programu Visual Studio Marketplace lub użyj Menedżera rozszerzeń w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eacca-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
