---
title: Pakiety, aplikacje i struktury — .NET Core
description: Poznaj terminologię dotyczącą pakietów, pakietów i struktur.
author: richlander
ms.date: 06/20/2016
ms.openlocfilehash: 6a8e257ebf493365518dd9663fbd2a9cadc83875
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116068"
---
# <a name="packages-metapackages-and-frameworks"></a>Pakiety, metapakiety i struktury

.NET Core to platforma przeprowadzona przez pakiety NuGet. Niektóre z nich korzystają z szczegółowej definicji pakietów, a inne z nich są bardzo duże. Aby zapewnić tę podwójność, produkt jest dystrybuowany jako szczegółowy zestaw pakietów i w grubszych fragmentach z typem pakietu nieformalnie nazywanym [pakietem](#metapackages).

Każdy pakiet .NET Core obsługuje uruchamianie w wielu implementacjach platformy .NET, które są reprezentowane jako struktury. Niektóre z tych platform to tradycyjne struktury, takie jak `net46`, reprezentujące .NET Framework. Innym zestawem są nowe struktury, które mogą być uważane za "struktury oparte na pakietach", które tworzą nowy model do definiowania struktur. Te platformy oparte na pakietach są całkowicie sformatowane i zdefiniowane jako pakiety, co stanowi silną relację między pakietami i strukturami.

## <a name="packages"></a>Pakiety

Platforma .NET Core jest podzielona na zestaw pakietów, które udostępniają elementy pierwotne, typy danych wyższego poziomu, typy kompozycji aplikacji i typowe narzędzia. Każdy z tych pakietów reprezentuje pojedynczy zestaw o tej samej nazwie. Na przykład [pakiet System. Runtime](https://www.nuget.org/packages/System.Runtime) zawiera system. Runtime. dll. 

Istnieją zalety definiowania pakietów w sposób szczegółowy:

- Szczegółowe pakiety mogą być dostarczane zgodnie z ich własnymi harmonogramami przy stosunkowo ograniczonym testowaniu innych pakietów.
- Szczegółowe pakiety mogą zapewnić różne wsparcie dla systemu operacyjnego i procesora CPU.
- Pakiety szczegółowe mogą mieć zależności specyficzne tylko dla jednej biblioteki.
- Aplikacje są mniejsze, ponieważ odwołania do pakietów nie staną się częścią dystrybucji aplikacji.

Niektóre z tych korzyści są używane tylko w pewnych okolicznościach. Na przykład pakiety .NET Core są zwykle dostarczane według tego samego harmonogramu z tą samą obsługą platformy. W przypadku obsługi poprawki mogą być dystrybuowane i instalowane jako małe aktualizacje pojedynczego pakietu. Ze względu na wąski zakres zmian weryfikacja i czas, w którym ma być dostępna poprawka, są ograniczone do tego, co jest potrzebne dla jednej biblioteki.

Poniżej znajduje się lista pakietów NuGet klucza dla programu .NET Core:

- [System. Runtime](https://www.nuget.org/packages/System.Runtime) — najbardziej podstawowy pakiet .NET Core, w tym <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>i <xref:System.Collections.Generic.IList%601>.
- [System. Collections](https://www.nuget.org/packages/System.Collections) — zestaw ogólnych kolekcji (głównie), w tym <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>.
- [System .NET. http](https://www.nuget.org/packages/System.Net.Http) — zestaw typów dla komunikacji sieciowej http, w tym <xref:System.Net.Http.HttpClient> i <xref:System.Net.Http.HttpResponseMessage>.
- [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) -zestaw typów służący do odczytywania i zapisywania w lokalnym lub sieciowym magazynie opartym na dyskach, w tym <xref:System.IO.File> i <xref:System.IO.Directory>.
- [System. LINQ](https://www.nuget.org/packages/System.Linq) — zestaw typów do wykonywania zapytań dotyczących obiektów, w tym `Enumerable` i <xref:System.Linq.ILookup%602>.
- [System. odbicie](https://www.nuget.org/packages/System.Reflection) — zestaw typów do ładowania, sprawdzania i uaktywniania typów, w tym <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> i <xref:System.Reflection.MethodInfo>.

Zwykle, zamiast dołączania każdego pakietu, jest prostsze i bardziej niezawodne, aby uwzględnić [pakiet](#metapackages). Jeśli jednak potrzebujesz pojedynczego pakietu, możesz dołączyć go tak jak w poniższym przykładzie, który odwołuje się do pakietu [System. Runtime](https://www.nuget.org/packages/System.Runtime/) . 

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

Pakiety webpackages to Konwencja pakietu NuGet opisująca zestaw pakietów, które są ze sobą zrozumiałe. Reprezentują one ten zestaw pakietów, udostępniając ich zależności. Mogą opcjonalnie ustanowić strukturę dla tego zestawu pakietów przez określenie struktury. 

Poprzednie wersje narzędzi .NET Core Tools (zarówno narzędzi Project. JSON i csproj) są domyślnie określone jako struktura i pakiet. Obecnie jest to jednak niejawnie przywoływane przez platformę docelową, dzięki czemu każdy pakiet jest powiązany z platformą docelową. Na przykład `netstandard1.6` Framework odwołuje się do pakietu 1.6.0 w wersji Standard. Library. Podobnie `netcoreapp2.1` Framework odwołuje się do pakietu Microsoft. servicecore. App Version 2.1.0. Aby uzyskać więcej informacji, zobacz [niejawne odwołanie do pakietu w zestaw .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Kierowanie do struktury i niejawne odwołanie do pakietu oznacza, że w efekcie dodawane jest odwołanie do każdego z jego zależnych pakietów jako jednego gestu. Dzięki temu wszystkie biblioteki w tych pakietach są dostępne dla technologii IntelliSense (lub podobnego środowiska) i do publikowania aplikacji.  

Istnieją zalety korzystania z pakietów:

- Oferuje wygodne środowisko użytkownika umożliwiające odwoływanie się do dużego zestawu szczegółowych pakietów. 
- Definiuje zestaw pakietów (w tym określonych wersji), które są testowane i współdziałające ze sobą.

Pakiet .NET Standard:

- [Standardowa. Library](https://www.nuget.org/packages/NETStandard.Library) — zawiera opis bibliotek, które są częścią ".NET standard". Dotyczy wszystkich implementacji platformy .NET (na przykład .NET Framework, .NET Core i mono), które obsługują .NET Standard. Ustanawia strukturę "standard".

Najważniejsze pakiety podstawowe platformy .NET:

- [Microsoft. WebCore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) — zawiera opis bibliotek, które są częścią dystrybucji programu .NET Core. Ustala [strukturę`.NETCoreApp`](https://github.com/dotnet/core-setup/blob/release/1.1.0/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Zależy od mniejszej `NETStandard.Library`.
- [Microsoft. AspNetCore. app](https://www.nuget.org/packages/Microsoft.AspNetCore.App) — obejmuje wszystkie obsługiwane pakiety z ASP.NET Core i Entity Framework Core z wyjątkiem tych, które zawierają zależności innych firm. Aby uzyskać więcej informacji, zobacz [Microsoft. AspNetCore. App Package for ASP.NET Core](/aspnet/core/fundamentals/metapackage-app) .
- [Microsoft. AspNetCore. All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) — obejmuje wszystkie obsługiwane pakiety z ASP.NET Core, Entity Framework Core i wewnętrznych i innych zależności używanych przez ASP.NET Core i Entity Framework Core. Aby uzyskać więcej informacji, zobacz [Microsoft. AspNetCore. allbinding dla ASP.NET Core 2. x](/aspnet/core/fundamentals/metapackage) .
- [Microsoft. rdzeń. Portable. Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) — zestaw fasad zgodności, który umożliwia uruchamianie na platformie .NET Core bibliotek klas przenośnych opartych na bibliotece Mscorlib (PCLs).

## <a name="frameworks"></a>Struktury

Pakiety .NET Core każda obsługują zestaw platform środowiska uruchomieniowego. Struktury opisują dostępny zestaw interfejsów API (i potencjalnie inne cechy), na których można polegać podczas określania docelowej danej struktury. Są one w wersji, gdy dodawane są nowe interfejsy API.

Na przykład [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) obsługuje następujące struktury:

- . NETFramework, Version = 4.6
- . Standard, Version = 1.3
- 6 platform Xamarin (na przykład xamarinios10)

Warto odróżnić pierwsze dwa z tych platform, ponieważ są to przykłady dwóch różnych sposobów definiowania struktur.

`.NETFramework,Version=4.6` Framework reprezentuje dostępne interfejsy API w .NET Framework 4,6. Można utworzyć biblioteki skompilowane z zestawami referencyjnymi .NET Framework 4,6, a następnie dystrybuować te biblioteki w pakietach NuGet w folderze net46 lib. Będzie ona używana w przypadku aplikacji przeznaczonych dla .NET Framework 4,6 lub zgodnych z nią. Jest to sposób, w jaki wszystkie struktury mają tradycyjną pracował.

Platforma `.NETStandard,Version=1.3` jest platformą opartą na pakiecie. Opiera się na pakietach przeznaczonych dla platformy w celu definiowania i uwidaczniania interfejsów API w ramach struktury.

## <a name="package-based-frameworks"></a>Struktury oparte na pakietach

Istnieje Dwukierunkowa relacja między strukturami i pakietami. Pierwsza część definiuje interfejsy API dostępne dla danej platformy, na przykład `netstandard1.3`. Pakiety przeznaczone dla `netstandard1.3` (lub zgodnych platform, takich jak `netstandard1.0`) definiują interfejsy API dostępne dla `netstandard1.3`. Może to być tak samo jak w przypadku definicji cyklicznej, ale nie jest to możliwe. Zgodnie z ich definicją interfejsu API dla struktury pochodzi z pakietów. Sama struktura nie definiuje żadnych interfejsów API.

Drugą częścią relacji jest wybór zasobów. Pakiety mogą zawierać zasoby dla wielu struktur. Mając odwołanie do zestawu pakietów i/lub pakietów trwałych, struktura jest wymagana do określenia, który zasób powinien być wybrany, na przykład `net46` lub `netstandard1.3`. Ważne jest, aby wybrać odpowiedni element zawartości. Na przykład zasób `net46` nie jest zgodny z .NET Framework 4,0 lub .NET Core 1,0.

Tę relację można zobaczyć na poniższej ilustracji. Obiekt docelowy *interfejsu API* i definiuje *strukturę*. *Struktura* jest używana do *wyboru elementu zawartości*. Element *zawartości* udostępnia interfejs API.

![Tworzenie struktury opartej na pakiecie](./media/packages/package-framework.png)

Dwie podstawowe struktury oparte na pakietach używane z platformą .NET Core to:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

.NET Standard ([moniker struktury docelowej](../standard/frameworks.md): `netstandard`) reprezentuje interfejsy API zdefiniowane przez i utworzone na podstawie [.NET Standard](../standard/net-standard.md). Biblioteki przeznaczone do uruchamiania w wielu środowiskach uruchomieniowych powinny wskazywać tę strukturę. Będą one obsługiwane w przypadku środowiska uruchomieniowego zgodnego z .NET Standard, takiego jak .NET Core, .NET Framework i mono/Xamarin. Każdy z tych środowisk uruchomieniowych obsługuje zestaw wersji .NET Standard, w zależności od tego, które interfejsy API implementują.

Platforma `netstandard` niejawnie odwołuje się do [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) pakietu. Na przykład następujący plik projektu MSBuild wskazuje, że projekt jest przeznaczony `netstandard1.6`, który odwołuje się do pakietu [`NETStandard.Library` w wersji 1,6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Jednak struktury i odwołania do pakietu w pliku projektu nie muszą być zgodne i można użyć elementu `<NetStandardImplicitPackageVersion>` w pliku projektu, aby określić wersję platformy, która jest starsza niż wersja pakietu. Na przykład następujący plik projektu jest prawidłowy.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Być może wydaje się, że jest to dziwna `netstandard1.3`, ale używana jest wersja 1.6.0 `NETStandard.Library`. Jest to prawidłowy przypadek użycia, ponieważ pakiet webpackage obsługuje starsze wersje `netstandard`. Może się tak zdarzyć w przypadku, gdy nastąpi standaryzacja wersja 1.6.0 pakietu, i użycie jej dla wszystkich bibliotek, które są przeznaczone dla różnych wersji `netstandard`. W tym podejściu należy tylko przywrócić `NETStandard.Library` 1.6.0 i nie wcześniejszych wersji. 

Odwrócenie nie jest prawidłowe: Określanie wartości docelowej `netstandard1.6` z wersją `NETStandard.Library`1.3.0. Nie można wyprowadzić wyższej struktury z niższym pakietem, ponieważ dolny pakiet wersji nie ujawnia żadnych zasobów dla tej wyższej struktury. Schemat obsługi wersji dla pakietów webpackages potwierdza, że pakiety są zgodne z najwyższą wersją opisywanej platformy. Zgodnie ze schematem przechowywania wersji pierwsza wersja `NETStandard.Library` to 1.6.0, ponieważ zawiera ona `netstandard1.6` zasoby. w powyższym przykładzie użyto programu v 1.3.0, dla symetrii z powyższym przykładem, ale nie istnieje.

### <a name="net-core-application"></a>Aplikacja .NET Core

Struktura .NET Core ([Target Framework moniker](../standard/frameworks.md): `netcoreapp`) reprezentuje pakiety i skojarzone interfejsy API, które są dostarczane z dystrybucją .NET Core oraz modelem aplikacji konsoli, który zapewnia. Aplikacje platformy .NET Core muszą używać tej struktury, ze względu na model aplikacji konsoli, jako że biblioteki, które mają być uruchamiane tylko na platformie .NET Core. Użycie tej struktury ogranicza aplikacje i biblioteki do uruchamiania tylko na platformie .NET Core. 

Pakiet `Microsoft.NETCore.App` jest przeznaczony dla struktury `netcoreapp`. Zapewnia ona dostęp do bibliotek ~ 60, ~ 40 dostarczonych przez pakiet `NETStandard.Library` i dodatkowo 20 dodatkowych. Aby uzyskać dostęp do dodatkowych interfejsów API, można odwoływać się do dodatkowych bibliotek, które są przeznaczone dla `netcoreapp` lub zgodnych platform, takich jak `netstandard`. 

Większość dodatkowych bibliotek zapewnianych przez `Microsoft.NETCore.App` również docelowy `netstandard`, ponieważ ich zależności są spełnione przez inne biblioteki `netstandard`. Oznacza to, że biblioteki `netstandard` mogą również odwoływać się do tych pakietów jako zależności. 
