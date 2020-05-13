---
title: Zarządzanie zależnościami w programie .NET Core
description: Wyjaśnia, jak zarządzać zależnościami projektu dla aplikacji .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: b77acc7d4f03a45784f753d3daaa9810f110a6ac
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205952"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="3da6e-103">Zarządzanie zależnościami w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="3da6e-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="3da6e-104">W tym artykule wyjaśniono, jak dodawać i usuwać zależności, edytując plik projektu lub korzystając z interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3da6e-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="3da6e-105">\<Element> PackageReference</span><span class="sxs-lookup"><span data-stu-id="3da6e-105">The \<PackageReference> element</span></span>

<span data-ttu-id="3da6e-106">`<PackageReference>`Element pliku projektu ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="3da6e-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="3da6e-107">Ten `Include` atrybut określa identyfikator pakietu, który ma zostać dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="3da6e-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="3da6e-108">Ten `Version` atrybut określa wersję do pobrania.</span><span class="sxs-lookup"><span data-stu-id="3da6e-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="3da6e-109">Wersje są określone jako [reguły wersji programu NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="3da6e-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="3da6e-110">Jeśli nie znasz składni pliku projektu, zapoznaj się z dokumentacją [projektu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="3da6e-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="3da6e-111">Użyj warunków, aby dodać zależność, która jest dostępna tylko w konkretnym miejscu docelowym, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3da6e-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="3da6e-112">Zależność w poprzednim przykładzie będzie prawidłowa tylko wtedy, gdy kompilacja ma miejsce dla danego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3da6e-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="3da6e-113">`$(TargetFramework)`W warunku jest właściwość programu MSBuild, która jest ustawiana w projekcie.</span><span class="sxs-lookup"><span data-stu-id="3da6e-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="3da6e-114">W przypadku najczęściej używanych aplikacji platformy .NET Core nie trzeba tego robić.</span><span class="sxs-lookup"><span data-stu-id="3da6e-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="3da6e-115">Dodaj zależność, edytując plik projektu</span><span class="sxs-lookup"><span data-stu-id="3da6e-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="3da6e-116">Aby dodać zależność, Dodaj `<PackageReference>` element wewnątrz `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3da6e-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="3da6e-117">Można dodać do istniejącej `<ItemGroup>` lub utworzyć nową.</span><span class="sxs-lookup"><span data-stu-id="3da6e-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="3da6e-118">W poniższym przykładzie zastosowano domyślny projekt aplikacji konsolowej utworzony przez `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="3da6e-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="3da6e-119">Dodawanie zależności przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="3da6e-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="3da6e-120">Aby dodać zależność, uruchom [dotnet add package](dotnet-add-package.md) polecenie, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3da6e-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="3da6e-121">Usuń zależność, edytując plik projektu</span><span class="sxs-lookup"><span data-stu-id="3da6e-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="3da6e-122">Aby usunąć zależność, Usuń jej `<PackageReference>` element z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3da6e-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="3da6e-123">Usuwanie zależności przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="3da6e-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="3da6e-124">Aby usunąć zależność, uruchom [dotnet remove package](dotnet-remove-package.md) polecenie, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3da6e-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="3da6e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3da6e-125">See also</span></span>

* [<span data-ttu-id="3da6e-126">Odwołania do pakietu w plikach projektu</span><span class="sxs-lookup"><span data-stu-id="3da6e-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="3da6e-127">[dotnet list packagedotyczące](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="3da6e-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
