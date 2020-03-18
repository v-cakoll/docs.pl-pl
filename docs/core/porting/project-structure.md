---
title: Organizowanie projektów dla platform .NET Framework i .NET Core
description: Pomoc dla właścicieli projektów, którzy chcą skompilować swoje rozwiązanie względem .NET Framework i .NET Core side-by-side.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777333"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="ae4c4-103">Organizowanie projektu w celu obsługi programu .NET Framework i programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae4c4-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="ae4c4-104">Można utworzyć rozwiązanie, które kompiluje zarówno .NET Framework i .NET Core side-by-side.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="ae4c4-105">W tym artykule omówiono kilka opcji organizacji projektu, które pomogą Ci osiągnąć ten cel.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="ae4c4-106">Oto kilka typowych scenariuszy, które należy wziąć pod uwagę przy podejmowaniu decyzji, jak skonfigurować układ projektu za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="ae4c4-107">Lista może nie obejmować wszystkiego, co chcesz; priorytetowo w zależności od potrzeb projektu.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="ae4c4-108">**Łączenie istniejących projektów i projektów .NET Core w pojedyncze projekty**</span><span class="sxs-lookup"><span data-stu-id="ae4c4-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="ae4c4-109">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="ae4c4-109">*What this is good for:*</span></span>
  - <span data-ttu-id="ae4c4-110">Upraszcza proces kompilacji przez kompilacji jednego projektu, a nie wiele projektów, które każdy docelowy innej wersji .NET Framework lub platformy.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="ae4c4-111">Upraszcza zarządzanie plikami źródłowymi dla projektów wielokierunkowych, ponieważ należy zarządzać pojedynczym plikiem projektu.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="ae4c4-112">Podczas dodawania lub usuwania plików źródłowych, alternatywy wymagają ręcznej synchronizacji z innymi projektami.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="ae4c4-113">Łatwo wygenerować pakiet NuGet do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="ae4c4-114">Umożliwia pisanie kodu dla określonej wersji .NET Framework w bibliotekach za pomocą dyrektyw kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="ae4c4-115">*Nieobsługiwane scenariusze:*</span><span class="sxs-lookup"><span data-stu-id="ae4c4-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="ae4c4-116">Wymaga od deweloperów użycia programu Visual Studio 2017 lub nowszej wersji do otwierania istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="ae4c4-117">Aby obsługiwać starsze wersje programu Visual Studio, [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="ae4c4-118">[**Oddziel istniejące projekty i nowe projekty .NET Core**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="ae4c4-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="ae4c4-119">*Co to jest dobre dla:*</span><span class="sxs-lookup"><span data-stu-id="ae4c4-119">*What this is good for:*</span></span>
  - <span data-ttu-id="ae4c4-120">Obsługuje tworzenie istniejących projektów dla deweloperów i współpracowników, którzy mogą nie mieć programu Visual Studio 2017 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="ae4c4-121">Zmniejsza możliwość tworzenia nowych błędów w istniejących projektach, ponieważ w tych projektach nie jest wymagany żaden współczynnik zmian kodu.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="ae4c4-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae4c4-122">Example</span></span>

<span data-ttu-id="ae4c4-123">Rozważmy repozytorium poniżej:</span><span class="sxs-lookup"><span data-stu-id="ae4c4-123">Consider the repository below:</span></span>

![Istniejący projekt](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="ae4c4-125">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="ae4c4-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="ae4c4-126">W poniższym artykule opisano kilka sposobów dodawania obsługi programu .NET Core dla tego repozytorium w zależności od ograniczeń i złożoności istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="ae4c4-127">Zastępowanie istniejących projektów wielokierunkowym projektem .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae4c4-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="ae4c4-128">Zreorganizuj repozytorium tak, aby wszystkie istniejące \* \*pliki csproj\* zostały usunięte i utworzony jest pojedynczy \* \*plik csproj,\* który jest przeznaczony dla wielu struktur.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="ae4c4-129">Jest to świetna opcja, ponieważ pojedynczy projekt jest w stanie skompilować dla różnych struktur.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="ae4c4-130">Posiada również możliwość obsługi różnych opcji kompilacji i zależności na ukierunkowane framework.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Tworzenie csproj, który jest przeznaczony dla wielu struktur](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="ae4c4-132">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="ae4c4-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="ae4c4-133">Zmiany w uwagach to:</span><span class="sxs-lookup"><span data-stu-id="ae4c4-133">Changes to note are:</span></span>

- <span data-ttu-id="ae4c4-134">Wymiana *packages.config* i \* \*.csproj\* na nowy [.NET Core \* \*.csproj\*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="ae4c4-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="ae4c4-135">Pakiety NuGet są `<PackageReference> ItemGroup`określone za pomocą .</span><span class="sxs-lookup"><span data-stu-id="ae4c4-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="ae4c4-136">Zachowaj istniejące projekty i utwórz projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae4c4-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="ae4c4-137">Jeśli istnieją projekty, które są przeznaczone dla starszych struktur, można pozostawić te projekty nietknięte i użyć projektu .NET Core do docelowych przyszłych struktur.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projekt .NET Core z istniejącym projektem w innym folderze](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="ae4c4-139">**Kod źródłowy**</span><span class="sxs-lookup"><span data-stu-id="ae4c4-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="ae4c4-140">.NET Core i istniejące projekty są przechowywane w oddzielnych folderach.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="ae4c4-141">Przechowywanie projektów w oddzielnych folderach pozwala uniknąć zmuszania do programu Visual Studio 2017 lub nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="ae4c4-142">Można utworzyć oddzielne rozwiązanie, które otwiera tylko stare projekty.</span><span class="sxs-lookup"><span data-stu-id="ae4c4-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae4c4-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae4c4-143">See also</span></span>

- [<span data-ttu-id="ae4c4-144">Dokumentacja przenoszenia programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae4c4-144">.NET Core porting documentation</span></span>](index.md)
