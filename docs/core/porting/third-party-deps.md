---
title: Eksportowanie do programu .NET Core — analizowanie zależności innych firm
description: Dowiedz się, jak i analizowanie zależności innych firm w celu portu projekty w programie .NET Framework i .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: 06d8d36d8369680c54af4d16513b2b871b57079c
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44709941"
---
# <a name="analyze-your-third-party-dependencies"></a><span data-ttu-id="912f1-103">Analizowanie zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="912f1-103">Analyze your third-party dependencies</span></span>

<span data-ttu-id="912f1-104">Jeśli szukasz przyłącz kod platformy .NET Core lub .NET Standard, jest pierwszym krokiem w procesie przenoszenia, aby zrozumieć zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="912f1-104">If you're looking to port your code to .NET Core or .NET Standard, the first step in the porting process is to understand your third-party dependencies.</span></span> <span data-ttu-id="912f1-105">Zależności innych firm są albo [pakiety NuGet](#analyze-referenced-nuget-packages-on-your-project) lub [biblioteki dll](#analyze-dependencies-that-arent-nuget-packages) odwołujesz w projekcie.</span><span class="sxs-lookup"><span data-stu-id="912f1-105">Third-party dependencies are either [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you're referencing in your project.</span></span> <span data-ttu-id="912f1-106">Oceń poszczególne zależności i opracować plan awaryjny zależności, które nie są zgodne z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-106">Evaluate each dependency and develop a contingency plan for the dependencies that aren't compatible with .NET Core.</span></span> <span data-ttu-id="912f1-107">W tym artykule pokazano, jak ustalić, czy zależność jest zgodna z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-107">This article shows you how to determine if the dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-project"></a><span data-ttu-id="912f1-108">Analizowanie odwołania pakietów NuGet w swoim projekcie</span><span class="sxs-lookup"><span data-stu-id="912f1-108">Analyze referenced NuGet packages in your project</span></span>

<span data-ttu-id="912f1-109">Jeśli masz odwołujące się do pakietów NuGet w projekcie, należy sprawdzić, jeśli są one zgodne z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-109">If you're referencing NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="912f1-110">Istnieją dwa sposoby, aby to zrobić:</span><span class="sxs-lookup"><span data-stu-id="912f1-110">There are two ways to accomplish that:</span></span>

