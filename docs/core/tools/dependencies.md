---
title: Zarządzanie zależnościami w narzędziu .NET Core
description: Wyjaśnia, jak zarządzać zależnościami przy użyciu narzędzi programu .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 28280dc05e746cdef4e90870cd4cb528382c45bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787862"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="7e6b1-103">Zarządzanie zależnościami przy użyciu zestaw .NET Core SDK 1,0</span><span class="sxs-lookup"><span data-stu-id="7e6b1-103">Manage dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="7e6b1-104">Po przeniesieniu projektów platformy .NET Core z pliku Project. JSON do csproj i MSBuild, znaczna inwestycja zakończyła się również nieujednoliceniem plików projektu i zasobów, które umożliwiają śledzenie zależności.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="7e6b1-105">W przypadku projektów platformy .NET Core jest to podobne do pliku Project. JSON.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-105">For .NET Core projects, this is similar to what project.json did.</span></span> <span data-ttu-id="7e6b1-106">Nie istnieje oddzielny plik JSON lub XML, który śledzi zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="7e6b1-107">W przypadku tej zmiany wprowadzono również inne *odwołanie* do składni csproj o nazwie `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span>

<span data-ttu-id="7e6b1-108">Ten dokument zawiera opis nowego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-108">This document describes the new reference type.</span></span> <span data-ttu-id="7e6b1-109">Pokazano również, jak dodać zależność pakietu przy użyciu tego nowego typu odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-109">It also shows how to add a package dependency using this new reference type to your project.</span></span>

## <a name="the-new-packagereference-element"></a><span data-ttu-id="7e6b1-110">Nowy element \<PackageReference ></span><span class="sxs-lookup"><span data-stu-id="7e6b1-110">The new \<PackageReference> element</span></span>

<span data-ttu-id="7e6b1-111">`<PackageReference>` ma następującą strukturę podstawową:</span><span class="sxs-lookup"><span data-stu-id="7e6b1-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="7e6b1-112">Jeśli znasz program MSBuild, zobaczysz znajome inne typy odwołań, które już istnieją.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="7e6b1-113">Klucz jest instrukcją `Include`, która określa identyfikator pakietu, który ma zostać dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-113">The key is the `Include` statement, which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="7e6b1-114">Element podrzędny `<Version>` określa wersję do pobrania.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="7e6b1-115">Wersje są określone zgodnie z [regułami wersji programu NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="7e6b1-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="7e6b1-116">Jeśli nie znasz ogólnej składni `csproj`, zobacz dokumentację [referencyjną projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="7e6b1-117">Dodawanie zależności, która jest dostępna tylko w konkretnym miejscu docelowym, odbywa się przy użyciu warunków, takich jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7e6b1-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="7e6b1-118">Powyższe oznacza, że zależność będzie prawidłowa tylko wtedy, gdy kompilacja ma miejsce dla danego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="7e6b1-119">`$(TargetFramework)` w warunku jest właściwością programu MSBuild, która jest ustawiana w projekcie.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-119">The `$(TargetFramework)` in the condition is an MSBuild property that is being set in the project.</span></span> <span data-ttu-id="7e6b1-120">W przypadku najczęściej używanych aplikacji platformy .NET Core nie trzeba tego robić.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-120">For most common .NET Core applications, you will not need to do this.</span></span>

## <a name="add-a-dependency-to-the-project"></a><span data-ttu-id="7e6b1-121">Dodawanie zależności do projektu</span><span class="sxs-lookup"><span data-stu-id="7e6b1-121">Add a dependency to the project</span></span>

<span data-ttu-id="7e6b1-122">Dodawanie zależności do projektu jest proste.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="7e6b1-123">Oto przykład sposobu dodawania `9.0.1` w wersji Json.NET do projektu.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="7e6b1-124">Oczywiście ma zastosowanie do innych zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-124">Of course, it is applicable to any other NuGet dependency.</span></span>

<span data-ttu-id="7e6b1-125">Gdy otworzysz plik projektu, zobaczysz co najmniej dwa węzły `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="7e6b1-126">Zobaczysz, że jeden z węzłów ma już elementy `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="7e6b1-127">Możesz dodać nową zależność do tego węzła lub utworzyć nową. jest to możliwe, ponieważ wynik będzie taki sam.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-127">You can add your new dependency to this node, or create a new one; it is up to you, as the result will be the same.</span></span>

<span data-ttu-id="7e6b1-128">Poniższy przykład używa szablonu domyślnego, który został porzucony przez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-128">The following example uses the default template that's dropped by `dotnet new console`.</span></span> <span data-ttu-id="7e6b1-129">Jest to prosta aplikacja konsolowa.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-129">This is a simple console application.</span></span> <span data-ttu-id="7e6b1-130">Po otwarciu projektu znajdziesz `<ItemGroup>` z już istniejącymi `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-130">When you open up the project, you'll find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="7e6b1-131">Dodaj do niego następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7e6b1-131">Add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="7e6b1-132">Następnie Zapisz projekt i uruchom `dotnet restore` polecenie, aby zainstalować zależność.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-132">After this, save the project and run the `dotnet restore` command to install the dependency.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="7e6b1-133">Pełny projekt wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="7e6b1-133">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a><span data-ttu-id="7e6b1-134">Usuń zależność z projektu</span><span class="sxs-lookup"><span data-stu-id="7e6b1-134">Remove a dependency from the project</span></span>

<span data-ttu-id="7e6b1-135">Usunięcie zależności z pliku projektu polega po prostu usunięciu `<PackageReference>` z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="7e6b1-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
