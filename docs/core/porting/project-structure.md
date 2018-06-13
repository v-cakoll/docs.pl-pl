---
title: Organizowanie projektu do obsługi środowiska .NET Framework i .NET Core
description: Pomoc dotyczącą właściciele projektu do skompilowania ich rozwiązanie przed .NET Framework i side-by-side .NET Core.
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.openlocfilehash: e6cd9c6d66996d9fd24fe71d48091723143e5849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211442"
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="36df1-103">Organizowanie projektu do obsługi środowiska .NET Framework i .NET Core</span><span class="sxs-lookup"><span data-stu-id="36df1-103">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="36df1-104">W tym artykule opisano właściciele projektu do skompilowania ich rozwiązanie przed .NET Framework i side-by-side .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36df1-104">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="36df1-105">Zapewnia kilka opcji do organizowania projektów, aby pomóc deweloperom osiągnięcie tego celu.</span><span class="sxs-lookup"><span data-stu-id="36df1-105">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="36df1-106">Poniżej przedstawiono niektóre typowe scenariusze wziąć pod uwagę, gdy jest o wyborze sposobu instalacji układ projektu z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36df1-106">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="36df1-107">Lista nie może obejmować wszystkie potrzebne; priorytet oparte na potrzeby projektu.</span><span class="sxs-lookup"><span data-stu-id="36df1-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="36df1-108">[**Łączenie istniejących projektów i .NET Core projektów w jednym projektów**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="36df1-108">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="36df1-109">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="36df1-109">*What this is good for:*</span></span>
  * <span data-ttu-id="36df1-110">Uproszczenie procesu kompilacji, kompilowanie pojedynczego projektu zamiast kompilowanie wielu projektów każdy przeznaczonych dla różnych wersji programu .NET Framework lub platformy.</span><span class="sxs-lookup"><span data-stu-id="36df1-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="36df1-111">Uproszczenie zarządzania plikami źródła dla projektów docelowe multi, ponieważ muszą zarządzać tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="36df1-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="36df1-112">Podczas dodawania/usuwania plików źródłowych, alternatywnych rozwiązań trzeba ręcznie zsynchronizować je z innych projektów.</span><span class="sxs-lookup"><span data-stu-id="36df1-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="36df1-113">Łatwe generowanie pakietu NuGet zużycia.</span><span class="sxs-lookup"><span data-stu-id="36df1-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="36df1-114">Umożliwia pisanie kodu dla określonej wersji środowiska .NET Framework w bibliotekach przy użyciu dyrektywy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="36df1-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="36df1-115">*Nieobsługiwane scenariusze:*</span><span class="sxs-lookup"><span data-stu-id="36df1-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="36df1-116">Wymaga deweloperom umożliwia otwieranie istniejących projektów Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="36df1-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="36df1-117">Do obsługi starszych wersji programu Visual Studio, [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="36df1-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="36df1-118">[**Zachowaj oddzielne istniejących i nowych projektów .NET Core**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="36df1-118">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="36df1-119">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="36df1-119">*What this is good for:*</span></span>
  * <span data-ttu-id="36df1-120">Kontynuowanie obsługuje programowanie w istniejących projektów bez konieczności aktualizacji dla deweloperów/współautorzy, którzy nie może mieć Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="36df1-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="36df1-121">Zmniejszenie możliwość tworzenia nowych usterek w istniejących projektów, ponieważ postęp dokonany w kodzie jest wymagany w tych projektach.</span><span class="sxs-lookup"><span data-stu-id="36df1-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="36df1-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="36df1-122">Example</span></span>

<span data-ttu-id="36df1-123">Należy wziąć pod uwagę poniższe repozytorium:</span><span class="sxs-lookup"><span data-stu-id="36df1-123">Consider the repository below:</span></span>

<span data-ttu-id="36df1-124">![Istniejący projekt][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="36df1-124">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="36df1-125">[**Kod źródłowy**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="36df1-125">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="36df1-126">Poniżej przedstawiono kilka sposobów, aby dodać obsługę tego repozytorium, w zależności od ograniczeń i złożoność istniejące projekty dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36df1-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="36df1-127">Zamień istniejące projekty docelowe multi projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="36df1-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="36df1-128">Reorganizacja repozytorium, tak aby każda istniejących  *\*.csproj* pliki są usuwane i na jednym  *\*.csproj* tworzony jest plik, który jest przeznaczony dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="36df1-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="36df1-129">Jest to doskonałe rozwiązanie, ponieważ jeden projekt jest w stanie kompilacji dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="36df1-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="36df1-130">Ma również uprawnienia do obsługi opcji różnych kompilacji i zależności na platforma docelowa.</span><span class="sxs-lookup"><span data-stu-id="36df1-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="36df1-131">![Utwórz csproj, przeznaczonego dla wielu struktur][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="36df1-131">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="36df1-132">[**Kod źródłowy**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="36df1-132">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="36df1-133">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="36df1-133">Changes to note are:</span></span>
* <span data-ttu-id="36df1-134">Zastąpienie *packages.config* i  *\*.csproj* o nowe [.NET Core  *\*.csproj* ] [ example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="36df1-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="36df1-135">Pakiety NuGet są określane za pomocą `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="36df1-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="36df1-136">Zachowaj istniejące projekty i tworzenie projektu platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="36df1-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="36df1-137">W przypadku istniejących projektów, które odnoszą się do starszej ramy można pozostawić bez zmian te projekty i przyszłych platform docelowych przy użyciu projektu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36df1-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="36df1-138">![Projekt .NET core z istniejącego projektu w innym folderze][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="36df1-138">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="36df1-139">[**Kod źródłowy**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="36df1-139">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="36df1-140">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="36df1-140">Changes to note are:</span></span>
* <span data-ttu-id="36df1-141">Oprogramowanie .NET Core i istniejące projekty są przechowywane w oddzielnych folderach.</span><span class="sxs-lookup"><span data-stu-id="36df1-141">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="36df1-142">Utrzymywanie projekty w oddzielnych folderach pozwala uniknąć wymuszania posiadania programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="36df1-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="36df1-143">Można utworzyć oddzielnym rozwiązaniu otwartym tylko starych projektów.</span><span class="sxs-lookup"><span data-stu-id="36df1-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="36df1-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36df1-144">See Also</span></span>

<span data-ttu-id="36df1-145">Zobacz [.NET Core eksportowanie dokumentacji] [ porting-doc] Aby uzyskać więcej pomocy na temat migracji do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36df1-145">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Istniejący projekt"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Utwórz csproj, przeznaczonego dla wielu struktur"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Oprogramowanie .NET core projekt z istniejących PCL w innym folderze"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
