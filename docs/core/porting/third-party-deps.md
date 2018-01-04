---
title: "Eksportowanie do platformy .NET Core - analizowanie zależności innych firm"
description: "Eksportowanie do platformy .NET Core - analizowanie zależności innych firm"
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a><span data-ttu-id="8ee21-104">Eksportowanie do platformy .NET Core - analizowanie zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="8ee21-104">Porting to .NET Core - Analyzing your Third-Party Party Dependencies</span></span>

<span data-ttu-id="8ee21-105">Pierwszym krokiem w procesie przenoszenia jest zrozumienie zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="8ee21-105">The first step in the porting process is to understand your third party dependencies.</span></span>  <span data-ttu-id="8ee21-106">Należy sprawdzić, który z nich, jeśli istnieje, nie jeszcze Uruchom na .NET Core i opracowanie planu gotowości do tych, które nie działają na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ee21-106">You need to figure out which of them, if any, don't yet run on .NET Core, and develop a contingency plan for those which don't run on .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ee21-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8ee21-107">Prerequisites</span></span>

<span data-ttu-id="8ee21-108">W tym artykule przyjmie korzystasz z systemu Windows i programu Visual Studio i czy masz kod, który obecnie jest uruchamiana w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ee21-108">This article will assume you are using Windows and Visual Studio, and that you have code which runs on the .NET Framework today.</span></span>

## <a name="analyzing-nuget-packages"></a><span data-ttu-id="8ee21-109">Analiza pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="8ee21-109">Analyzing NuGet Packages</span></span>

<span data-ttu-id="8ee21-110">Analiza pakietów NuGet przenośności jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="8ee21-110">Analyzing NuGet packages for portability is very easy.</span></span>  <span data-ttu-id="8ee21-111">Pakiet NuGet jest zestaw folderów, które zawierają zestawy specyficzne dla platformy, musisz wykonać jest sprawdzenie, czy jest folder, który zawiera zestaw .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ee21-111">Because a NuGet package is itself a set of folders which contain platform-specific assemblies, all you have to do is check to see if there is a folder which contains a .NET Core assembly.</span></span>

