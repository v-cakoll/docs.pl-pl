---
title: Pakiety, metapakiety i struktury — .NET Core
description: Naucz się terminologii dla pakietów, metapakietów i struktur.
author: richlander
ms.date: 06/20/2016
ms.openlocfilehash: 657519edf1c0860ee3222c71ce85723e19029a9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398980"
---
# <a name="packages-metapackages-and-frameworks"></a>Pakiety, metapakiety i struktury

.NET Core to platforma sofna z pakietów NuGet. Niektóre doświadczenia produktu korzystają z drobnoziarnistej definicji opakowań, podczas gdy inne z gruboziarnistych. Aby pomieścić tę dwoistość, .NET Core jest rozprowadzany jako szczegółowy zestaw pakietów i w grubszych fragmentach z typem pakietu nieformalnie nazywanym [metapakietem.](#metapackages)

Każdy z pakietów .NET Core obsługuje uruchamianie na wielu implementacjach platformy .NET, reprezentowanych jako struktury. Niektóre z tych struktur są tradycyjne `net46`struktury, jak , który reprezentuje .NET Framework. Innym zestawem są nowe ramy, które można traktować jako "ramy oparte na pakiecie", które ustanawiają nowy model definiowania struktur. Te struktury oparte na pakiecie są w całości tworzone i definiowane jako pakiety, tworząc silną relację między pakietami i strukturami.

## <a name="packages"></a>Pakiety

.NET Core jest podzielony na zestaw pakietów, które zapewniają podstawowe, typy danych wyższego poziomu, typy kompozycji aplikacji i typowe narzędzia. Każdy z tych pakietów reprezentuje pojedynczy zestaw o tej samej nazwie. Na przykład [pakiet System.Runtime](https://www.nuget.org/packages/System.Runtime) zawiera system.runtime.dll.

Istnieją zalety definiowania opakowań w sposób szczegółowy:

- Opakowania drobnoziarniste mogą być wysyłane zgodnie z własnym harmonogramem przy stosunkowo ograniczonym testowaniu innych opakowań.
- Pakiety szczegółowe mogą zapewniać różne wsparcie systemu operacyjnego i procesora CPU.
- Pakiety szczegółowe mogą mieć zależności specyficzne tylko dla jednej biblioteki.
- Aplikacje są mniejsze, ponieważ pakiety bez odwołań nie stają się częścią dystrybucji aplikacji.

Niektóre z tych korzyści są używane tylko w pewnych okolicznościach. Na przykład pakiety NET Core zazwyczaj będą wysyłane według tego samego harmonogramu z tą samą obsługą platformy. W przypadku obsługi poprawki mogą być dystrybuowane i instalowane jako małe aktualizacje pojedynczego pakietu. Ze względu na wąski zakres zmian, sprawdzania poprawności i czas, aby udostępnić poprawkę jest ograniczona do tego, co jest potrzebne dla jednej biblioteki.

Poniżej znajduje się lista kluczowych pakietów NuGet dla .NET Core:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) - Najbardziej podstawowy pakiet .NET <xref:System.String> <xref:System.Array>Core, w tym <xref:System.Action> <xref:System.Object>, , , i <xref:System.Collections.Generic.IList%601>.
- [System.Collections](https://www.nuget.org/packages/System.Collections) — zestaw (przede wszystkim) kolekcji <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602>ogólnych, w tym i .
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) - Zestaw typów komunikacji sieciowej <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpResponseMessage>HTTP, w tym i .
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) - Zestaw typów do odczytu i zapisu do lokalnej <xref:System.IO.File> <xref:System.IO.Directory>lub sieciowej pamięci masowej na dysku, w tym i .
- [System.Linq](https://www.nuget.org/packages/System.Linq) — zestaw typów do wykonywania `Enumerable` <xref:System.Linq.ILookup%602>zapytań obiektów, w tym i .
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) - Zestaw typów do ładowania, sprawdzania i aktywowania <xref:System.Reflection.TypeInfo> <xref:System.Reflection.MethodInfo>typów, w tym <xref:System.Reflection.Assembly>, i .

