---
title: ''
description: ''
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: ''
ms.openlocfilehash: 667b2d4d68edd82a4d18c370e45ea18f4d4b379a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702838"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="22b4f-101">Zarządzanie zależnościami w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="22b4f-101">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="22b4f-102">W tym artykule wyjaśniono, jak dodawać i usuwać zależności, edytując plik projektu lub korzystając z interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="22b4f-102">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="22b4f-103">\<Element> PackageReference</span><span class="sxs-lookup"><span data-stu-id="22b4f-103">The \<PackageReference> element</span></span>

<span data-ttu-id="22b4f-104">`<PackageReference>`Element pliku projektu ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="22b4f-104">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="22b4f-105">Ten `Include` atrybut określa identyfikator pakietu, który ma zostać dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="22b4f-105">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="22b4f-106">Ten `Version` atrybut określa wersję do pobrania.</span><span class="sxs-lookup"><span data-stu-id="22b4f-106">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="22b4f-107">Wersje są określone jako [reguły wersji programu NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="22b4f-107">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="22b4f-108">Jeśli nie znasz składni pliku projektu, zapoznaj się z dokumentacją [projektu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="22b4f-108">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="22b4f-109">Użyj warunków, aby dodać zależność, która jest dostępna tylko w konkretnym miejscu docelowym, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="22b4f-109">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="22b4f-110">Zależność w poprzednim przykładzie będzie prawidłowa tylko wtedy, gdy kompilacja ma miejsce dla danego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="22b4f-110">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="22b4f-111">`$(TargetFramework)`W warunku jest właściwość programu MSBuild, która jest ustawiana w projekcie.</span><span class="sxs-lookup"><span data-stu-id="22b4f-111">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="22b4f-112">W przypadku najczęściej używanych aplikacji platformy .NET Core nie trzeba tego robić.</span><span class="sxs-lookup"><span data-stu-id="22b4f-112">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="22b4f-113">Dodaj zależność, edytując plik projektu</span><span class="sxs-lookup"><span data-stu-id="22b4f-113">Add a dependency by editing the project file</span></span>

<span data-ttu-id="22b4f-114">Aby dodać zależność, Dodaj `<PackageReference>` element wewnątrz `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="22b4f-114">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="22b4f-115">Można dodać do istniejącej `<ItemGroup>` lub utworzyć nową.</span><span class="sxs-lookup"><span data-stu-id="22b4f-115">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="22b4f-116">W poniższym przykładzie zastosowano domyślny projekt aplikacji konsolowej utworzony przez `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="22b4f-116">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="22b4f-117">Dodawanie zależności przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="22b4f-117">Add a dependency by using the CLI</span></span>

<span data-ttu-id="22b4f-118">Aby dodać zależność, uruchom [dotnet add package](dotnet-add-package.md) polecenie, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="22b4f-118">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="22b4f-119">Usuń zależność, edytując plik projektu</span><span class="sxs-lookup"><span data-stu-id="22b4f-119">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="22b4f-120">Aby usunąć zależność, Usuń jej `<PackageReference>` element z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="22b4f-120">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="22b4f-121">Usuwanie zależności przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="22b4f-121">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="22b4f-122">Aby usunąć zależność, uruchom [dotnet remove package](dotnet-remove-package.md) polecenie, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="22b4f-122">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="22b4f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22b4f-123">See also</span></span>

* [<span data-ttu-id="22b4f-124">Odwołania do pakietu w plikach projektu</span><span class="sxs-lookup"><span data-stu-id="22b4f-124">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="22b4f-125">[dotnet list packagedotyczące](dotnet-list-package.md)</span><span class="sxs-lookup"><span data-stu-id="22b4f-125">[dotnet list package command](dotnet-list-package.md)</span></span>
