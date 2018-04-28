---
title: Jak zarządzać wersji zależności pakietu dla platformy .NET Core 1.0
description: Więcej informacji na temat zarządzania wersji zależności pakietu dla bibliotek .NET Core i aplikacji.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 7b508f3d83833361bd830bb232587df2ad090661
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="6a7c1-103">Jak zarządzać wersji zależności pakietu dla platformy .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="6a7c1-103">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="6a7c1-104">W tym artykule opisano, co należy wiedzieć o wersji pakietu dla bibliotek .NET Core i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-104">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="6a7c1-105">Słownik</span><span class="sxs-lookup"><span data-stu-id="6a7c1-105">Glossary</span></span>

<span data-ttu-id="6a7c1-106">**Usuń** -ustalania zależności oznacza, że używasz tego samego "rodziny" pakiety wydanej w dniu NuGet dla programu .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-106">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="6a7c1-107">**Metapackage** -pakietu A NuGet, który reprezentuje zestaw pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-107">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="6a7c1-108">**Przycinanie** -oznacza usunięcie pakietów nie zależą od metapackage.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-108">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="6a7c1-109">Jest to coś, które są odpowiednie dla autorów pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-109">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="6a7c1-110">Zobacz [zmniejszenia zależności pakietu z pliku project.json](../deploying/reducing-dependencies.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-110">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="6a7c1-111">Usuń zależności .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="6a7c1-111">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="6a7c1-112">Aby niezawodnie przywracania pakietów i pisanie niezawodnego kodu, ważne jest, aby naprawieniu zależności do wersji pakietów wysyłania obok .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-112">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="6a7c1-113">Oznacza to, że każdy pakiet ma jedną wersję z nie dodatkowych kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-113">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="6a7c1-114">**Przykłady pakietów stałą 1.0**</span><span class="sxs-lookup"><span data-stu-id="6a7c1-114">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="6a7c1-115">**Przykładowe pakiety, które nie zostały usunięte 1.0**</span><span class="sxs-lookup"><span data-stu-id="6a7c1-115">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="6a7c1-116">Dlaczego ta sprawa?</span><span class="sxs-lookup"><span data-stu-id="6a7c1-116">Why does this matter?</span></span>

<span data-ttu-id="6a7c1-117">Firma Microsoft gwarantuje, że jeśli rozwiązać zależności do jakiego jest dostarczany razem .NET Core 1.0, pakiety zostaną współpracują ze sobą.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-117">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="6a7c1-118">Jeśli używasz pakiety, które nie są ustalone w ten sposób jest żadnej gwarancji, takie.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-118">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="6a7c1-119">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="6a7c1-119">Scenarios</span></span>

<span data-ttu-id="6a7c1-120">Ma dużą listę wszystkich pakietów i ich wersje publikowana z .NET Core 1.0, ale nie masz do wyszukiwania przy jego użyciu, jeśli kod znajduje się w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-120">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="6a7c1-121">**Czy zależności tylko w systemie** `NETStandard.Library` **?**</span><span class="sxs-lookup"><span data-stu-id="6a7c1-121">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="6a7c1-122">Jeśli tak, należy naprawić Twojej `NETStandard.Library` pakietu do wersji `1.6`.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-122">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="6a7c1-123">Ponieważ jest to wyselekcjonowanych metapackage, jego zamknięcia pakietu jest również stałą 1.0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-123">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="6a7c1-124">**Czy zależności tylko w systemie** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="6a7c1-124">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="6a7c1-125">Jeśli tak, należy naprawić Twojej `Microsoft.NETCore.App` pakietu do wersji `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-125">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="6a7c1-126">Ponieważ jest to wyselekcjonowanych metapackage, jego zamknięcia pakietu jest również stałą 1.0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-126">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="6a7c1-127">**Czy [przycinanie](../deploying/reducing-dependencies.md) Twojego** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **metapackage zależności?**</span><span class="sxs-lookup"><span data-stu-id="6a7c1-127">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="6a7c1-128">Jeśli tak, należy upewnić się, że metapackage, który jest uruchamiany z jest stałą 1.0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-128">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="6a7c1-129">Indywidualne pakiety, które są zależne od po przycięciu są również stałą 1.0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-129">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="6a7c1-130">**Czy w zależności od pakietów poza** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **metapackages?**</span><span class="sxs-lookup"><span data-stu-id="6a7c1-130">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="6a7c1-131">Jeśli tak, należy rozwiązać zależności do 1,0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-131">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="6a7c1-132">Zobacz wersje pakietów poprawne i numery na końcu tego artykułu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-132">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="6a7c1-133">Uwaga na użycie ciągu splat (\*) podczas kontroli wersji</span><span class="sxs-lookup"><span data-stu-id="6a7c1-133">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="6a7c1-134">Przyjęte wzorzec przechowywania wersji, który używa splat (\*) ciąg następująco: `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-134">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="6a7c1-135">**Nie należy tego robić**.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-135">**You should not do this**.</span></span>  <span data-ttu-id="6a7c1-136">Przy użyciu parametrów splat może spowodować Przywracanie pakietów z różnych kompilacji, z których część może być dalej wzdłuż niż .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-136">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="6a7c1-137">Następnie może to spowodować niektóre pakiety są niezgodne.</span><span class="sxs-lookup"><span data-stu-id="6a7c1-137">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="6a7c1-138">Pakiety i uporządkowane według Metapackage numery wersji</span><span class="sxs-lookup"><span data-stu-id="6a7c1-138">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="6a7c1-139">[Lista wszystkich pakietów .NET Standard i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="6a7c1-139">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="6a7c1-140">[Lista wszystkich pakietów środowiska uruchomieniowego i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="6a7c1-140">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="6a7c1-141">[Lista wszystkich pakietów aplikacji .NET Core i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="6a7c1-141">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
