---
title: Jak zainstalować Model Konstruktora
description: Dowiedz się, jak zainstalować narzędzie ML.NET Model Builder
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848655"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="fab41-103">Jak zainstalować ML.NET Model Builder</span><span class="sxs-lookup"><span data-stu-id="fab41-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="fab41-104">Dowiedz się, jak zainstalować ML.NET Model Builder, aby dodać uczenie maszynowe do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="fab41-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="fab41-105">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="fab41-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fab41-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fab41-106">Prerequisites</span></span>

- <span data-ttu-id="fab41-107">Visual Studio 2017 w wersji 15.9.12 lub nowszej / Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="fab41-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="fab41-108">SDK .NET Core 2.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="fab41-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="fab41-109">Zestaw SDK .NET Core 3.0 nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="fab41-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="fab41-110">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="fab41-110">Limitations</span></span>

- <span data-ttu-id="fab41-111">ML.NET Rozszerzenie Konstruktora modeli działa obecnie tylko w programie Visual Studio w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="fab41-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="fab41-112">Limit zestawu danych szkoleniowych 1 GB</span><span class="sxs-lookup"><span data-stu-id="fab41-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="fab41-113">PROGRAM SQL Server ma limit 100 tysięcy wierszy na szkolenia</span><span class="sxs-lookup"><span data-stu-id="fab41-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="fab41-114">Narzędzia danych programu Microsoft SQL Server dla programu Visual Studio 2017 nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="fab41-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="fab41-115">Instalowanie</span><span class="sxs-lookup"><span data-stu-id="fab41-115">Install</span></span>

<span data-ttu-id="fab41-116">ML.NET konstruktora modelu można zainstalować za pośrednictwem portalu Visual Studio Marketplace lub z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fab41-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="fab41-117">Witryna Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="fab41-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="fab41-118">Pobierz z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="fab41-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="fab41-119">Postępuj zgodnie z monitami, aby zainstalować odpowiednią wersję programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fab41-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="fab41-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fab41-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="fab41-121">Na pasku menu wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > </span><span class="sxs-lookup"><span data-stu-id="fab41-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Vs2017 otwórz menedżera rozszerzeń okno dialogowe](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="fab41-123">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online.*</span><span class="sxs-lookup"><span data-stu-id="fab41-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="fab41-124">Na pasku wyszukiwania wyszukaj *ML.NET Konstruktora modeli* i na podstawie wyników wybierz ML.NET Konstruktora modeli (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="fab41-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![Vs2017 wyszukiwanie i instalowanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="fab41-126">Postępuj zgodnie z monitami, aby ukończyć instalację</span><span class="sxs-lookup"><span data-stu-id="fab41-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="fab41-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="fab41-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="fab41-128">Na pasku menu wybierz pozycję **Rozszerzenia** > **Zarządzaj rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="fab41-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Vs2019 otwórz menedżera rozszerzeń okno dialogowe](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="fab41-130">W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online.*</span><span class="sxs-lookup"><span data-stu-id="fab41-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="fab41-131">Wpisz *ML.NET Konstruktora modeli* na pasku wyszukiwania wybierz pozycję ML.NET Konstruktor modeli (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="fab41-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![Vs2019 wyszukiwanie i instalowanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="fab41-133">Postępuj zgodnie z monitami, aby ukończyć instalację</span><span class="sxs-lookup"><span data-stu-id="fab41-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="fab41-134">Dezinstalacja</span><span class="sxs-lookup"><span data-stu-id="fab41-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="fab41-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fab41-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="fab41-136">Na pasku menu wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > </span><span class="sxs-lookup"><span data-stu-id="fab41-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Vs2017 otwórz zarządzanie rozszerzeniami, okno dialogowe](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="fab41-138">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *Zainstalowane* i wybierz *pozycję Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="fab41-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="fab41-139">Wybierz ML.NET Konstruktora modeli (Podgląd) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj*</span><span class="sxs-lookup"><span data-stu-id="fab41-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Vs2017 wyszukiwanie i odinstalowywanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="fab41-141">Postępuj zgodnie z instrukcjami, aby zakończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="fab41-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="fab41-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="fab41-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="fab41-143">Na pasku menu wybierz pozycję **Rozszerzenia** > **Zarządzaj rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="fab41-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Vs2019 otwórz zarządzanie rozszerzeniami, okno dialogowe](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="fab41-145">W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *Zainstalowane* i wybierz *pozycję Narzędzia*</span><span class="sxs-lookup"><span data-stu-id="fab41-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="fab41-146">Wybierz ML.NET Konstruktora modeli (Podgląd) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj*</span><span class="sxs-lookup"><span data-stu-id="fab41-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![Vs2019 wyszukiwanie i odinstalowywanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="fab41-148">Postępuj zgodnie z instrukcjami, aby zakończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="fab41-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="fab41-149">Uaktualnienie</span><span class="sxs-lookup"><span data-stu-id="fab41-149">Upgrade</span></span>

<span data-ttu-id="fab41-150">Proces uaktualniania jest podobny do procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="fab41-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="fab41-151">Pobierz najnowszą wersję z programu Visual Studio Marketplace lub użyj Menedżera rozszerzeń w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fab41-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
