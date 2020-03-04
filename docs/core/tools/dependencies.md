---
title: Zarządzanie zależnościami w programie .NET Core
description: Wyjaśnia, jak zarządzać zależnościami projektu dla aplikacji .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157248"
---
# <a name="manage-dependencies-in-net-core-applications"></a>Zarządzanie zależnościami w aplikacjach .NET Core

W tym artykule wyjaśniono, jak dodawać i usuwać zależności, edytując plik projektu lub korzystając z interfejsu wiersza polecenia.

## <a name="the-packagereference-element"></a>Element \<PackageReference >

Element pliku projektu `<PackageReference>` ma następującą strukturę:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Atrybut `Include` określa identyfikator pakietu, który ma zostać dodany do projektu. Atrybut `Version` określa wersję do pobrania. Wersje są określone jako [reguły wersji programu NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Jeśli nie znasz składni pliku projektu, zapoznaj się z dokumentacją [projektu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) , aby uzyskać więcej informacji.

Użyj warunków, aby dodać zależność, która jest dostępna tylko w konkretnym miejscu docelowym, jak pokazano w następującym przykładzie:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Zależność w poprzednim przykładzie będzie prawidłowa tylko wtedy, gdy kompilacja ma miejsce dla danego elementu docelowego. `$(TargetFramework)` w warunku jest właściwością programu MSBuild, która jest ustawiana w projekcie. W przypadku najczęściej używanych aplikacji platformy .NET Core nie trzeba tego robić.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Dodaj zależność, edytując plik projektu

Aby dodać zależność, Dodaj element `<PackageReference>` wewnątrz elementu `<ItemGroup>`. Możesz dodać do istniejącego `<ItemGroup>` lub utworzyć nowy. Poniższy przykład używa domyślnego projektu aplikacji konsolowej utworzonego przez `dotnet new console`:

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

## <a name="add-a-dependency-by-using-the-cli"></a>Dodawanie zależności przy użyciu interfejsu wiersza polecenia

Aby dodać zależność, uruchom polecenie [dotnet add package](dotnet-add-package.md) , jak pokazano w następującym przykładzie:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Usuń zależność, edytując plik projektu

Aby usunąć zależność, Usuń jej element `<PackageReference>` z pliku projektu.

## <a name="remove-a-dependency-by-using-the-cli"></a>Usuwanie zależności przy użyciu interfejsu wiersza polecenia

Aby usunąć zależność, uruchom polecenie [dotnet remove package](dotnet-remove-package.md) , jak pokazano w następującym przykładzie:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Zobacz też

* [Pakiety NuGet w plikach projektu](../project-sdk/msbuild-props.md#nuget-packages)
* [polecenie dotnet list package](dotnet-remove-package.md)
