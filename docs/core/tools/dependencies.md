---
title: "Zarządzanie zależności w narzędzi platformy .NET Core"
description: "Wyjaśnia sposób zarządzania zależności przy użyciu narzędzi platformy .NET Core."
keywords: "Interfejs wiersza polecenia, rozszerzalności, polecenia niestandardowych, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.workload: dotnetcore
ms.openlocfilehash: a064ae72a077583cfb544309700555ebd9d398a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>Zarządzanie zależności z .NET Core SDK w wersji 1.0

Wraz z przejściem .NET Core projektów z project.json csproj i MSBuild znaczącą inwestycję wystąpiło również zakończonych ujednolicenie pliku projektu i zasoby, które umożliwiają śledzenie zależności. Projekty platformy .NET Core jest to podobne do jakiego pliku project.json została. Plik nie istnieje oddzielne JSON i XML służący do śledzenia zależności NuGet. Dzięki tej zmianie także dodaliśmy innego typu *odwołania* do składni csproj o nazwie `<PackageReference>`. 

Ten dokument zawiera opis nowego typu odwołania. Widoczny jest również sposób Dodawanie zależności pakietu przy użyciu tego nowego typu odwołanie do projektu. 

## <a name="the-new-packagereference-element"></a>Nowy \<PackageReference > — element
`<PackageReference>` Ma następującą strukturę podstawowe:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Jeśli znasz program MSBuild, zostanie ona wyszukana znane inne typy odwołań, które już istnieją. Klucz jest `Include` instrukcji, która określa identyfikator pakietu, który chcesz dodać do projektu. `<Version>` Wersji, aby uzyskać określa element podrzędny. Wersje są określone w [reguły wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Jeśli nie masz doświadczenia z ogólnym `csproj` składni, zobacz [odwołania projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji, aby uzyskać więcej informacji.  

Dodawanie zależności, która jest dostępna tylko w określonej lokalizacji docelowej jest wykonywane przy użyciu warunki, takie jak w poniższym przykładzie:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

Środków zależności będą tylko ważne, jeśli wykonywane kompilacji dla podanej docelowej. `$(TargetFramework)` w warunku jest właściwość MSBuild, która jest ustawiona w projekcie. Do najbardziej typowych zastosowań .NET Core nie musisz to zrobić. 

## <a name="adding-a-dependency-to-your-project"></a>Dodawanie zależności do projektu
Dodawanie zależności projektu jest prosta. Oto przykład sposobu dodawania wersji struktury Json.NET `9.0.1` do projektu. Oczywiście nie ma zastosowania do innych zależności NuGet. 

Po otwarciu pliku projektu, zobaczysz co najmniej dwóch `<ItemGroup>` węzłów. Można zauważyć, że jeden z węzłów ma już `<PackageReference>` elementy. Dodaj nowy zależność do tego węzła lub Utwórz nową; jest całkowicie od użytkownika jako wynik będzie taka sama. 

W tym przykładzie używamy domyślny szablon, który jest porzuconych przez `dotnet new console`. Jest to prostej aplikacji konsolowej. Gdy firma Microsoft otworzyć projekt, najpierw znaleźliśmy `<ItemGroup>` z już istniejącym `<PackageReference>` w nim. Następnie możemy Dodaj następującą wartość do niej:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
Po to, możemy zapisać projekt i uruchomić `dotnet restore` polecenie, aby zainstalować zależności. 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pełna projektu wygląda następująco:

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

## <a name="removing-a-dependency-from-the-project"></a>Usuwanie zależności w projekcie
Usuwanie zależności z pliku projektu pociąga za sobą usunięcie `<PackageReference>` z pliku projektu.
