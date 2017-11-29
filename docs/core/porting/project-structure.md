---
title: "Organizowanie projektu do obsługi środowiska .NET Framework i .NET Core"
description: "Pomoc dotyczącą właściciele projektu do skompilowania ich rozwiązanie przed .NET Framework i side-by-side .NET Core."
keywords: ".NET, .NET core, .NET Framework, układ projektu, wiele platform"
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.openlocfilehash: 93bec65e3bbee93855d6f5bce5e2d6cea8bb9f3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="ca30a-104">Organizowanie projektu do obsługi środowiska .NET Framework i .NET Core</span><span class="sxs-lookup"><span data-stu-id="ca30a-104">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="ca30a-105">W tym artykule opisano właściciele projektu do skompilowania ich rozwiązanie przed .NET Framework i side-by-side .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ca30a-105">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="ca30a-106">Zapewnia kilka opcji do organizowania projektów, aby pomóc deweloperom osiągnięcie tego celu.</span><span class="sxs-lookup"><span data-stu-id="ca30a-106">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="ca30a-107">Poniżej przedstawiono niektóre typowe scenariusze wziąć pod uwagę, gdy jest o wyborze sposobu instalacji układ projektu z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ca30a-107">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="ca30a-108">Lista nie może obejmować wszystkie potrzebne; priorytet oparte na potrzeby projektu.</span><span class="sxs-lookup"><span data-stu-id="ca30a-108">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="ca30a-109">[**Łączenie istniejących projektów i .NET Core projektów w jednym projektów**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="ca30a-109">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="ca30a-110">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="ca30a-110">*What this is good for:*</span></span>
  * <span data-ttu-id="ca30a-111">Uproszczenie procesu kompilacji, kompilowanie pojedynczego projektu zamiast kompilowanie wielu projektów każdy przeznaczonych dla różnych wersji programu .NET Framework lub platformy.</span><span class="sxs-lookup"><span data-stu-id="ca30a-111">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="ca30a-112">Uproszczenie zarządzania plikami źródła dla projektów docelowe multi, ponieważ muszą zarządzać tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="ca30a-112">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="ca30a-113">Podczas dodawania/usuwania plików źródłowych, alternatywnych rozwiązań trzeba ręcznie zsynchronizować je z innych projektów.</span><span class="sxs-lookup"><span data-stu-id="ca30a-113">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="ca30a-114">Łatwe generowanie pakietu NuGet zużycia.</span><span class="sxs-lookup"><span data-stu-id="ca30a-114">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="ca30a-115">Umożliwia pisanie kodu dla określonej wersji środowiska .NET Framework w bibliotekach przy użyciu dyrektywy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ca30a-115">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="ca30a-116">*Nieobsługiwane scenariusze:*</span><span class="sxs-lookup"><span data-stu-id="ca30a-116">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="ca30a-117">Wymaga deweloperom umożliwia otwieranie istniejących projektów Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="ca30a-117">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="ca30a-118">Do obsługi starszych wersji programu Visual Studio, [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="ca30a-118">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <span data-ttu-id="ca30a-119"><a name="support-vs"></a>[**Zachowaj oddzielne istniejących i nowych projektów .NET Core**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="ca30a-119"><a name="support-vs"></a>[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="ca30a-120">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="ca30a-120">*What this is good for:*</span></span>
  * <span data-ttu-id="ca30a-121">Kontynuowanie obsługuje programowanie w istniejących projektów bez konieczności aktualizacji dla deweloperów/współautorzy, którzy nie może mieć Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="ca30a-121">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="ca30a-122">Zmniejszenie możliwość tworzenia nowych usterek w istniejących projektów, ponieważ postęp dokonany w kodzie jest wymagany w tych projektach.</span><span class="sxs-lookup"><span data-stu-id="ca30a-122">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="ca30a-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca30a-123">Example</span></span>

<span data-ttu-id="ca30a-124">Należy wziąć pod uwagę poniższe repozytorium:</span><span class="sxs-lookup"><span data-stu-id="ca30a-124">Consider the repository below:</span></span>

<span data-ttu-id="ca30a-125">![Istniejący projekt][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="ca30a-125">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="ca30a-126">[**Kod źródłowy**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="ca30a-126">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="ca30a-127">Poniżej przedstawiono kilka sposobów, aby dodać obsługę tego repozytorium, w zależności od ograniczeń i złożoność istniejące projekty dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ca30a-127">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="ca30a-128">Zamień istniejące projekty docelowe multi projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="ca30a-128">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="ca30a-129">Reorganizacja repozytorium, tak aby każda istniejących  *\*.csproj* pliki są usuwane i na jednym  *\*.csproj* tworzony jest plik, który jest przeznaczony dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="ca30a-129">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="ca30a-130">Jest to doskonałe rozwiązanie, ponieważ jeden projekt jest w stanie kompilacji dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="ca30a-130">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="ca30a-131">Ma również uprawnienia do obsługi opcji różnych kompilacji i zależności na platforma docelowa.</span><span class="sxs-lookup"><span data-stu-id="ca30a-131">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="ca30a-132">![Utwórz csproj, przeznaczonego dla wielu struktur][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="ca30a-132">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="ca30a-133">[**Kod źródłowy**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="ca30a-133">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="ca30a-134">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="ca30a-134">Changes to note are:</span></span>
* <span data-ttu-id="ca30a-135">Zastąpienie *packages.config* i  *\*.csproj* o nowe [.NET Core  *\*.csproj* ] [ example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="ca30a-135">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="ca30a-136">Pakiety NuGet są określane za pomocą `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="ca30a-136">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="ca30a-137">Zachowaj istniejące projekty i tworzenie projektu platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ca30a-137">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="ca30a-138">W przypadku istniejących projektów, które odnoszą się do starszej ramy można pozostawić bez zmian te projekty i przyszłych platform docelowych przy użyciu projektu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ca30a-138">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="ca30a-139">![Projekt .NET core z istniejącego projektu w innym folderze][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="ca30a-139">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="ca30a-140">[**Kod źródłowy**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="ca30a-140">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="ca30a-141">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="ca30a-141">Changes to note are:</span></span>
* <span data-ttu-id="ca30a-142">Oprogramowanie .NET Core i istniejące projekty są przechowywane w oddzielnych folderach.</span><span class="sxs-lookup"><span data-stu-id="ca30a-142">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="ca30a-143">Utrzymywanie projekty w oddzielnych folderach pozwala uniknąć wymuszania posiadania programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="ca30a-143">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="ca30a-144">Można utworzyć oddzielnym rozwiązaniu otwartym tylko starych projektów.</span><span class="sxs-lookup"><span data-stu-id="ca30a-144">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca30a-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca30a-145">See Also</span></span>

<span data-ttu-id="ca30a-146">Zobacz [.NET Core eksportowanie dokumentacji] [ porting-doc] Aby uzyskać więcej pomocy na temat migracji do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ca30a-146">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Istniejący projekt"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Utwórz csproj, przeznaczonego dla wielu struktur"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Oprogramowanie .NET core projekt z istniejących PCL w innym folderze"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
