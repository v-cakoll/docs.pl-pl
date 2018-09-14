---
title: Zarządzanie zależnościami w zestaw narzędzi .NET Core
description: Wyjaśnia, jak zarządzanie zależnościami za pomocą narzędzi .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.openlocfilehash: cbeb9ad17932f6abaf14333a71fab2b4b8fd099c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591124"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>Zarządzanie zależnościami za pomocą platformy .NET Core SDK 1.0

Wraz z przejściem projektów .NET Core z pliku project.json do csproj i MSBuild znaczących inwestycji również się stało, przez co ujednolicenie słów kluczowych pliku projektu i zasoby, które umożliwiają śledzenie zależności. Dla projektów .NET Core, jest to podobne do jakiego pliku project.json zostało. Plik nie istnieje oddzielny JSON lub XML, który śledzi zależności NuGet. Dzięki tej zmianie wprowadziliśmy także innego typu *odwołania* w składni csproj, o nazwie `<PackageReference>`. 

W tym dokumencie opisano nowy typ odwołania. Pokazano również, jak można dodać zależności pakietu, za pomocą tego nowego typu odwołania do projektu. 

## <a name="the-new-packagereference-element"></a>Nowy \<PackageReference > element
`<PackageReference>` Ma podstawowe następującą strukturę:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Jeśli znasz program MSBuild będzie wyglądać dobrze znanych na inne typy odwołań, które już istnieją. Klucz jest `Include` instrukcji, która określa identyfikator pakietu, który chcesz dodać do projektu. `<Version>` Element podrzędny określa wersję można pobrać. Wersje są określone jako na [reguły wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Jeśli nie jesteś zaznajomiony z ogólnych `csproj` składnię, zobacz [odwołanie do projektu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji, aby uzyskać więcej informacji.  

Dodawanie zależności, która jest dostępna tylko w określonej lokalizacji docelowej jest wykonywane przy użyciu warunki, takie jak w poniższym przykładzie:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Oznacza, że powyższe zależności będą tylko ważne, jeśli kompilacja się dzieje w tym element docelowy. `$(TargetFramework)` w warunku jest właściwość MSBuild, która jest ustawiona w projekcie. W przypadku najbardziej typowych aplikacji .NET Core nie należy w tym celu. 

## <a name="adding-a-dependency-to-your-project"></a>Dodawanie zależności do projektu
Dodawanie zależności do projektu jest bardzo proste. Oto przykład sposobu dodawania wersji na składnik Json.NET `9.0.1` do projektu. Oczywiście ma zastosowanie do wszelkich innych zależności NuGet. 

Gdy otworzysz plik projektu, zostanie wyświetlony co najmniej dwóch `<ItemGroup>` węzłów. Można zauważyć, że jeden z węzłów ma już `<PackageReference>` elementy. Dodaj nowe zależność do tego węzła lub Utwórz nową; jest całkowicie do Ciebie jako wynik będzie taki sam. 

W tym przykładzie użyto domyślnego szablonu, który został upuszczony przez `dotnet new console`. Jest to prostą aplikację konsolową. Gdy firma Microsoft otworzyć projekt, najpierw znaleźliśmy `<ItemGroup>` z już istniejącymi `<PackageReference>` w nim. Firma Microsoft następnie dodaj następujący kod do jego:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
Po to, możemy zapisać projekt i uruchomić `dotnet restore` polecenie, aby zainstalować zależności. 

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

## <a name="removing-a-dependency-from-the-project"></a>Usuwanie zależności projektu
Usuwanie zależności z pliku projektu pociąga za sobą usunięcie `<PackageReference>` z pliku projektu.
