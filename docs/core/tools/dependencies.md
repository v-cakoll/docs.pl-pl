---
title: Zarządzanie zależnościami w ustom .NET Core
description: W tym artykule wyjaśniono, jak zarządzać zależnościami projektu dla aplikacji .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399148"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="ac99e-103">Zarządzanie zależnościami w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="ac99e-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="ac99e-104">W tym artykule wyjaśniono, jak dodawać i usuwać zależności, edytując plik projektu lub używając nazwy między klasą procentowa.</span><span class="sxs-lookup"><span data-stu-id="ac99e-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="ac99e-105">Element \<> PackageReference</span><span class="sxs-lookup"><span data-stu-id="ac99e-105">The \<PackageReference> element</span></span>

<span data-ttu-id="ac99e-106">Element `<PackageReference>` pliku projektu ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="ac99e-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="ac99e-107">Atrybut `Include` określa identyfikator pakietu, który ma zostać dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="ac99e-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="ac99e-108">Atrybut `Version` określa wersję, aby uzyskać.</span><span class="sxs-lookup"><span data-stu-id="ac99e-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="ac99e-109">Wersje są określone zgodnie z [regułami wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="ac99e-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="ac99e-110">Jeśli nie znasz składni pliku projektu, zobacz dokumentację [dokumentacji odwołania projektu MSBuild,](/visualstudio/msbuild/msbuild-project-file-schema-reference) aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ac99e-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="ac99e-111">Użyj warunków, aby dodać zależność, która jest dostępna tylko w określonym miejscu docelowym, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ac99e-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="ac99e-112">Zależność w poprzednim przykładzie będzie prawidłowa tylko wtedy, gdy kompilacja odbywa się dla danego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ac99e-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="ac99e-113">W `$(TargetFramework)` stanie jest MSBuild właściwość, która jest ustawiona w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ac99e-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="ac99e-114">W przypadku większości aplikacji .NET Core nie trzeba tego robić.</span><span class="sxs-lookup"><span data-stu-id="ac99e-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="ac99e-115">Dodawanie zależności przez edycję pliku projektu</span><span class="sxs-lookup"><span data-stu-id="ac99e-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="ac99e-116">Aby dodać zależność, dodaj `<PackageReference>` element `<ItemGroup>` wewnątrz elementu.</span><span class="sxs-lookup"><span data-stu-id="ac99e-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="ac99e-117">Można dodać do `<ItemGroup>` istniejącego lub utworzyć nowy.</span><span class="sxs-lookup"><span data-stu-id="ac99e-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="ac99e-118">W poniższym przykładzie użyto domyślnego projektu `dotnet new console`aplikacji konsoli utworzonego przez:</span><span class="sxs-lookup"><span data-stu-id="ac99e-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="ac99e-119">Dodawanie zależności przy użyciu funkcji cli</span><span class="sxs-lookup"><span data-stu-id="ac99e-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="ac99e-120">Aby dodać zależność, uruchom [dotnet add package](dotnet-add-package.md) polecenie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ac99e-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="ac99e-121">Usuwanie zależności przez edycję pliku projektu</span><span class="sxs-lookup"><span data-stu-id="ac99e-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="ac99e-122">Aby usunąć zależność, usuń `<PackageReference>` jego element z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ac99e-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="ac99e-123">Usuwanie zależności przy użyciu funkcji cli</span><span class="sxs-lookup"><span data-stu-id="ac99e-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="ac99e-124">Aby usunąć zależność, uruchom [dotnet remove package](dotnet-remove-package.md) polecenie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ac99e-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="ac99e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac99e-125">See also</span></span>

* [<span data-ttu-id="ac99e-126">Pakiety NuGet w plikach projektu</span><span class="sxs-lookup"><span data-stu-id="ac99e-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="ac99e-127">[dotnet list packagePolecenia](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="ac99e-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
