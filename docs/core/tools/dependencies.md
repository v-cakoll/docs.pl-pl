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
# <a name="manage-dependencies-in-net-core-applications"></a>Zarządzanie zależnościami w aplikacjach .NET Core

W tym artykule wyjaśniono, jak dodawać i usuwać zależności, edytując plik projektu lub używając nazwy między klasą procentowa.

## <a name="the-packagereference-element"></a>Element \<> PackageReference

Element `<PackageReference>` pliku projektu ma następującą strukturę:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Atrybut `Include` określa identyfikator pakietu, który ma zostać dodany do projektu. Atrybut `Version` określa wersję, aby uzyskać. Wersje są określone zgodnie z [regułami wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Jeśli nie znasz składni pliku projektu, zobacz dokumentację [dokumentacji odwołania projektu MSBuild,](/visualstudio/msbuild/msbuild-project-file-schema-reference) aby uzyskać więcej informacji.

Użyj warunków, aby dodać zależność, która jest dostępna tylko w określonym miejscu docelowym, jak pokazano w poniższym przykładzie:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Zależność w poprzednim przykładzie będzie prawidłowa tylko wtedy, gdy kompilacja odbywa się dla danego obiektu docelowego. W `$(TargetFramework)` stanie jest MSBuild właściwość, która jest ustawiona w projekcie. W przypadku większości aplikacji .NET Core nie trzeba tego robić.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Dodawanie zależności przez edycję pliku projektu

Aby dodać zależność, dodaj `<PackageReference>` element `<ItemGroup>` wewnątrz elementu. Można dodać do `<ItemGroup>` istniejącego lub utworzyć nowy. W poniższym przykładzie użyto domyślnego projektu `dotnet new console`aplikacji konsoli utworzonego przez:

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

## <a name="add-a-dependency-by-using-the-cli"></a>Dodawanie zależności przy użyciu funkcji cli

Aby dodać zależność, uruchom [dotnet add package](dotnet-add-package.md) polecenie, jak pokazano w poniższym przykładzie:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Usuwanie zależności przez edycję pliku projektu

Aby usunąć zależność, usuń `<PackageReference>` jego element z pliku projektu.

## <a name="remove-a-dependency-by-using-the-cli"></a>Usuwanie zależności przy użyciu funkcji cli

Aby usunąć zależność, uruchom [dotnet remove package](dotnet-remove-package.md) polecenie, jak pokazano w poniższym przykładzie:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Zobacz też

* [Pakiety NuGet w plikach projektu](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list packagePolecenia](dotnet-remove-package.md)
