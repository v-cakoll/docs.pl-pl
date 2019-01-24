---
title: Organizowanie projektów programu .NET Framework i .NET Core
description: Pomoc dla właścicieli projektu, którzy chcą Kompiluj swoje rozwiązanie dla platformy .NET Framework i .NET Core side-by-side.
author: conniey
ms.date: 04/06/2017
ms.custom: seodec18
ms.openlocfilehash: 52205a32af212dc74b000025c0e4fc8cde3ae134
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498664"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="fe600-103">Zorganizować projekt do obsługi środowiska .NET Framework i .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe600-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="fe600-104">Dowiedz się, jak utworzyć rozwiązanie, które jest kompilowany dla środowiska .NET Framework i .NET Core side-by-side.</span><span class="sxs-lookup"><span data-stu-id="fe600-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="fe600-105">Zobacz kilka opcji do organizowania projektów, aby pomóc Ci osiągnąć ten cel.</span><span class="sxs-lookup"><span data-stu-id="fe600-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="fe600-106">Poniżej przedstawiono niektóre typowe scenariusze należy wziąć pod uwagę podczas wybierania sposobu konfigurowania układ projektu za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe600-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="fe600-107">Lista nie może obejmować wszystkie potrzebne mu; Ustaw priorytet zależnie od potrzeb Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="fe600-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="fe600-108">[**Łączenie istniejących projektów i projektów .NET Core w jednym projektów**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="fe600-108">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="fe600-109">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="fe600-109">*What this is good for:*</span></span>
  * <span data-ttu-id="fe600-110">Upraszczanie procesu kompilacji, kompilowanie pojedynczego projektu, a nie każdego przeznaczonych dla różnych wersji programu .NET Framework lub platformy kompilacji wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="fe600-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="fe600-111">Upraszczanie zarządzanie plikami źródła dla projektów docelowych multi, ponieważ musisz zarządzać pliku pojedynczego projektu.</span><span class="sxs-lookup"><span data-stu-id="fe600-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="fe600-112">Podczas dodawania/usuwania plików źródłowych, alternatyw wymagają ręcznie zsynchronizować je z innych projektów.</span><span class="sxs-lookup"><span data-stu-id="fe600-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="fe600-113">Łatwe generowanie pakietu NuGet do użycia.</span><span class="sxs-lookup"><span data-stu-id="fe600-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="fe600-114">Umożliwia pisanie kodu dla określonej wersji środowiska .NET Framework w bibliotekach przy użyciu dyrektywy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fe600-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="fe600-115">*Nieobsługiwane scenariusze:*</span><span class="sxs-lookup"><span data-stu-id="fe600-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="fe600-116">Wymaga deweloperzy mogą używać programu Visual Studio 2017 można otworzyć istniejące projekty.</span><span class="sxs-lookup"><span data-stu-id="fe600-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="fe600-117">Do obsługi starszych wersji programu Visual Studio [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="fe600-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="fe600-118">[**Zachowaj istniejące projekty i nowych projektów .NET Core, oddzielne**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="fe600-118">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="fe600-119">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="fe600-119">*What this is good for:*</span></span>
  * <span data-ttu-id="fe600-120">W dalszym ciągu obsługuje programowanie na istniejące projekty bez konieczności aktualizacji dla deweloperów lub współautorzy, którzy nie mają Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fe600-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="fe600-121">Zmniejsza możliwości tworzenia nowych usterek w istniejących projektów, ponieważ postęp dokonany w kodzie jest wymagany w tych projektach.</span><span class="sxs-lookup"><span data-stu-id="fe600-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="fe600-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe600-122">Example</span></span>

<span data-ttu-id="fe600-123">Należy wziąć pod uwagę poniższe repozytorium:</span><span class="sxs-lookup"><span data-stu-id="fe600-123">Consider the repository below:</span></span>

<span data-ttu-id="fe600-124">![Istniejący projekt][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="fe600-124">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="fe600-125">[**Kod źródłowy**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="fe600-125">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="fe600-126">Poniżej przedstawiono kilka sposobów dodawania pomocy technicznej dla platformy .NET Core dla tego repozytorium, w zależności od ograniczeń i złożoność istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="fe600-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="fe600-127">Zamień istniejące projekty projektu .NET Core ukierunkowane na wielu</span><span class="sxs-lookup"><span data-stu-id="fe600-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="fe600-128">Reorganizować tak, aby każda istniejącego repozytorium  *\*.csproj* pliki są usuwane i pojedynczą  *\*.csproj* tworzony jest plik, który jest przeznaczony dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="fe600-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="fe600-129">Jest to doskonałe rozwiązanie, ponieważ jeden projekt jest w stanie kompilowanie dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="fe600-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="fe600-130">Ma również uprawnienia do obsługi opcji różnych kompilacji i zależności dla platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="fe600-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="fe600-131">![Tworzenie pliku csproj, który jest przeznaczony dla wielu platform][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="fe600-131">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="fe600-132">[**Kod źródłowy**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="fe600-132">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="fe600-133">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="fe600-133">Changes to note are:</span></span>

* <span data-ttu-id="fe600-134">Zastąpienie *packages.config* i  *\*.csproj* dzięki nowemu [platformy .NET Core  *\*.csproj* ] [ example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="fe600-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="fe600-135">Pakiety NuGet są określane za pomocą `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="fe600-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="fe600-136">Zachowaj istniejące projekty i utworzyć projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe600-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="fe600-137">W przypadku istniejących projektów przeznaczonych dla platform starszych można pozostawić te projekty w charakterze, a przyszłe ustalać platformy docelowe za pomocą projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe600-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="fe600-138">![Projekt .NET core z istniejącego projektu w innym folderze][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="fe600-138">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="fe600-139">[**Kod źródłowy**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="fe600-139">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="fe600-140">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="fe600-140">Changes to note are:</span></span>

* <span data-ttu-id="fe600-141">.NET Core i istniejące projekty są przechowywane w oddzielnych folderach.</span><span class="sxs-lookup"><span data-stu-id="fe600-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="fe600-142">Utrzymywanie projektów w oddzielnych folderach pozwala uniknąć, co zmuszało do programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fe600-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="fe600-143">Możesz utworzyć oddzielne rozwiązanie, które otwiera tylko starych projektów.</span><span class="sxs-lookup"><span data-stu-id="fe600-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe600-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe600-144">See also</span></span>

* <span data-ttu-id="fe600-145">Zobacz [platformy .NET Core, przenoszenie dokumentacji] [ porting-doc] Aby uzyskać więcej wskazówek na temat migracji do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe600-145">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Istniejący projekt"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Tworzenie pliku csproj, który jest przeznaczony dla wielu platform"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projekt .NET core przy użyciu istniejących PCL w innym folderze"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
