---
title: Organizowanie projektów programu .NET Framework i .NET Core
description: Pomoc dla właścicieli projektu, którzy chcą Kompiluj swoje rozwiązanie dla platformy .NET Framework i .NET Core side-by-side.
author: conniey
ms.date: 04/06/2017
ms.custom: seodec18
ms.openlocfilehash: 0ea82e6ebbeeb52a2f77bc3260eeae2972ebeff1
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825423"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="a5b32-103">Zorganizować projekt do obsługi środowiska .NET Framework i .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5b32-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="a5b32-104">Dowiedz się, jak utworzyć rozwiązanie, które jest kompilowany dla środowiska .NET Framework i .NET Core side-by-side.</span><span class="sxs-lookup"><span data-stu-id="a5b32-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="a5b32-105">Zobacz kilka opcji do organizowania projektów, aby pomóc Ci osiągnąć ten cel.</span><span class="sxs-lookup"><span data-stu-id="a5b32-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="a5b32-106">Poniżej przedstawiono niektóre typowe scenariusze należy wziąć pod uwagę podczas wybierania sposobu konfigurowania układ projektu za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b32-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="a5b32-107">Lista nie może obejmować wszystkie potrzebne mu; Ustaw priorytet zależnie od potrzeb Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="a5b32-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* [<span data-ttu-id="a5b32-108">**Łączenie istniejących projektów i projektów .NET Core w jednym projektów**</span><span class="sxs-lookup"><span data-stu-id="a5b32-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="a5b32-109">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="a5b32-109">*What this is good for:*</span></span>
  * <span data-ttu-id="a5b32-110">Upraszczanie procesu kompilacji, kompilowanie pojedynczego projektu, a nie każdego przeznaczonych dla różnych wersji programu .NET Framework lub platformy kompilacji wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="a5b32-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="a5b32-111">Upraszczanie zarządzanie plikami źródła dla projektów docelowych multi, ponieważ musisz zarządzać pliku pojedynczego projektu.</span><span class="sxs-lookup"><span data-stu-id="a5b32-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="a5b32-112">Podczas dodawania/usuwania plików źródłowych, alternatyw wymagają ręcznie zsynchronizować je z innych projektów.</span><span class="sxs-lookup"><span data-stu-id="a5b32-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="a5b32-113">Łatwe generowanie pakietu NuGet do użycia.</span><span class="sxs-lookup"><span data-stu-id="a5b32-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="a5b32-114">Umożliwia pisanie kodu dla określonej wersji środowiska .NET Framework w bibliotekach przy użyciu dyrektywy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a5b32-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="a5b32-115">*Nieobsługiwane scenariusze:*</span><span class="sxs-lookup"><span data-stu-id="a5b32-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="a5b32-116">Wymaga deweloperzy mogą używać programu Visual Studio 2017 można otworzyć istniejące projekty.</span><span class="sxs-lookup"><span data-stu-id="a5b32-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="a5b32-117">Do obsługi starszych wersji programu Visual Studio [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="a5b32-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="a5b32-118">[**Zachowaj istniejące projekty i nowych projektów .NET Core, oddzielne**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="a5b32-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="a5b32-119">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="a5b32-119">*What this is good for:*</span></span>
  * <span data-ttu-id="a5b32-120">W dalszym ciągu obsługuje programowanie na istniejące projekty bez konieczności aktualizacji dla deweloperów lub współautorzy, którzy nie mają Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a5b32-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="a5b32-121">Zmniejsza możliwości tworzenia nowych usterek w istniejących projektów, ponieważ postęp dokonany w kodzie jest wymagany w tych projektach.</span><span class="sxs-lookup"><span data-stu-id="a5b32-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="a5b32-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5b32-122">Example</span></span>

<span data-ttu-id="a5b32-123">Należy wziąć pod uwagę poniższe repozytorium:</span><span class="sxs-lookup"><span data-stu-id="a5b32-123">Consider the repository below:</span></span>

![Istniejący projekt](media/project-structure/project.png)

[<span data-ttu-id="a5b32-125">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="a5b32-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="a5b32-126">Poniżej przedstawiono kilka sposobów dodawania pomocy technicznej dla platformy .NET Core dla tego repozytorium, w zależności od ograniczeń i złożoność istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="a5b32-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="a5b32-127">Zamień istniejące projekty projektu .NET Core ukierunkowane na wielu</span><span class="sxs-lookup"><span data-stu-id="a5b32-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="a5b32-128">Reorganizować tak, aby każda istniejącego repozytorium  *\*.csproj* pliki są usuwane i pojedynczą  *\*.csproj* tworzony jest plik, który jest przeznaczony dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="a5b32-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="a5b32-129">Jest to doskonałe rozwiązanie, ponieważ jeden projekt jest w stanie kompilowanie dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="a5b32-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="a5b32-130">Ma również uprawnienia do obsługi opcji różnych kompilacji i zależności dla platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="a5b32-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Tworzenie pliku csproj, który jest przeznaczony dla wielu platform](media/project-structure/project.csproj.png)

[<span data-ttu-id="a5b32-132">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="a5b32-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="a5b32-133">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="a5b32-133">Changes to note are:</span></span>

* <span data-ttu-id="a5b32-134">Zastąpienie *packages.config* i  *\*.csproj* dzięki nowemu [platformy .NET Core  *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="a5b32-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="a5b32-135">Pakiety NuGet są określane za pomocą `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="a5b32-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="a5b32-136">Zachowaj istniejące projekty i utworzyć projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5b32-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="a5b32-137">W przypadku istniejących projektów przeznaczonych dla platform starszych można pozostawić te projekty w charakterze, a przyszłe ustalać platformy docelowe za pomocą projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b32-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projekt .NET core z istniejącego projektu w innym folderze](media/project-structure/project.csproj.different.png)

[<span data-ttu-id="a5b32-139">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="a5b32-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="a5b32-140">Zmiany, należy pamiętać, są następujące:</span><span class="sxs-lookup"><span data-stu-id="a5b32-140">Changes to note are:</span></span>

* <span data-ttu-id="a5b32-141">.NET Core i istniejące projekty są przechowywane w oddzielnych folderach.</span><span class="sxs-lookup"><span data-stu-id="a5b32-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="a5b32-142">Utrzymywanie projektów w oddzielnych folderach pozwala uniknąć, co zmuszało do programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a5b32-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="a5b32-143">Możesz utworzyć oddzielne rozwiązanie, które otwiera tylko starych projektów.</span><span class="sxs-lookup"><span data-stu-id="a5b32-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5b32-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5b32-144">See also</span></span>

<span data-ttu-id="a5b32-145">Zobacz [platformy .NET Core, przenoszenie dokumentacji](index.md) Aby uzyskać więcej wskazówek na temat migracji do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b32-145">Please see the [.NET Core porting documentation](index.md) for more guidance on migrating to .NET Core.</span></span>