* <span data-ttu-id="912f1-111">[Za pomocą aplikacji Eksplorator pakietów NuGet](#analyze-nuget-packages-using-nuget-package-explorer) (najbardziej niezawodna metoda).</span><span class="sxs-lookup"><span data-stu-id="912f1-111">[Using the NuGet Package Explorer app](#analyze-nuget-packages-using-nuget-package-explorer) (the most reliable method).</span></span>
* <span data-ttu-id="912f1-112">[Przy użyciu witryny nuget.org](#analyze-nuget-packages-using-nugetorg).</span><span class="sxs-lookup"><span data-stu-id="912f1-112">[Using the nuget.org site](#analyze-nuget-packages-using-nugetorg).</span></span>

<span data-ttu-id="912f1-113">Po przeanalizowaniu pakietów, jeśli tak nie jest zgodny z platformy .NET Core i docelowego środowiska .NET Framework, można sprawdzić Jeśli [.NET Framework w trybie zgodności](#net-framework-compatibility-mode) może pomóc w procesie przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="912f1-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="912f1-114">Analiza pakietów NuGet za pomocą Eksploratora pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="912f1-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="912f1-115">Pakiet NuGet jest zestaw folderów, które zawierają zestawy specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="912f1-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="912f1-116">Zatem należy sprawdzić, czy istnieje folder, który zawiera zestaw zgodnych wewnątrz pakietu.</span><span class="sxs-lookup"><span data-stu-id="912f1-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="912f1-117">Najprostszym sposobem Sprawdź foldery pakietu NuGet jest użycie [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="912f1-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="912f1-118">Po zainstalowaniu, należy użyć następujących kroków, aby wyświetlić nazwy folderów:</span><span class="sxs-lookup"><span data-stu-id="912f1-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="912f1-119">Otwórz Eksplorator pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="912f1-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="912f1-120">Kliknij przycisk **Otwórz pakiet z kanału informacyjnego online**.</span><span class="sxs-lookup"><span data-stu-id="912f1-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="912f1-121">Wyszukaj nazwę pakietu.</span><span class="sxs-lookup"><span data-stu-id="912f1-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="912f1-122">Wybierz nazwę pakietu w wynikach wyszukiwania, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="912f1-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="912f1-123">Rozwiń *lib* folderu na po prawej stronie i spójrz na nazwy folderu.</span><span class="sxs-lookup"><span data-stu-id="912f1-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="912f1-124">Zwróć uwagę na folder z dowolnymi z następujących nazw:</span><span class="sxs-lookup"><span data-stu-id="912f1-124">Look for a folder with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="912f1-125">Te wartości są [Target Framework monikerów (krótkich nazw)](../../standard/frameworks.md) mapowania wersje [.NET Standard](../../standard/net-standard.md), .NET Core i tradycyjne profile biblioteki klas przenośnych (PCL), które są zgodne z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="912f1-126">Po wyświetleniu krótkich nazw, obsługiwanych przez pakiet, należy pamiętać, że `netcoreapp*`, podczas gdy zgodne, jest tylko dla projektów .NET Core, a nie projektów .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="912f1-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="912f1-127">Biblioteki, który jest przeznaczony tylko dla `netcoreapp*` i nie `netstandard*` mogą być używane tylko przez inne aplikacje platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

<span data-ttu-id="912f1-128">Dostępne są także niektóre starsze krótkich nazw używanych w wersji wstępnej wersji programu .NET Core, która może być również zgodna:</span><span class="sxs-lookup"><span data-stu-id="912f1-128">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="912f1-129">Chociaż te krótkich nazw może pracować z kodu, nie ma gwarancji zgodności.</span><span class="sxs-lookup"><span data-stu-id="912f1-129">While these TFMs likely work with your code, there is no guarantee of compatibility.</span></span> <span data-ttu-id="912f1-130">Pakiety za pomocą tych krótkich nazw zostały utworzone za pomocą pakietów .NET Core w wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="912f1-130">Packages with these TFMs were built with pre-release .NET Core packages.</span></span> <span data-ttu-id="912f1-131">Zwróć uwagę na, gdy (lub) pakiety przy użyciu tych krótkich nazw są zaktualizowane pod kątem oparte na .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="912f1-131">Take note of when (or if) packages using these TFMs are updated to be .NET Standard-based.</span></span>

> [!NOTE]
> <span data-ttu-id="912f1-132">Aby użyć pakietu z tradycyjnych aplikacji PCL lub docelowej platformy .NET Core w wersji wstępnej, należy użyć `PackageTargetFallback` elementu MSBuild w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="912f1-132">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `PackageTargetFallback` MSBuild element in your project file.</span></span>
> <span data-ttu-id="912f1-133">Aby uzyskać więcej informacji o tym elemencie programu MSBuild, zobacz [ `PackageTargetFallback` ](../tools/csproj.md#packagetargetfallback).</span><span class="sxs-lookup"><span data-stu-id="912f1-133">For more information about this MSBuild element, see [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="912f1-134">Analizowanie pakietów NuGet za pomocą nuget.org</span><span class="sxs-lookup"><span data-stu-id="912f1-134">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="912f1-135">Możesz również zapoznać się krótkich nazw, obsługiwanych przez każdy pakiet na [nuget.org](https://www.nuget.org/) w obszarze **zależności** części pakietu.</span><span class="sxs-lookup"><span data-stu-id="912f1-135">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="912f1-136">Mimo że za pomocą witryny jest łatwiejszy sposób sprawdzić zgodność, **zależności** informacje nie są dostępne w witrynie dla wszystkich pakietów.</span><span class="sxs-lookup"><span data-stu-id="912f1-136">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="912f1-137">Tryb zgodności w programie .NET framework</span><span class="sxs-lookup"><span data-stu-id="912f1-137">.NET Framework compatibility mode</span></span>

<span data-ttu-id="912f1-138">Po przeanalizowaniu pakietów NuGet, może się okazać że ich tylko dla środowiska .NET Framework, tak jak większość pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="912f1-138">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="912f1-139">Począwszy od .NET Standard 2.0 wprowadzono tryb zgodności w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="912f1-139">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="912f1-140">Ten tryb zgodności umożliwia projektów .NET Standard i .NET Core odwoływać się do bibliotek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="912f1-140">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="912f1-141">Odwołujące się do bibliotek .NET Framework nie działa dla wszystkich projektów, takich jak if biblioteki korzysta z Windows Presentation Foundation (WPF) interfejsów API, ale go odblokować wiele scenariuszy przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="912f1-141">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="912f1-142">Gdy odwołujesz się pakiety NuGet dla środowiska .NET Framework w projekcie, takie jak [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), zostanie wyświetlone ostrzeżenie rezerwowego pakietu ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) podobny do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="912f1-142">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="912f1-143">Tego ostrzeżenie jest wyświetlane, gdy dodasz pakiet za każdym razem, gdy tworzysz, aby upewnić się, testowanie tego pakietu z projektem.</span><span class="sxs-lookup"><span data-stu-id="912f1-143">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="912f1-144">Jeśli projekt działa zgodnie z oczekiwaniami, możesz pominąć tego ostrzeżenia, edytując właściwości pakietu w programie Visual Studio lub ręcznie, edytując plik projektu w wybrany edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="912f1-144">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="912f1-145">Aby pominąć to ostrzeżenie, edytując plik projektu, znaleźć `PackageReference` wpis dla pakietu, którą chcesz pominąć ostrzeżenia dla, a następnie dodaj `NoWarn` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="912f1-145">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="912f1-146">`NoWarn` Atrybutu akceptuje rozdzielaną przecinkami listę wszystkie ostrzeżenia identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="912f1-146">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="912f1-147">Poniższy przykład pokazuje, jak pomijanie `NU1701` ostrzeżenia dla `Huitian.PowerCollections` pakietu, ręcznie edytując plik projektu:</span><span class="sxs-lookup"><span data-stu-id="912f1-147">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="912f1-148">Aby uzyskać więcej informacji na temat sposobu pomijanie ostrzeżeń kompilatora w programie Visual Studio, zobacz [pomijanie ostrzeżeń dla pakietów NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="912f1-148">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="912f1-149">Co zrobić, gdy Twoje zależności pakietów NuGet nie zostanie uruchomiona na platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="912f1-149">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="912f1-150">Istnieje kilka rzeczy, które można zrobić, jeśli pakiet NuGet, których zależysz nie działa na platformie .NET Core:</span><span class="sxs-lookup"><span data-stu-id="912f1-150">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="912f1-151">Jeśli projekt jest typu open source i hostowany takich jak GitHub, deweloperzy mogą angażować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="912f1-151">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="912f1-152">Możesz skontaktować się bezpośrednio na autora [nuget.org](https://www.nuget.org/). Wyszukaj pakiet, a następnie kliknij przycisk **skontaktuj się z właścicielami** po lewej stronie strony pakietu.</span><span class="sxs-lookup"><span data-stu-id="912f1-152">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="912f1-153">Możesz wyszukać inny pakiet, który działa na platformie .NET Core, która w ramach tego samego zadania jako pakiet, który był używany.</span><span class="sxs-lookup"><span data-stu-id="912f1-153">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="912f1-154">Możesz spróbować napisać kod, który pakiet wykonywanych samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="912f1-154">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="912f1-155">Można wyeliminować zależność od pakietu, zmieniając działaniem aplikacji, co najmniej do momentu udostępnienia zgodnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="912f1-155">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="912f1-156">Należy pamiętać, że maintainers projektu open-source i wydawców pakietu NuGet często ochotników.</span><span class="sxs-lookup"><span data-stu-id="912f1-156">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="912f1-157">Przyczyniają się, ponieważ o danej domeny, to zrobić za darmo i często mają różne zadania dziennych.</span><span class="sxs-lookup"><span data-stu-id="912f1-157">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="912f1-158">Dlatego należy w trosce o tym, że podczas kontaktowania się z ich poprosić o obsłudze programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-158">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="912f1-159">Jeśli nie możesz rozwiązać problemu z powyższych elementów, może być konieczne port platformy .NET Core w późniejszym terminie.</span><span class="sxs-lookup"><span data-stu-id="912f1-159">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="912f1-160">Zespół .NET chce wiedzieć, które biblioteki są najważniejsze dla pomocy technicznej za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-160">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="912f1-161">Możesz wysłać wiadomość e-mail na adres dotnet@microsoft.com o bibliotekach, o których chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="912f1-161">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="912f1-162">Analizowanie zależności, które nie są pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="912f1-162">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="912f1-163">Może mieć zależność, która nie jest pakiet NuGet, takich jak biblioteki DLL w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="912f1-163">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="912f1-164">Jedynym sposobem ustalenia przenoszenia tej zależności jest uruchomienie [narzędzia .NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="912f1-164">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="912f1-165">Narzędzie można analizować zestawów, które obsługują program .NET Framework i zidentyfikować interfejsy API, które nie są przenośne na innych platformach .NET, takich jak .NET Core.</span><span class="sxs-lookup"><span data-stu-id="912f1-165">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="912f1-166">Narzędzie można uruchomić jako aplikację konsolową w języku lub [rozszerzenia programu Visual Studio](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="912f1-166">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="912f1-167">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="912f1-167">Next steps</span></span>

<span data-ttu-id="912f1-168">Jeśli masz przenoszenie biblioteki, zapoznaj się z [przenoszenie bibliotek](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="912f1-168">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
