---
title: Zarządzanie zależnościami w programie .NET Core
description: Wyjaśnia, jak zarządzać zależnościami projektu dla aplikacji .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 3e1d807ea69e66e31b277a92cd6a1dc0e76531b5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795550"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="23790-103">Zarządzanie zależnościami w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="23790-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="23790-104">W tym artykule wyjaśniono, jak dodawać i usuwać zależności, edytując plik projektu lub korzystając z interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="23790-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="23790-105">Element \<> PackageReference</span><span class="sxs-lookup"><span data-stu-id="23790-105">The \<PackageReference> element</span></span>

<span data-ttu-id="23790-106">Element `<PackageReference>` pliku projektu ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="23790-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="23790-107">Ten `Include` ATRYBUT określa identyfikator pakietu, który ma zostać dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="23790-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="23790-108">Ten `Version` atrybut określa wersję do pobrania.</span><span class="sxs-lookup"><span data-stu-id="23790-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="23790-109">Wersje są określone jako [reguły wersji programu NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="23790-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="23790-110">Jeśli nie znasz składni pliku projektu, zapoznaj się z dokumentacją [projektu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="23790-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="23790-111">Użyj warunków, aby dodać zależność, która jest dostępna tylko w konkretnym miejscu docelowym, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="23790-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="23790-112">Zależność w poprzednim przykładzie będzie prawidłowa tylko wtedy, gdy kompilacja ma miejsce dla danego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="23790-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="23790-113">`$(TargetFramework)` W warunku jest właściwość programu MSBuild, która jest ustawiana w projekcie.</span><span class="sxs-lookup"><span data-stu-id="23790-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="23790-114">W przypadku najczęściej używanych aplikacji platformy .NET Core nie trzeba tego robić.</span><span class="sxs-lookup"><span data-stu-id="23790-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="23790-115">Dodaj zależność, edytując plik projektu</span><span class="sxs-lookup"><span data-stu-id="23790-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="23790-116">Aby dodać zależność, Dodaj `<PackageReference>` element wewnątrz `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="23790-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="23790-117">Można dodać do istniejącej `<ItemGroup>` lub utworzyć nową.</span><span class="sxs-lookup"><span data-stu-id="23790-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="23790-118">W poniższym przykładzie zastosowano domyślny projekt aplikacji konsolowej utworzony przez `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="23790-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="23790-119">Dodawanie zależności przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="23790-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="23790-120">Aby dodać zależność, uruchom [dotnet add package](dotnet-add-package.md) polecenie, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="23790-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="23790-121">Usuń zależność, edytując plik projektu</span><span class="sxs-lookup"><span data-stu-id="23790-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="23790-122">Aby usunąć zależność, Usuń jej `<PackageReference>` element z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="23790-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="23790-123">Usuwanie zależności przy użyciu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="23790-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="23790-124">Aby usunąć zależność, uruchom [dotnet remove package](dotnet-remove-package.md) polecenie, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="23790-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="23790-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23790-125">See also</span></span>

* [<span data-ttu-id="23790-126">Odwołania do pakietu w plikach projektu</span><span class="sxs-lookup"><span data-stu-id="23790-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties)
* <span data-ttu-id="23790-127">[dotnet list packagedotyczące](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="23790-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
