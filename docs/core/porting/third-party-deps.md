---
title: Analizowanie zależności w kodzie portu do programu .NET Core
description: Dowiedz się, jak analizować zależności zewnętrzne w celu przenoszenia projektu z .NET Framework do programu .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521472"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="1ec5f-103">Analizowanie zależności w kodzie portu do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="1ec5f-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="1ec5f-104">Aby przenieść kod do programu .NET Core lub .NET Standard, musisz zrozumieć zależności.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="1ec5f-105">Zależności zewnętrzne to [pakiety NuGet](#analyze-referenced-nuget-packages-in-your-projects) lub [biblioteki DLL](#analyze-dependencies-that-arent-nuget-packages) , do których odwołuje się w projekcie, ale nie są kompilowane.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-105">External dependencies are the [NuGet packages](#analyze-referenced-nuget-packages-in-your-projects) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you reference in your project, but that you don't build.</span></span> <span data-ttu-id="1ec5f-106">Oceń każdą zależność i opracowuj plan awaryjny dla tych, które nie są zgodne z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-106">Evaluate each dependency and develop a contingency plan for the ones that aren't compatible with .NET Core.</span></span> <span data-ttu-id="1ec5f-107">Oto jak ustalić, czy zależność jest zgodna z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-107">Here's how to determine if a dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a><span data-ttu-id="1ec5f-108">Analizowanie przywoływanych pakietów NuGet w projektach</span><span class="sxs-lookup"><span data-stu-id="1ec5f-108">Analyze referenced NuGet packages in your projects</span></span>

<span data-ttu-id="1ec5f-109">W przypadku odwoływania się do pakietów NuGet w projekcie należy sprawdzić, czy są one zgodne z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-109">If you reference NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="1ec5f-110">Istnieją dwa sposoby osiągnięcia tego:</span><span class="sxs-lookup"><span data-stu-id="1ec5f-110">There are two ways to accomplish that:</span></span>

- [<span data-ttu-id="1ec5f-111">Korzystanie z aplikacji Eksplorator pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="1ec5f-111">Using the NuGet Package Explorer app</span></span>](#analyze-nuget-packages-using-nuget-package-explorer)
- [<span data-ttu-id="1ec5f-112">Korzystanie z witryny nuget.org</span><span class="sxs-lookup"><span data-stu-id="1ec5f-112">Using the nuget.org site</span></span>](#analyze-nuget-packages-using-nugetorg)

<span data-ttu-id="1ec5f-113">Po przeanalizowaniu pakietów, jeśli nie są zgodne z platformą .NET Core i są przeznaczone tylko dla .NET Framework, można sprawdzić, czy [.NET Framework tryb zgodności](#net-framework-compatibility-mode) może ułatwić proces przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="1ec5f-114">Analizowanie pakietów NuGet przy użyciu Eksploratora pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="1ec5f-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="1ec5f-115">Pakiet NuGet jest samym zestawem folderów, które zawierają zestawy specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="1ec5f-116">Należy sprawdzić, czy w pakiecie znajduje się folder zawierający zgodny zestaw.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="1ec5f-117">Najprostszym sposobem sprawdzenia folderów pakietów NuGet jest użycie narzędzia [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) .</span><span class="sxs-lookup"><span data-stu-id="1ec5f-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="1ec5f-118">Po zainstalowaniu programu wykonaj następujące kroki, aby wyświetlić nazwy folderów:</span><span class="sxs-lookup"><span data-stu-id="1ec5f-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="1ec5f-119">Otwórz Eksploratora pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="1ec5f-120">Kliknij pozycję **Otwórz pakiet ze źródła online**.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="1ec5f-121">Wyszukaj nazwę pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="1ec5f-122">Wybierz nazwę pakietu z wyników wyszukiwania, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="1ec5f-123">Rozwiń folder *lib* po prawej stronie i Sprawdź nazwy folderów.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="1ec5f-124">Poszukaj folderu z dowolną z następujących nazw:</span><span class="sxs-lookup"><span data-stu-id="1ec5f-124">Look for a folder with any of the following names:</span></span>

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
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="1ec5f-125">Te wartości są [monikerami struktury docelowej (TFMs)](../../standard/frameworks.md) , które są mapowane na wersje [.NET Standard](../../standard/net-standard.md), .NET Core i tradycyjnych profilów biblioteki klas przenośnych (PCL), które są zgodne z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ec5f-126">Podczas przeglądania TFMs, który obsługuje pakiet, należy pamiętać, że `netcoreapp*`, chociaż jest zgodny, jest przeznaczony tylko dla projektów .NET Core, a nie dla projektów .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="1ec5f-127">Biblioteka przeznaczona tylko dla `netcoreapp*` i nie `netstandard*` może być używana przez inne aplikacje platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="1ec5f-128">Analizowanie pakietów NuGet przy użyciu nuget.org</span><span class="sxs-lookup"><span data-stu-id="1ec5f-128">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="1ec5f-129">Alternatywnie można zobaczyć TFMs, że każdy pakiet obsługuje w [NuGet.org](https://www.nuget.org/) w sekcji **zależności** strony pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-129">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="1ec5f-130">Chociaż korzystanie z lokacji jest łatwiejsze w celu sprawdzenia zgodności, informacje o **zależnościach** nie są dostępne w lokacji dla wszystkich pakietów.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-130">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="1ec5f-131">.NET Framework tryb zgodności</span><span class="sxs-lookup"><span data-stu-id="1ec5f-131">.NET Framework compatibility mode</span></span>

<span data-ttu-id="1ec5f-132">Po przeanalizowaniu pakietów NuGet może się okazać, że są one przeznaczone tylko do .NET Framework, jak większość pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-132">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="1ec5f-133">Począwszy od .NET Standard 2,0, wprowadzono .NET Framework tryb zgodności.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-133">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="1ec5f-134">Ten tryb zgodności umożliwia projektom .NET Standard i .NET Core odwoływanie się do bibliotek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-134">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="1ec5f-135">Odwoływanie się do bibliotek .NET Framework nie działa dla wszystkich projektów, takich jak jeśli biblioteka używa interfejsów API Windows Presentation Foundation (WPF), ale odblokowuje wiele scenariuszy przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-135">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="1ec5f-136">W przypadku odwoływania się do pakietów NuGet, które są przeznaczone dla .NET Framework w projekcie, takich jak [Huitian. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), otrzymujesz ostrzeżenie powrotu do pakietu ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="1ec5f-136">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="1ec5f-137">To ostrzeżenie jest wyświetlane, gdy dodajesz pakiet i za każdym razem, gdy kompilujesz, aby upewnić się, że ten pakiet został przetestowany z projektem.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-137">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="1ec5f-138">Jeśli projekt działa zgodnie z oczekiwaniami, możesz pominąć to ostrzeżenie, edytując właściwości pakietu w Visual Studio lub edytując plik projektu ręcznie w ulubionym edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-138">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="1ec5f-139">Aby pominąć ostrzeżenie przez edytowanie pliku projektu, Znajdź wpis `PackageReference` dla pakietu, dla którego chcesz pominąć ostrzeżenie, i Dodaj atrybut `NoWarn`.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-139">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="1ec5f-140">Atrybut `NoWarn` akceptuje rozdzieloną przecinkami listę wszystkich identyfikatorów ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-140">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="1ec5f-141">Poniższy przykład pokazuje, jak pominąć `NU1701` Ostrzeżenie dla pakietu `Huitian.PowerCollections`, edytując plik projektu ręcznie:</span><span class="sxs-lookup"><span data-stu-id="1ec5f-141">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="1ec5f-142">Aby uzyskać więcej informacji na temat pomijania ostrzeżeń kompilatora w programie Visual Studio, zobacz [pomijanie ostrzeżeń dla pakietów NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="1ec5f-142">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span></span>

## <a name="port-your-packages-to-packagereference"></a><span data-ttu-id="1ec5f-143">Przenoszenie pakietów do `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="1ec5f-143">Port your packages to `PackageReference`</span></span>

<span data-ttu-id="1ec5f-144">Program .NET Core używa [PackageReference](/nuget/consume-packages/package-references-in-project-files) , aby określić zależności pakietów.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-144">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="1ec5f-145">Jeśli używasz [pliku Packages. config](/nuget/reference/packages-config) do określania pakietów, musisz przekonwertować go na `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-145">If you are using [packages.config](/nuget/reference/packages-config) to specify your packages, you will need to convert over to `PackageReference`.</span></span>

<span data-ttu-id="1ec5f-146">Więcej informacji można znaleźć w części [Migrowanie z pliku Packages. config do PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="1ec5f-146">You can learn more at [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span></span>

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="1ec5f-147">Co zrobić, gdy zależność pakietu NuGet nie jest uruchamiana na platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="1ec5f-147">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="1ec5f-148">Istnieje kilka rzeczy, które można wykonać, jeśli pakiet NuGet, od którego jest zależny, nie jest uruchamiany w programie .NET Core:</span><span class="sxs-lookup"><span data-stu-id="1ec5f-148">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="1ec5f-149">Jeśli projekt jest typu open source, który jest hostowany w witrynie GitHub, możesz bezpośrednio przyangażować deweloperów.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-149">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="1ec5f-150">Można skontaktować się z autorem bezpośrednio w witrynie [NuGet.org](https://www.nuget.org/). Wyszukaj pakiet, a następnie kliknij pozycję **skontaktuj się z właścicielem** po lewej stronie pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-150">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="1ec5f-151">Możesz wyszukać inny pakiet uruchomiony w programie .NET Core, który wykonuje to samo zadanie co używany pakiet.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-151">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="1ec5f-152">Możesz spróbować napisać kod, który pakiet wykonywał.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-152">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="1ec5f-153">Możesz wyeliminować zależność od pakietu, zmieniając funkcjonalność aplikacji, co najmniej do momentu udostępnienia zgodnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-153">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="1ec5f-154">Pamiętaj, że obsłudze projektów open source i wydawcy pakietów NuGet często są ochotnikami.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-154">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="1ec5f-155">Przyczyniają się one do tego, że zadbają o daną domenę, wykonują ją bezpłatnie i często mają inne zadania dzienne.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-155">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="1ec5f-156">Należy więc wiedzieć, że podczas kontaktowania się z nimi w celu uzyskania pomocy technicznej dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-156">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="1ec5f-157">Jeśli nie możesz rozwiązać problemu przy użyciu któregokolwiek z powyższych, być może trzeba będzie przenieść port do programu .NET Core w późniejszym terminie.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-157">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="1ec5f-158">Zespół platformy .NET chce wiedzieć, które biblioteki są najważniejsze do obsługi platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-158">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="1ec5f-159">Możesz wysłać wiadomość e-mail w celu dotnet@microsoft.com informacji o bibliotekach, których chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-159">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="1ec5f-160">Analizowanie zależności, które nie są pakietami NuGet</span><span class="sxs-lookup"><span data-stu-id="1ec5f-160">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="1ec5f-161">Może istnieć zależność, która nie jest pakietem NuGet, taka jak biblioteka DLL w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-161">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="1ec5f-162">Jedynym sposobem określenia przenośności tej zależności jest uruchomienie narzędzia [analizatora przenośności platformy .NET](https://github.com/Microsoft/dotnet-apiport) .</span><span class="sxs-lookup"><span data-stu-id="1ec5f-162">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="1ec5f-163">Narzędzie może analizować zestawy przeznaczone dla .NET Framework i identyfikować interfejsy API, które nie są przenośne na inne platformy .NET, takie jak .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ec5f-163">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="1ec5f-164">Narzędzie można uruchomić jako aplikację konsolową lub jako [rozszerzenie programu Visual Studio](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="1ec5f-164">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="1ec5f-165">Next</span><span class="sxs-lookup"><span data-stu-id="1ec5f-165">Next</span></span>](libraries.md)