<span data-ttu-id="8ee21-112">Pakiet NuGet folderach najłatwiej z [Explorer pakietu NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="8ee21-112">Inspecting NuGet Package folders is easiest with the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span>  <span data-ttu-id="8ee21-113">Oto jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="8ee21-113">Here's how to do it.</span></span>

1. <span data-ttu-id="8ee21-114">Pobierz i Otwórz Eksploratora pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="8ee21-114">Download and open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="8ee21-115">Kliknij przycisk "Otwórz pakiet ze strumieniowego źródła online".</span><span class="sxs-lookup"><span data-stu-id="8ee21-115">Click "Open package from online feed".</span></span>
3. <span data-ttu-id="8ee21-116">Wyszukaj nazwę pakietu.</span><span class="sxs-lookup"><span data-stu-id="8ee21-116">Search for the name of the package.</span></span>
4. <span data-ttu-id="8ee21-117">Rozwiń węzeł folderu "lib" po prawej stronie i przyjrzyj się nazwy folderów.</span><span class="sxs-lookup"><span data-stu-id="8ee21-117">Expand the "lib" folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="8ee21-118">Możesz również sprawdzić pakietu obsługuje na [nuget.org](https://www.nuget.org/) w obszarze **zależności** sekcji strony dla tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8ee21-118">You can also see what a package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the page for that package.</span></span>

<span data-ttu-id="8ee21-119">W obu przypadkach należy szukać folder lub wpis [nuget.org](https://www.nuget.org/) za pomocą dowolnego z następujących nazw:</span><span class="sxs-lookup"><span data-stu-id="8ee21-119">In either case, you'll need to look for a folder or entry on [nuget.org](https://www.nuget.org/) with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="8ee21-120">Są to docelowej Framework monikerów (TFM), które mapują do wersji [.NET Standard](../../standard/net-standard.md) i tradycyjnych profile przenośnej biblioteki klasy (PCL), które są zgodne z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ee21-120">These are the Target Framework Monikers (TFM) which map to versions of the [.NET Standard](../../standard/net-standard.md) and traditional Portable Class Library (PCL) profiles which are compatible with .NET Core.</span></span>  <span data-ttu-id="8ee21-121">Należy pamiętać, że `netcoreapp1.0`, podczas zgodny, jest dla aplikacji i nie bibliotek.</span><span class="sxs-lookup"><span data-stu-id="8ee21-121">Note that `netcoreapp1.0`, while compatible, is for applications and not libraries.</span></span>  <span data-ttu-id="8ee21-122">Mimo że nie ma problem z za pomocą biblioteki, który jest `netcoreapp1.0`— na podstawie, biblioteki mogą nie być przeznaczone do wszelkich *innych* niż użycie przez inne `netcoreapp1.0` aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ee21-122">Although there's nothing wrong with using a library which is `netcoreapp1.0`-based, that library may not be intended for anything *other* than consumption by other `netcoreapp1.0` applications.</span></span>

<span data-ttu-id="8ee21-123">Dostępne są również niektórych starszych TFMs używane w wersji wstępnych programu .NET Core, które mogą być niezgodne:</span><span class="sxs-lookup"><span data-stu-id="8ee21-123">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="8ee21-124">**Gdy te prawdopodobnie będzie działać w kodzie, nie ma żadnej gwarancji zgodności**.</span><span class="sxs-lookup"><span data-stu-id="8ee21-124">**While these will likely work with your code, there is no guarantee of compatibility**.</span></span>  <span data-ttu-id="8ee21-125">Pakiety z tych TFMs zostały skompilowane z pakietami .NET Core wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="8ee21-125">Packages with these TFMs were built with pre-release .NET Core packages.</span></span>  <span data-ttu-id="8ee21-126">Zwróć uwagę, gdy (lub) pakiety takie zostaną zaktualizowane, aby być `netstandard`— na podstawie.</span><span class="sxs-lookup"><span data-stu-id="8ee21-126">Take note of when (or if) packages like this are updated to be `netstandard`-based.</span></span>

> [!NOTE]
> <span data-ttu-id="8ee21-127">Pakiet tradycyjnych PCL lub docelowej platformy .NET Core wersji wstępnej, możesz korzystać `imports` dyrektywy w Twojej `project.json` pliku.</span><span class="sxs-lookup"><span data-stu-id="8ee21-127">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `imports` directive in your `project.json` file.</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="8ee21-128">Co robić, jeśli zależność pakietu NuGet nie działa na .NET Core</span><span class="sxs-lookup"><span data-stu-id="8ee21-128">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="8ee21-129">Istnieje kilka rzeczy, które można wykonać, gdy nie można uruchomić pakietu NuGet, które zależą od platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ee21-129">There are a few things you can do if a NuGet package you depend on won't run on .NET Core.</span></span>

1. <span data-ttu-id="8ee21-130">Projekt jest typu open source, takie jak GitHub hostowany developer(s) może prowadzić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8ee21-130">If the project is open source and hosted somewhere like GitHub, you can engage the developer(s) directly.</span></span>
2. <span data-ttu-id="8ee21-131">Można skontaktować się z autorem bezpośrednio na [nuget.org](https://www.nuget.org/) wyszukiwania dla pakietu, a następnie klikając polecenie "Skontaktuj się z właścicieli" po stronie lewej strony pakietu.</span><span class="sxs-lookup"><span data-stu-id="8ee21-131">You can contact the author directly on [nuget.org](https://www.nuget.org/) by searching for the package and clicking "Contact Owners" on the left hand side of the package's page.</span></span>
3. <span data-ttu-id="8ee21-132">Można wyszukać inny pakiet, który działa na .NET Core, które wykonuje to samo zadanie pakietu, który był używany.</span><span class="sxs-lookup"><span data-stu-id="8ee21-132">You can look for another package that runs on .NET Core which accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="8ee21-133">Możesz spróbować pisanie kodu, że pakiet wykonywanych samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="8ee21-133">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="8ee21-134">Zależność od pakietu można wyeliminować, zmieniając funkcji aplikacji, co najmniej do momentu udostępnienia zgodnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="8ee21-134">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="8ee21-135">Należy pamiętać, że maintainers projekt typu open source i wydawców pakietu NuGet są często ochotników, którzy przyczyniają się, ponieważ interesujących danej domeny, należy go bezpłatnie i często mają różne zadania dziennych.</span><span class="sxs-lookup"><span data-stu-id="8ee21-135">Please remember that open source project maintainers and NuGet package publishers are often volunteers who contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="8ee21-136">Jeśli przejdziesz może rozpoczynać się od instrukcji dodatnią informacje o bibliotece przed pytaniem o obsłudze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ee21-136">If you do reach out, you might start with a positive statement about the library before asking about .NET Core support.</span></span>

<span data-ttu-id="8ee21-137">Jeśli nie uda się rozwiązać problem z żadnym z powyższych, może być konieczne port .NET Core w późniejszym terminie.</span><span class="sxs-lookup"><span data-stu-id="8ee21-137">If you're unable to resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="8ee21-138">Zespół .NET chcesz dowiedzieć się, które biblioteki są najważniejsze obsługuje next z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ee21-138">The .NET Team would like to know which libraries are the most important to support next with .NET Core.</span></span> <span data-ttu-id="8ee21-139">Możesz również wysłać nam poczty na dotnet@microsoft.com o bibliotekach chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="8ee21-139">You can also send us mail at dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a><span data-ttu-id="8ee21-140">Analizowanie zależności, które nie są pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="8ee21-140">Analyzing Dependencies which aren't NuGet Packages</span></span>

<span data-ttu-id="8ee21-141">Może mieć zależności, która nie jest pakietem NuGet, takich jak biblioteki DLL w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="8ee21-141">You may have a dependency that isn't a NuGet package, such as a DLL in the filesystem.</span></span>  <span data-ttu-id="8ee21-142">Jedynym sposobem, aby określić przenośność Zależność ta jest uruchomienie [narzędzie ApiPort](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span><span class="sxs-lookup"><span data-stu-id="8ee21-142">The only way to determine the portability of that dependency is to run the [ApiPort tool](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8ee21-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8ee21-143">Next steps</span></span>

<span data-ttu-id="8ee21-144">Jeśli w przypadku przenoszenia biblioteki, zapoznaj się [eksportowanie bibliotek](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="8ee21-144">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
