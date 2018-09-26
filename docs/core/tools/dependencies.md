---
title: Zarządzanie zależnościami w zestaw narzędzi .NET Core
description: Wyjaśnia, jak zarządzanie zależnościami za pomocą narzędzi .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.openlocfilehash: cbeb9ad17932f6abaf14333a71fab2b4b8fd099c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086077"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="4464a-103">Zarządzanie zależnościami za pomocą platformy .NET Core SDK 1.0</span><span class="sxs-lookup"><span data-stu-id="4464a-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="4464a-104">Wraz z przejściem projektów .NET Core z pliku project.json do csproj i MSBuild znaczących inwestycji również się stało, przez co ujednolicenie słów kluczowych pliku projektu i zasoby, które umożliwiają śledzenie zależności.</span><span class="sxs-lookup"><span data-stu-id="4464a-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="4464a-105">Dla projektów .NET Core, jest to podobne do jakiego pliku project.json zostało.</span><span class="sxs-lookup"><span data-stu-id="4464a-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="4464a-106">Plik nie istnieje oddzielny JSON lub XML, który śledzi zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="4464a-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="4464a-107">Dzięki tej zmianie wprowadziliśmy także innego typu *odwołania* w składni csproj, o nazwie `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="4464a-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="4464a-108">W tym dokumencie opisano nowy typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="4464a-108">This document describes the new reference type.</span></span> <span data-ttu-id="4464a-109">Pokazano również, jak można dodać zależności pakietu, za pomocą tego nowego typu odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="4464a-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="4464a-110">Nowy \<PackageReference > element</span><span class="sxs-lookup"><span data-stu-id="4464a-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="4464a-111">`<PackageReference>` Ma podstawowe następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="4464a-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="4464a-112">Jeśli znasz program MSBuild będzie wyglądać dobrze znanych na inne typy odwołań, które już istnieją.</span><span class="sxs-lookup"><span data-stu-id="4464a-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="4464a-113">Klucz jest `Include` instrukcji, która określa identyfikator pakietu, który chcesz dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="4464a-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="4464a-114">`<Version>` Element podrzędny określa wersję można pobrać.</span><span class="sxs-lookup"><span data-stu-id="4464a-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="4464a-115">Wersje są określone jako na [reguły wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="4464a-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="4464a-116">Jeśli nie jesteś zaznajomiony z ogólnych `csproj` składnię, zobacz [odwołanie do projektu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="4464a-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="4464a-117">Dodawanie zależności, która jest dostępna tylko w określonej lokalizacji docelowej jest wykonywane przy użyciu warunki, takie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4464a-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="4464a-118">Oznacza, że powyższe zależności będą tylko ważne, jeśli kompilacja się dzieje w tym element docelowy.</span><span class="sxs-lookup"><span data-stu-id="4464a-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="4464a-119">`$(TargetFramework)` w warunku jest właściwość MSBuild, która jest ustawiona w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4464a-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="4464a-120">W przypadku najbardziej typowych aplikacji .NET Core nie należy w tym celu.</span><span class="sxs-lookup"><span data-stu-id="4464a-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="4464a-121">Dodawanie zależności do projektu</span><span class="sxs-lookup"><span data-stu-id="4464a-121">Adding a dependency to your project</span></span>
<span data-ttu-id="4464a-122">Dodawanie zależności do projektu jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="4464a-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="4464a-123">Oto przykład sposobu dodawania wersji na składnik Json.NET `9.0.1` do projektu.</span><span class="sxs-lookup"><span data-stu-id="4464a-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="4464a-124">Oczywiście ma zastosowanie do wszelkich innych zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="4464a-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="4464a-125">Gdy otworzysz plik projektu, zostanie wyświetlony co najmniej dwóch `<ItemGroup>` węzłów.</span><span class="sxs-lookup"><span data-stu-id="4464a-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="4464a-126">Można zauważyć, że jeden z węzłów ma już `<PackageReference>` elementy.</span><span class="sxs-lookup"><span data-stu-id="4464a-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="4464a-127">Dodaj nowe zależność do tego węzła lub Utwórz nową; jest całkowicie do Ciebie jako wynik będzie taki sam.</span><span class="sxs-lookup"><span data-stu-id="4464a-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="4464a-128">W tym przykładzie użyto domyślnego szablonu, który został upuszczony przez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="4464a-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="4464a-129">Jest to prostą aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="4464a-129">This is a simple console application.</span></span> <span data-ttu-id="4464a-130">Gdy firma Microsoft otworzyć projekt, najpierw znaleźliśmy `<ItemGroup>` z już istniejącymi `<PackageReference>` w nim.</span><span class="sxs-lookup"><span data-stu-id="4464a-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="4464a-131">Firma Microsoft następnie dodaj następujący kod do jego:</span><span class="sxs-lookup"><span data-stu-id="4464a-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="4464a-132">Po to, możemy zapisać projekt i uruchomić `dotnet restore` polecenie, aby zainstalować zależności.</span><span class="sxs-lookup"><span data-stu-id="4464a-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4464a-133">Pełny projekt wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="4464a-133">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="4464a-134">Usuwanie zależności projektu</span><span class="sxs-lookup"><span data-stu-id="4464a-134">Removing a dependency from the project</span></span>
<span data-ttu-id="4464a-135">Usuwanie zależności z pliku projektu pociąga za sobą usunięcie `<PackageReference>` z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="4464a-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
