---
title: Jak zainstalować program model Builder
description: Dowiedz się, jak zainstalować narzędzie ML.NET model Builder
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774570"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="63602-103">Jak zainstalować program ML.NET model Builder</span><span class="sxs-lookup"><span data-stu-id="63602-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="63602-104">Dowiedz się, jak zainstalować program ML.NET model Builder, aby dodać Uczenie maszynowe do aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="63602-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="63602-105">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="63602-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="63602-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="63602-106">Pre-requisites</span></span>

- <span data-ttu-id="63602-107">Visual Studio 2017 w wersji 15.9.12 lub nowszej/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="63602-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="63602-108">Zestaw SDK platformy .NET Core 2,1 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="63602-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="63602-109">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="63602-109">Limitations</span></span>

- <span data-ttu-id="63602-110">Rozszerzenie konstruktora modelu ML.NET aktualnie działa tylko w programie Visual Studio w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="63602-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="63602-111">Limit zestawu danych szkolenia wynoszący 1 GB</span><span class="sxs-lookup"><span data-stu-id="63602-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="63602-112">SQL Server ma limit 100 000 wierszy na potrzeby szkolenia</span><span class="sxs-lookup"><span data-stu-id="63602-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="63602-113">Narzędzia Microsoft SQL Server Data Tools for Visual Studio 2017 nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="63602-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="63602-114">Zainstaluj</span><span class="sxs-lookup"><span data-stu-id="63602-114">Install</span></span>

<span data-ttu-id="63602-115">Konstruktora modelu ML.NET można zainstalować za pośrednictwem Visual Studio Marketplace lub z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63602-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="63602-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="63602-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="63602-117">Pobierz z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="63602-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="63602-118">Postępuj zgodnie z monitami, aby zainstalować odpowiednie wersje programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63602-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="63602-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="63602-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="63602-120">Na pasku menu wybierz kolejno opcje **narzędzia**  > **rozszerzenia i aktualizacje** .</span><span class="sxs-lookup"><span data-stu-id="63602-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń program VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="63602-122">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .</span><span class="sxs-lookup"><span data-stu-id="63602-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="63602-123">Na pasku wyszukiwania Wyszukaj pozycję *ml.NET model Builder* i z wyników wybierz pozycję ml.NET model Builder (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="63602-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![Program VS2017 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="63602-125">Postępuj zgodnie z monitami, aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="63602-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="63602-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="63602-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="63602-127">Na pasku menu wybierz pozycję **rozszerzenia**  > **Zarządzanie rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="63602-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="63602-129">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .</span><span class="sxs-lookup"><span data-stu-id="63602-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="63602-130">Wpisz *ml.NET model Builder* na pasku wyszukiwania wybierz pozycję ml.NET model Builder (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="63602-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="63602-132">Postępuj zgodnie z monitami, aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="63602-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="63602-133">Odinstaluj</span><span class="sxs-lookup"><span data-stu-id="63602-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="63602-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="63602-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="63602-135">Na pasku menu wybierz kolejno opcje **narzędzia**  > **rozszerzenia i aktualizacje** .</span><span class="sxs-lookup"><span data-stu-id="63602-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Program VS2017 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="63602-137">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="63602-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="63602-138">Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .</span><span class="sxs-lookup"><span data-stu-id="63602-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Rozszerzenie program VS2017 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="63602-140">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="63602-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="63602-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="63602-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="63602-142">Na pasku menu wybierz pozycję **rozszerzenia**  > **Zarządzanie rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="63602-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="63602-144">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="63602-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="63602-145">Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .</span><span class="sxs-lookup"><span data-stu-id="63602-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Rozszerzenie VS2019 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="63602-147">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="63602-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="63602-148">Uaktualniony</span><span class="sxs-lookup"><span data-stu-id="63602-148">Upgrade</span></span>

<span data-ttu-id="63602-149">Proces uaktualniania jest podobny do procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="63602-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="63602-150">Pobierz najnowszą wersję z programu Visual Studio Marketplace lub użyj Menedżera rozszerzeń w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63602-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