Zazwyczaj, zamiast uwzględniać każdy pakiet, łatwiej i bardziej niezawodne jest dołączenie [metapakietu.](#metapackages) Jednak gdy potrzebujesz jednego pakietu, można dołączyć go jak w poniższym przykładzie, który odwołuje się do [pakietu System.Runtime.](https://www.nuget.org/packages/System.Runtime/)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>Metapakiety

Metapackage jest konwencją pakietu NuGet do opisywania zestawu pakietów, które mają znaczenie razem. Metapakiet reprezentuje ten zestaw pakietów, czyniąc je zależnościami. Metapackage można opcjonalnie ustanowić ramy dla zestawu pakietów, określając struktury.

Poprzednie wersje narzędzi .NET Core (zarówno project.json, jak i csproj-based tools) domyślnie określały zarówno strukturę, jak i metapakiet. Obecnie jednak metapakiet jest niejawnie odwołuje się do platformy docelowej, tak aby każdy metapakiet jest powiązany z platformą docelową. Na przykład `netstandard1.6` framework odwołuje się do metapakietu NetStandard.Library w wersji 1.6.0. Podobnie `netcoreapp2.1` struktura odwołuje się do metapakietu Microsoft.NETCore.App w wersji 2.1.0. Aby uzyskać więcej informacji, zobacz [niejawny pakiet metapakietów niejawnych w sdku .NET Core .](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md)

Kierowanie na ramach i niejawnie odwołując się do metapakietu oznacza, że w efekcie dodajesz odwołanie do każdego z jego pakietów zależnych jako pojedynczy gest. Dzięki temu wszystkie biblioteki w tych pakietach są dostępne dla intelliSense (lub podobnego środowiska) i do publikowania aplikacji.

Korzystanie z metapakietów ma zalety:

- Zapewnia wygodne środowisko użytkownika do odwoływania się do dużego zestawu pakietów drobnoziarnistych.
- Definiuje zestaw pakietów (w tym określonych wersji), które są testowane i dobrze ze sobą współpracują.

Metapakiet .NET Standard to:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) — opisuje biblioteki, które są częścią .NET Standard. Dotyczy wszystkich implementacji .NET obsługujących standard .NET (na przykład .NET Framework, .NET Core i Mono). Ustanawia `netstandard` ramy.

Klucz .NET Core metapackages są:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) — opisuje biblioteki, które są częścią dystrybucji .NET Core. Ustanawia `.NETCoreApp` ramy. Zależy od mniejszych `NETStandard.Library`.
- [Microsoft.AspNetCore.App](https://www.nuget.org/packages/Microsoft.AspNetCore.App) — zawiera wszystkie obsługiwane pakiety z ASP.NET Core i Entity Framework Core, z wyjątkiem tych, które zawierają zależności innych firm. Aby uzyskać więcej [informacji, zobacz pakiet metapackage microsoft.AspNetCore.App dla ASP.NET Core.](/aspnet/core/fundamentals/metapackage-app)
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) — zawiera wszystkie obsługiwane pakiety z ASP.NET Core, Entity Framework Core oraz zależności wewnętrznych i innych firm używanych przez ASP.NET Core i Entity Framework Core. Zobacz [Microsoft.AspNetCore.All metapackage dla ASP.NET Core 2.x](/aspnet/core/fundamentals/metapackage) aby uzyskać więcej informacji.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) — zestaw fasad zgodności, które umożliwiają uruchamianie przenośnych bibliotek klas (PCLs) opartych na mscorlib na komputerze .NET Core.

## <a name="frameworks"></a>Struktury

Pakiety .NET Core obsługują zestaw struktur czasu wykonywania. Struktury opisują dostępny zestaw interfejsu API (i potencjalnie inne cechy), na których można polegać podczas kierowania danej struktury. Są one wersjonowane w miarę dodawania nowych interfejsów API.

Na przykład [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) obsługuje następujące struktury:

- . NETFramework,Wersja=4.6
- . NETStandard,Wersja=1.3
- 6 platform Xamarin (na przykład xamarinios10)

Warto kontrastować pierwsze dwa z tych struktur, ponieważ są one przykładami dwóch różnych sposobów definiowania struktur:

- Struktura `.NETFramework,Version=4.6` reprezentuje dostępne interfejsy API w .NET Framework 4.6. Można utworzyć biblioteki skompilowane z zestawami referencyjnymi .NET Framework 4.6, a następnie rozpowszechniać te biblioteki w pakietach NuGet w folderze lib net46. Będzie on używany dla aplikacji, które są przeznaczone dla .NET Framework 4.6 lub które są zgodne z nim. Tak tradycyjnie działały wszystkie struktury.

- Ramy `.NETStandard,Version=1.3` te są ramami opartymi na pakiecie. Opiera się na pakietach, które są przeznaczone dla struktury, aby zdefiniować i udostępnić interfejsy API w zakresie struktury.

## <a name="package-based-frameworks"></a>Ramy oparte na pakietach

Istnieje dwukierunkowa relacja między ramami i pakietami. Pierwsza część jest definiowanie interfejsów API dostępnych `netstandard1.3`dla danej struktury, na przykład . Pakiety, `netstandard1.3` które są przeznaczone dla `netstandard1.0`(lub zgodnych `netstandard1.3`struktur, takich jak ) definiują interfejsy API dostępne dla . To może brzmieć jak okrągła definicja, ale tak nie jest. Ze względu na "oparte na pakiecie", definicja interfejsu API dla struktury pochodzi z pakietów. Sama struktura nie definiuje żadnych interfejsów API.

