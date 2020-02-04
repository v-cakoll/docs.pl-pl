---
title: Zarządzanie zależnościami w narzędziu .NET Core
description: Wyjaśnia, jak zarządzać zależnościami przy użyciu narzędzi programu .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 916daca0240c10dc63ca96048590a426bc51d450
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965623"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a>Zarządzanie zależnościami przy użyciu zestaw .NET Core SDK 1,0

Po przeniesieniu projektów platformy .NET Core z pliku Project. JSON do csproj i MSBuild, znaczna inwestycja zakończyła się również nieujednoliceniem plików projektu i zasobów, które umożliwiają śledzenie zależności. W przypadku projektów platformy .NET Core jest to podobne do pliku Project. JSON. Nie istnieje oddzielny plik JSON lub XML, który śledzi zależności NuGet. W przypadku tej zmiany wprowadzono również inne *odwołanie* do składni csproj o nazwie `<PackageReference>`.

Ten dokument zawiera opis nowego typu odwołania. Pokazano również, jak dodać zależność pakietu przy użyciu tego nowego typu odwołania do projektu.

## <a name="the-new-packagereference-element"></a>Nowy element \<PackageReference >

`<PackageReference>` ma następującą strukturę podstawową:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Jeśli znasz program MSBuild, zobaczysz znajome inne typy odwołań, które już istnieją. Klucz jest instrukcją `Include`, która określa identyfikator pakietu, który ma zostać dodany do projektu. Element podrzędny `<Version>` określa wersję do pobrania. Wersje są określone zgodnie z [regułami wersji programu NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Jeśli nie znasz składni pliku projektu, zapoznaj się z dokumentacją projektu programu [MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) , aby uzyskać więcej informacji.

Użyj warunków, aby dodać zależność, która jest dostępna tylko w konkretnym miejscu docelowym, jak pokazano w następującym przykładzie:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Zależność będzie poprawna tylko wtedy, gdy kompilacja ma miejsce dla danego elementu docelowego. `$(TargetFramework)` w warunku jest właściwością programu MSBuild, która jest ustawiana w projekcie. W przypadku najczęściej używanych aplikacji platformy .NET Core nie trzeba tego robić.

## <a name="add-a-dependency-to-the-project"></a>Dodawanie zależności do projektu

Dodawanie zależności do projektu jest proste. Oto przykład sposobu dodawania `9.0.1` w wersji Json.NET do projektu. Oczywiście ma zastosowanie do innych zależności NuGet.

Plik projektu zawiera co najmniej dwa węzły `<ItemGroup>`. Jeden z węzłów ma już elementy `<PackageReference>`. Możesz dodać nową zależność do tego węzła lub utworzyć nową. wynik będzie taki sam.

Poniższy przykład używa szablonu domyślnego, który został porzucony przez `dotnet new console`. Jest to prosta aplikacja konsolowa. Po otwarciu projektu znajdziesz `<ItemGroup>` z już istniejącymi `<PackageReference>`. Dodaj do niego następujące elementy:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Następnie Zapisz projekt i uruchom `dotnet restore` polecenie, aby zainstalować zależność.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pełny projekt wygląda następująco:

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

## <a name="remove-a-dependency-from-the-project"></a>Usuń zależność z projektu

Usunięcie zależności z pliku projektu polega po prostu usunięciu `<PackageReference>` z pliku projektu.
