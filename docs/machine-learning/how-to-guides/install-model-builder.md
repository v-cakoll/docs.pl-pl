---
title: Jak zainstalować konstruktora modeli
description: Dowiedz się, jak zainstalować narzędzie konstruktora Model w strukturze ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410651"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="5f2d3-103">Jak zainstalować konstruktora Model w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="5f2d3-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="5f2d3-104">Dowiedz się, jak zainstalować strukturze ML.NET konstruktora modelu można dodać usługi machine learning do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="5f2d3-105">Konstruktor modelu jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="5f2d3-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5f2d3-106">Pre-requisites</span></span>

- <span data-ttu-id="5f2d3-107">Visual Studio 2017 15.9.12 lub nowszej / Visual Studio 2019 r</span><span class="sxs-lookup"><span data-stu-id="5f2d3-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="5f2d3-108">.NET core 2.1 lub nowszej zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="5f2d3-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="5f2d3-109">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="5f2d3-109">Limitations</span></span>

- <span data-ttu-id="5f2d3-110">Rozszerzenia konstruktora modelu strukturze ML.NET obecnie działa tylko w programie Visual Studio na Windows.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="5f2d3-111">Szkolenie zestaw danych limitu 1 GB</span><span class="sxs-lookup"><span data-stu-id="5f2d3-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="5f2d3-112">Program SQL Server ma limit równy 100 tysięcy wierszy szkolenia</span><span class="sxs-lookup"><span data-stu-id="5f2d3-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="5f2d3-113">Microsoft SQL Server Data Tools dla programu Visual Studio 2017 nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="5f2d3-114">Zainstaluj</span><span class="sxs-lookup"><span data-stu-id="5f2d3-114">Install</span></span>

<span data-ttu-id="5f2d3-115">Konstruktor modelu strukturze ML.NET można zainstalować za pośrednictwem witryny Marketplace programu Visual Studio lub z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="5f2d3-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="5f2d3-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="5f2d3-117">Pobieranie z [witryny Marketplace programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="5f2d3-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="5f2d3-118">Postępuj zgodnie z monitami, aby zainstalować na odpowiedniej wersji programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5f2d3-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="5f2d3-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5f2d3-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="5f2d3-120">Na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**</span><span class="sxs-lookup"><span data-stu-id="5f2d3-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="5f2d3-121">Wewnątrz *rozszerzenia i aktualizacje* monit, wybierz opcję *Online* węzła.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-121">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="5f2d3-122">Na pasku wyszukiwania, wyszukaj *konstruktora Model w strukturze ML.NET* z wyników, wybierz strukturze ML.NET konstruktora modeli (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="5f2d3-122">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="5f2d3-123">Postępuj zgodnie z monitami, aby ukończyć instalację</span><span class="sxs-lookup"><span data-stu-id="5f2d3-123">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="5f2d3-124">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="5f2d3-124">Visual Studio 2019</span></span>

1. <span data-ttu-id="5f2d3-125">Na pasku menu wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="5f2d3-125">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="5f2d3-126">Wewnątrz *rozszerzenia i aktualizacje* monit, wybierz opcję *Online* węzła.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-126">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="5f2d3-127">Typ *konstruktora Model w strukturze ML.NET* na pasku wyszukiwania wybierz strukturze ML.NET konstruktora modeli (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="5f2d3-127">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="5f2d3-128">Postępuj zgodnie z monitami, aby ukończyć instalację</span><span class="sxs-lookup"><span data-stu-id="5f2d3-128">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="5f2d3-129">Odinstaluj</span><span class="sxs-lookup"><span data-stu-id="5f2d3-129">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="5f2d3-130">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5f2d3-130">Visual Studio 2017</span></span>

1. <span data-ttu-id="5f2d3-131">Na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**</span><span class="sxs-lookup"><span data-stu-id="5f2d3-131">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="5f2d3-132">Wewnątrz *rozszerzenia i aktualizacje* monit, a następnie rozwiń *zainstalowane* a następnie wybierz węzeł *narzędzia*</span><span class="sxs-lookup"><span data-stu-id="5f2d3-132">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="5f2d3-133">Wybierz Model strukturze ML.NET — Konstruktor (wersja zapoznawcza) z listy narzędzi, a następnie wybierz *dezinstalacji*</span><span class="sxs-lookup"><span data-stu-id="5f2d3-133">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="5f2d3-134">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-134">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="5f2d3-135">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="5f2d3-135">Visual Studio 2019</span></span>

1. <span data-ttu-id="5f2d3-136">Na pasku menu wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**</span><span class="sxs-lookup"><span data-stu-id="5f2d3-136">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="5f2d3-137">Wewnątrz *rozszerzenia i aktualizacje* monit, a następnie rozwiń *zainstalowane* a następnie wybierz węzeł *narzędzia*</span><span class="sxs-lookup"><span data-stu-id="5f2d3-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="5f2d3-138">Wybierz Model strukturze ML.NET — Konstruktor (wersja zapoznawcza) z listy narzędzi, a następnie wybierz *dezinstalacji*</span><span class="sxs-lookup"><span data-stu-id="5f2d3-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="5f2d3-139">Postępuj zgodnie z monitami, aby ukończyć dezinstalację.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-139">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="5f2d3-140">Uaktualnienie</span><span class="sxs-lookup"><span data-stu-id="5f2d3-140">Upgrade</span></span>

<span data-ttu-id="5f2d3-141">Proces uaktualniania jest podobny do procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-141">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="5f2d3-142">Pobierz najnowszą wersję programu Visual Studio Marketplace albo użyj Menedżera rozszerzeń w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f2d3-142">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
