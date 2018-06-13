---
title: Zarządzanie zależności w narzędzi platformy .NET Core
description: Wyjaśnia sposób zarządzania zależności przy użyciu narzędzi platformy .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.openlocfilehash: c8f40b8571523b98da55b047fea8d2bf03b390a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213665"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="064f9-103">Zarządzanie zależności z .NET Core SDK w wersji 1.0</span><span class="sxs-lookup"><span data-stu-id="064f9-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="064f9-104">Wraz z przejściem .NET Core projektów z project.json csproj i MSBuild znaczącą inwestycję wystąpiło również zakończonych ujednolicenie pliku projektu i zasoby, które umożliwiają śledzenie zależności.</span><span class="sxs-lookup"><span data-stu-id="064f9-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="064f9-105">Projekty platformy .NET Core jest to podobne do jakiego pliku project.json została.</span><span class="sxs-lookup"><span data-stu-id="064f9-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="064f9-106">Plik nie istnieje oddzielne JSON i XML służący do śledzenia zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="064f9-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="064f9-107">Dzięki tej zmianie także dodaliśmy innego typu *odwołania* do składni csproj o nazwie `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="064f9-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="064f9-108">Ten dokument zawiera opis nowego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="064f9-108">This document describes the new reference type.</span></span> <span data-ttu-id="064f9-109">Widoczny jest również sposób Dodawanie zależności pakietu przy użyciu tego nowego typu odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="064f9-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="064f9-110">Nowy \<PackageReference > — element</span><span class="sxs-lookup"><span data-stu-id="064f9-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="064f9-111">`<PackageReference>` Ma następującą strukturę podstawowe:</span><span class="sxs-lookup"><span data-stu-id="064f9-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="064f9-112">Jeśli znasz program MSBuild, zostanie ona wyszukana znane inne typy odwołań, które już istnieją.</span><span class="sxs-lookup"><span data-stu-id="064f9-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="064f9-113">Klucz jest `Include` instrukcji, która określa identyfikator pakietu, który chcesz dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="064f9-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="064f9-114">`<Version>` Wersji, aby uzyskać określa element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="064f9-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="064f9-115">Wersje są określone w [reguły wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="064f9-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="064f9-116">Jeśli nie masz doświadczenia z ogólnym `csproj` składni, zobacz [odwołania projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="064f9-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="064f9-117">Dodawanie zależności, która jest dostępna tylko w określonej lokalizacji docelowej jest wykonywane przy użyciu warunki, takie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="064f9-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="064f9-118">Środków zależności będą tylko ważne, jeśli wykonywane kompilacji dla podanej docelowej.</span><span class="sxs-lookup"><span data-stu-id="064f9-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="064f9-119">`$(TargetFramework)` w warunku jest właściwość MSBuild, która jest ustawiona w projekcie.</span><span class="sxs-lookup"><span data-stu-id="064f9-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="064f9-120">Do najbardziej typowych zastosowań .NET Core nie musisz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="064f9-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="064f9-121">Dodawanie zależności do projektu</span><span class="sxs-lookup"><span data-stu-id="064f9-121">Adding a dependency to your project</span></span>
<span data-ttu-id="064f9-122">Dodawanie zależności projektu jest prosta.</span><span class="sxs-lookup"><span data-stu-id="064f9-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="064f9-123">Oto przykład sposobu dodawania wersji struktury Json.NET `9.0.1` do projektu.</span><span class="sxs-lookup"><span data-stu-id="064f9-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="064f9-124">Oczywiście nie ma zastosowania do innych zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="064f9-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="064f9-125">Po otwarciu pliku projektu, zobaczysz co najmniej dwóch `<ItemGroup>` węzłów.</span><span class="sxs-lookup"><span data-stu-id="064f9-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="064f9-126">Można zauważyć, że jeden z węzłów ma już `<PackageReference>` elementy.</span><span class="sxs-lookup"><span data-stu-id="064f9-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="064f9-127">Dodaj nowy zależność do tego węzła lub Utwórz nową; jest całkowicie od użytkownika jako wynik będzie taka sama.</span><span class="sxs-lookup"><span data-stu-id="064f9-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="064f9-128">W tym przykładzie używamy domyślny szablon, który jest porzuconych przez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="064f9-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="064f9-129">Jest to prostej aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="064f9-129">This is a simple console application.</span></span> <span data-ttu-id="064f9-130">Gdy firma Microsoft otworzyć projekt, najpierw znaleźliśmy `<ItemGroup>` z już istniejącym `<PackageReference>` w nim.</span><span class="sxs-lookup"><span data-stu-id="064f9-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="064f9-131">Następnie możemy Dodaj następującą wartość do niej:</span><span class="sxs-lookup"><span data-stu-id="064f9-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="064f9-132">Po to, możemy zapisać projekt i uruchomić `dotnet restore` polecenie, aby zainstalować zależności.</span><span class="sxs-lookup"><span data-stu-id="064f9-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="064f9-133">Pełna projektu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="064f9-133">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="064f9-134">Usuwanie zależności w projekcie</span><span class="sxs-lookup"><span data-stu-id="064f9-134">Removing a dependency from the project</span></span>
<span data-ttu-id="064f9-135">Usuwanie zależności z pliku projektu pociąga za sobą usunięcie `<PackageReference>` z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="064f9-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