Druga część relacji to wybór zasobu. Pakiety mogą zawierać zasoby dla wielu struktur. Biorąc pod uwagę odwołanie do zestawu pakietów i/lub metapakietów, ramy są potrzebne do `net46` `netstandard1.3`określenia, który składnik aktywów powinien zostać wybrany, na przykład lub . Ważne jest, aby wybrać odpowiedni zasób. Na przykład `net46` zasób prawdopodobnie nie będzie zgodny z .NET Framework 4.0 lub .NET Core 1.0.

Możesz zobaczyć tę relację na poniższej ilustracji. Interfejs *API* jest przeznaczony dla celów i definiuje *ramy*. *Struktura* jest używana do *wyboru zasobów*. *Zasób* zapewnia interfejs API.

![Skład ramowy oparty na pakiecie](./media/packages/package-framework.png)

Dwie podstawowe struktury oparte na pakiecie używane z .NET Core to:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

Struktura .NET Standard[(Target Framework Moniker](../standard/frameworks.md): `netstandard`) reprezentuje interfejsy API zdefiniowane przez i zbudowane na wierzchu [.NET Standard](../standard/net-standard.md). Biblioteki, które są przeznaczone do uruchamiania w wielu programach wykonywania powinny być przeznaczone dla tej struktury. Będą one obsługiwane w dowolnym czasie wykonywania zgodnym ze standardami .NET, takim jak .NET Core, .NET Framework i Mono/Xamarin. Każdy z tych uruchomień obsługuje zestaw wersji .NET Standard, w zależności od tego, które interfejsy API implementują.

Struktura `netstandard` niejawnie [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) odwołuje się do metapakietu. Na przykład następujący plik projektu MSBuild wskazuje, że obiekt docelowy `netstandard1.6`projektu , który odwołuje się do [ `NETStandard.Library` metapakietu w wersji 1.6.](https://www.nuget.org/packages/NETStandard.Library/1.6.0)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Jednak framework i metapackage odwołania w pliku projektu nie trzeba dopasować `<NetStandardImplicitPackageVersion>` i można użyć elementu w pliku projektu, aby określić wersję struktury, która jest niższa niż wersja metapackage. Na przykład następujący plik projektu jest prawidłowy.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

To może wydawać `netstandard1.3` się dziwne do celu, ale `NETStandard.Library`użyj wersji 1.6.0 . Jest to prawidłowy przypadek użycia, ponieważ metapakiet `netstandard` utrzymuje obsługę starszych wersji. Może to być przypadek, w którym został znormalizowany w wersji 1.6.0 metapakietu i używać `netstandard` go do wszystkich bibliotek, które są przeznaczone dla różnych wersji. Dzięki takiemu podejściu wystarczy `NETStandard.Library` przywrócić 1.6.0, a nie wcześniejsze wersje.

Odwrotna nie będzie prawidłowa: kierowanie `netstandard1.6` z wersją `NETStandard.Library`1.3.0 . Nie można kierować wyższy framework z niższym metapackage, ponieważ metapakiet niższej wersji nie będzie uwidaczniać żadnych zasobów dla tej wyższej struktury. Schemat wersji metapakietów potwierdza, że metapakiety są zgodne z najwyższą wersją struktury, którą opisują. Na mocy schematu wersji, pierwsza `NETStandard.Library` wersja jest v1.6.0, `netstandard1.6` biorąc pod uwagę, że zawiera aktywa. (W przypadku symetrii w poprzednim przykładzie w tym miejscu jest używany v1.3.0, ale w rzeczywistości nie istnieje).

### <a name="net-core-application"></a>Aplikacja .NET Core

Struktura .NET Core[(Target Framework Moniker](../standard/frameworks.md): `netcoreapp`) reprezentuje pakiety i skojarzone interfejsy API, które są dostępne z dystrybucją .NET Core i model aplikacji konsoli, który zapewnia. Aplikacje .NET Core muszą używać tej struktury ze względu na kierowanie na model aplikacji konsoli, podobnie jak biblioteki, które mają być uruchamiane tylko w usłudze .NET Core. Korzystanie z tej struktury ogranicza aplikacje i biblioteki do uruchamiania tylko w platformie .NET Core.

Metapakiet `Microsoft.NETCore.App` jest `netcoreapp` przeznaczony dla struktury. Zapewnia dostęp do ~ 60 bibliotek, ~ `NETStandard.Library` 40 dostarczonych przez pakiet i ~ 20 więcej dodatkowo. Można odwoływać się do `netcoreapp` dodatkowych bibliotek, które `netstandard`są przeznaczone dla platform docelowych lub zgodnych, takich jak , aby uzyskać dostęp do dodatkowych interfejsów API.

Większość dodatkowych bibliotek dostarczonych `Microsoft.NETCore.App` przez `netstandard` również miejsce docelowe, biorąc `netstandard` pod uwagę, że ich zależności są spełnione przez inne biblioteki. Oznacza to, że `netstandard` biblioteki mogą również odwoływać się do tych pakietów jako zależności.
