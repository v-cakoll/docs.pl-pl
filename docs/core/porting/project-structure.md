---
title: Organizuj projekty dla .NET Framework i .NET Core
description: Pomoc dla właścicieli projektu, którzy chcą kompilować rozwiązanie względem .NET Framework i .NET Core obok siebie.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 789f50ffb61b80f590a24bc45693df895b3424f7
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801927"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="036e1-103">Organizuj projekt, aby obsługiwał zarówno .NET Framework, jak i .NET Core</span><span class="sxs-lookup"><span data-stu-id="036e1-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="036e1-104">Dowiedz się, jak utworzyć rozwiązanie, które kompiluje zarówno .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="036e1-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="036e1-105">Zobacz kilka opcji, aby zorganizować projekty w celu ułatwienia osiągnięcia tego celu.</span><span class="sxs-lookup"><span data-stu-id="036e1-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="036e1-106">Poniżej przedstawiono kilka typowych scenariuszy, które należy wziąć pod uwagę w przypadku podejmowania decyzji o sposobie konfigurowania układu projektu przy użyciu programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="036e1-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="036e1-107">Lista może nie obejmować wszystkiego, czego potrzebujesz; ustalanie priorytetów w zależności od potrzeb projektu.</span><span class="sxs-lookup"><span data-stu-id="036e1-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="036e1-108">**Połącz istniejące projekty i projekty .NET Core w pojedyncze projekty**</span><span class="sxs-lookup"><span data-stu-id="036e1-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="036e1-109">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="036e1-109">*What this is good for:*</span></span>
  - <span data-ttu-id="036e1-110">Uproszczenie procesu kompilacji przez skompilowanie pojedynczego projektu, a nie kompilowanie wielu projektów, każdy przeznaczony dla innej wersji .NET Framework lub platformy.</span><span class="sxs-lookup"><span data-stu-id="036e1-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="036e1-111">Uproszczenie zarządzania plikami źródłowymi dla projektów wielowymiarowych, ponieważ należy zarządzać pojedynczym plikiem projektu.</span><span class="sxs-lookup"><span data-stu-id="036e1-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="036e1-112">W przypadku dodawania/usuwania plików źródłowych alternatywa wymaga ręcznej synchronizacji z innymi projektami.</span><span class="sxs-lookup"><span data-stu-id="036e1-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="036e1-113">Łatwe generowanie pakietu NuGet do użycia.</span><span class="sxs-lookup"><span data-stu-id="036e1-113">Easily generating a NuGet package for consumption.</span></span>
  - <span data-ttu-id="036e1-114">Umożliwia pisanie kodu dla konkretnej wersji .NET Framework w bibliotekach za pomocą dyrektyw kompilatora.</span><span class="sxs-lookup"><span data-stu-id="036e1-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="036e1-115">*Nieobsługiwane scenariusze:*</span><span class="sxs-lookup"><span data-stu-id="036e1-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="036e1-116">Aby otworzyć istniejące projekty, deweloperzy muszą używać programu Visual Studio 2017 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="036e1-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="036e1-117">Aby można było obsługiwać starsze wersje programu Visual Studio, [zachowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="036e1-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="036e1-118">[**Przechowuj istniejące projekty i nowe projekty .NET Core**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="036e1-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="036e1-119">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="036e1-119">*What this is good for:*</span></span>
  - <span data-ttu-id="036e1-120">Obsługa opracowywania istniejących projektów dla deweloperów i współautorów, którzy nie mają programu Visual Studio w wersji 2017 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="036e1-120">Supporting development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="036e1-121">Zmniejszenie możliwości tworzenia nowych usterek w istniejących projektach, ponieważ w tych projektach nie są wymagane żadne zmiany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="036e1-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="036e1-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="036e1-122">Example</span></span>

<span data-ttu-id="036e1-123">Rozważ następujące repozytorium:</span><span class="sxs-lookup"><span data-stu-id="036e1-123">Consider the repository below:</span></span>

![Istniejący projekt](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="036e1-125">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="036e1-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="036e1-126">Poniżej opisano kilka sposobów dodawania obsługi platformy .NET Core dla tego repozytorium w zależności od ograniczeń i złożoności istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="036e1-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="036e1-127">Zastąp istniejące projekty z wielowymiarowym projektem platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="036e1-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="036e1-128">Uporządkuj repozytorium, aby wszystkie istniejące pliki *\*. csproj* zostały usunięte, a plik *\*. csproj* zostanie utworzony, który jest przeznaczony dla wielu struktur.</span><span class="sxs-lookup"><span data-stu-id="036e1-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="036e1-129">Jest to świetna opcja, ponieważ pojedynczy projekt jest w stanie kompilować dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="036e1-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="036e1-130">Ma także moc do obsługi różnych opcji kompilacji i zależności dla platformy dostosowanej.</span><span class="sxs-lookup"><span data-stu-id="036e1-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Utwórz element csproj, który jest przeznaczony dla wielu struktur](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="036e1-132">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="036e1-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="036e1-133">Zmiany w notatce:</span><span class="sxs-lookup"><span data-stu-id="036e1-133">Changes to note are:</span></span>

- <span data-ttu-id="036e1-134">Zastąpienie elementów *Packages. config* i *\*. csproj* przy użyciu nowego [\*.NET Core *. csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="036e1-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="036e1-135">Pakiety NuGet są określone za pomocą `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="036e1-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="036e1-136">Zachowaj istniejące projekty i Utwórz projekt platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="036e1-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="036e1-137">Jeśli istnieją projekty, które są przeznaczone dla starszych platform, możesz pozostawić te projekty jako nienaruszone i użyć projektu .NET Core, aby określić przyszłe struktury.</span><span class="sxs-lookup"><span data-stu-id="036e1-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projekt .NET Core z istniejącym projektem w innym folderze](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="036e1-139">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="036e1-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="036e1-140">Zmiany w notatce:</span><span class="sxs-lookup"><span data-stu-id="036e1-140">Changes to note are:</span></span>

- <span data-ttu-id="036e1-141">Środowisko .NET Core i istniejące projekty są przechowywane w oddzielnych folderach.</span><span class="sxs-lookup"><span data-stu-id="036e1-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  - <span data-ttu-id="036e1-142">Utrzymywanie projektów w oddzielnych folderach pozwala uniknąć wymuszania programu Visual Studio w wersji 2017 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="036e1-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="036e1-143">Można utworzyć oddzielne rozwiązanie, które otwiera tylko stare projekty.</span><span class="sxs-lookup"><span data-stu-id="036e1-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="036e1-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="036e1-144">See also</span></span>

- [<span data-ttu-id="036e1-145">Dokumentacja dotycząca portów .NET Core</span><span class="sxs-lookup"><span data-stu-id="036e1-145">.NET Core porting documentation</span></span>](index.md)
