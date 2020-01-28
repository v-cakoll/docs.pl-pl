---
title: Zarządzanie zależnościami w narzędziu .NET Core
description: Wyjaśnia, jak zarządzać zależnościami przy użyciu narzędzi programu .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: e14fa42534d807e2a0fcce1dabe747c18c5166b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733376"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>Zarządzanie zależnościami przy użyciu zestaw .NET Core SDK 1,0

Po przeniesieniu projektów platformy .NET Core z pliku Project. JSON do csproj i MSBuild, znaczna inwestycja zakończyła się również nieujednoliceniem plików projektu i zasobów, które umożliwiają śledzenie zależności. W przypadku projektów platformy .NET Core jest to podobne do pliku Project. JSON. Nie istnieje oddzielny plik JSON lub XML, który śledzi zależności NuGet. W przypadku tej zmiany wprowadzono również inne *odwołanie* do składni csproj o nazwie `<PackageReference>`. 

Ten dokument zawiera opis nowego typu odwołania. Pokazano również, jak dodać zależność pakietu przy użyciu tego nowego typu odwołania do projektu. 

## <a name="the-new-packagereference-element"></a>Nowy element \<PackageReference >
`<PackageReference>` ma następującą strukturę podstawową:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Jeśli znasz program MSBuild, zobaczysz znajome inne typy odwołań, które już istnieją. Klucz jest instrukcją `Include`, która określa identyfikator pakietu, który ma zostać dodany do projektu. Element podrzędny `<Version>` określa wersję do pobrania. Wersje są określone zgodnie z [regułami wersji programu NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Jeśli nie znasz ogólnej składni `csproj`, zobacz dokumentację [referencyjną projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) , aby uzyskać więcej informacji.  

Dodawanie zależności, która jest dostępna tylko w konkretnym miejscu docelowym, odbywa się przy użyciu warunków, takich jak w poniższym przykładzie:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Powyższe oznacza, że zależność będzie prawidłowa tylko wtedy, gdy kompilacja ma miejsce dla danego elementu docelowego. `$(TargetFramework)` w warunku jest właściwością programu MSBuild, która jest ustawiana w projekcie. W przypadku najczęściej używanych aplikacji platformy .NET Core nie trzeba tego robić. 

## <a name="adding-a-dependency-to-your-project"></a>Dodawanie zależności do projektu
Dodawanie zależności do projektu jest proste. Oto przykład sposobu dodawania `9.0.1` w wersji Json.NET do projektu. Oczywiście ma zastosowanie do innych zależności NuGet. 

Gdy otworzysz plik projektu, zobaczysz co najmniej dwa węzły `<ItemGroup>`. Zobaczysz, że jeden z węzłów ma już elementy `<PackageReference>`. Możesz dodać nową zależność do tego węzła lub utworzyć nową. jest on całkowicie aktualny, ponieważ wynik będzie taki sam. 

W tym przykładzie użyjemy szablonu domyślnego, który zostanie porzucony przez `dotnet new console`. Jest to prosta aplikacja konsolowa. Po otwarciu projektu najpierw znajdziesz `<ItemGroup>` z już istniejącymi `<PackageReference>`. Następnie dodamy do niego następujące elementy:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Następnie zapiszemy projekt i uruchomimy `dotnet restore` polecenie, aby zainstalować zależność. 

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

## <a name="removing-a-dependency-from-the-project"></a>Usuwanie zależności z projektu
Usunięcie zależności z pliku projektu polega po prostu usunięciu `<PackageReference>` z pliku projektu.
