---
title: "Zarządzanie zależności w narzędzi platformy .NET Core"
description: "Wyjaśnia sposób zarządzania zależności przy użyciu narzędzi platformy .NET Core."
keywords: "Interfejs wiersza polecenia, rozszerzalności, polecenia niestandardowych, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.workload: dotnetcore
ms.openlocfilehash: a064ae72a077583cfb544309700555ebd9d398a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="cb1a4-104">Zarządzanie zależności z .NET Core SDK w wersji 1.0</span><span class="sxs-lookup"><span data-stu-id="cb1a4-104">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="cb1a4-105">Wraz z przejściem .NET Core projektów z project.json csproj i MSBuild znaczącą inwestycję wystąpiło również zakończonych ujednolicenie pliku projektu i zasoby, które umożliwiają śledzenie zależności.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-105">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="cb1a4-106">Projekty platformy .NET Core jest to podobne do jakiego pliku project.json została.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-106">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="cb1a4-107">Plik nie istnieje oddzielne JSON i XML służący do śledzenia zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-107">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="cb1a4-108">Dzięki tej zmianie także dodaliśmy innego typu *odwołania* do składni csproj o nazwie `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-108">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="cb1a4-109">Ten dokument zawiera opis nowego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-109">This document describes the new reference type.</span></span> <span data-ttu-id="cb1a4-110">Widoczny jest również sposób Dodawanie zależności pakietu przy użyciu tego nowego typu odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-110">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="cb1a4-111">Nowy \<PackageReference > — element</span><span class="sxs-lookup"><span data-stu-id="cb1a4-111">The new \<PackageReference> element</span></span>
<span data-ttu-id="cb1a4-112">`<PackageReference>` Ma następującą strukturę podstawowe:</span><span class="sxs-lookup"><span data-stu-id="cb1a4-112">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="cb1a4-113">Jeśli znasz program MSBuild, zostanie ona wyszukana znane inne typy odwołań, które już istnieją.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-113">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="cb1a4-114">Klucz jest `Include` instrukcji, która określa identyfikator pakietu, który chcesz dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-114">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="cb1a4-115">`<Version>` Wersji, aby uzyskać określa element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-115">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="cb1a4-116">Wersje są określone w [reguły wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="cb1a4-116">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="cb1a4-117">Jeśli nie masz doświadczenia z ogólnym `csproj` składni, zobacz [odwołania projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-117">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="cb1a4-118">Dodawanie zależności, która jest dostępna tylko w określonej lokalizacji docelowej jest wykonywane przy użyciu warunki, takie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cb1a4-118">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="cb1a4-119">Środków zależności będą tylko ważne, jeśli wykonywane kompilacji dla podanej docelowej.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-119">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="cb1a4-120">`$(TargetFramework)` w warunku jest właściwość MSBuild, która jest ustawiona w projekcie.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-120">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="cb1a4-121">Do najbardziej typowych zastosowań .NET Core nie musisz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-121">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="cb1a4-122">Dodawanie zależności do projektu</span><span class="sxs-lookup"><span data-stu-id="cb1a4-122">Adding a dependency to your project</span></span>
<span data-ttu-id="cb1a4-123">Dodawanie zależności projektu jest prosta.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-123">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="cb1a4-124">Oto przykład sposobu dodawania wersji struktury Json.NET `9.0.1` do projektu.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-124">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="cb1a4-125">Oczywiście nie ma zastosowania do innych zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-125">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="cb1a4-126">Po otwarciu pliku projektu, zobaczysz co najmniej dwóch `<ItemGroup>` węzłów.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-126">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="cb1a4-127">Można zauważyć, że jeden z węzłów ma już `<PackageReference>` elementy.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-127">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="cb1a4-128">Dodaj nowy zależność do tego węzła lub Utwórz nową; jest całkowicie od użytkownika jako wynik będzie taka sama.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-128">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="cb1a4-129">W tym przykładzie używamy domyślny szablon, który jest porzuconych przez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-129">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="cb1a4-130">Jest to prostej aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-130">This is a simple console application.</span></span> <span data-ttu-id="cb1a4-131">Gdy firma Microsoft otworzyć projekt, najpierw znaleźliśmy `<ItemGroup>` z już istniejącym `<PackageReference>` w nim.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-131">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="cb1a4-132">Następnie możemy Dodaj następującą wartość do niej:</span><span class="sxs-lookup"><span data-stu-id="cb1a4-132">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="cb1a4-133">Po to, możemy zapisać projekt i uruchomić `dotnet restore` polecenie, aby zainstalować zależności.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-133">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="cb1a4-134">Pełna projektu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="cb1a4-134">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="cb1a4-135">Usuwanie zależności w projekcie</span><span class="sxs-lookup"><span data-stu-id="cb1a4-135">Removing a dependency from the project</span></span>
<span data-ttu-id="cb1a4-136">Usuwanie zależności z pliku projektu pociąga za sobą usunięcie `<PackageReference>` z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="cb1a4-136">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
