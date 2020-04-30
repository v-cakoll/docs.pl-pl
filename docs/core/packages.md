---
title: Pakiety, aplikacje i struktury — .NET Core
description: Poznaj terminologię dotyczącą pakietów, pakietów i struktur.
author: richlander
ms.date: 04/29/2020
ms.openlocfilehash: a6575226feb71b96f1fe5070406c118081a8cbf0
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595588"
---
# <a name="packages-metapackages-and-frameworks"></a>Pakiety, metapakiety i struktury

.NET Core to platforma przeprowadzona przez pakiety NuGet. Niektóre z nich korzystają z szczegółowej definicji pakietów, a inne z nich są bardzo duże. Aby zapewnić tę podwójność, program .NET Core jest dystrybuowany jako szczegółowy zestaw pakietów i w grubszych fragmentach z typem pakietu nieformalnie nazywanym [pakietem](#metapackages).

Każdy pakiet .NET Core obsługuje uruchamianie w wielu implementacjach platformy .NET, które są reprezentowane jako struktury. Niektóre z tych platform to tradycyjne struktury, takie jak `net46`, które reprezentują .NET Framework. Innym zestawem są nowe struktury, które mogą być uważane za "struktury oparte na pakietach", które tworzą nowy model do definiowania struktur. Te platformy oparte na pakietach są całkowicie tworzone i definiowane jako pakiety, tworząc silną relację między pakietami i strukturami.

## <a name="packages"></a>Pakiety

Platforma .NET Core jest podzielona na zestaw pakietów, które udostępniają elementy pierwotne, typy danych wyższego poziomu, typy kompozycji aplikacji i typowe narzędzia. Każdy z tych pakietów reprezentuje pojedynczy zestaw o tej samej nazwie. Na przykład [pakiet System. Runtime](https://www.nuget.org/packages/System.Runtime) zawiera system. Runtime. dll.

Istnieją zalety definiowania pakietów w sposób szczegółowy:

- Szczegółowe pakiety mogą być dostarczane zgodnie z ich własnymi harmonogramami przy stosunkowo ograniczonym testowaniu innych pakietów.
- Szczegółowe pakiety mogą zapewnić różne wsparcie dla systemu operacyjnego i procesora CPU.
- Pakiety szczegółowe mogą mieć zależności specyficzne tylko dla jednej biblioteki.
- Aplikacje są mniejsze, ponieważ odwołania do pakietów nie staną się częścią dystrybucji aplikacji.

Niektóre z tych korzyści są używane tylko w pewnych okolicznościach. Na przykład pakiety .NET Core są zwykle dostarczane według tego samego harmonogramu z tą samą obsługą platformy. W przypadku obsługi poprawki mogą być dystrybuowane i instalowane jako małe aktualizacje pojedynczego pakietu. Ze względu na wąski zakres zmian weryfikacja i czas, w którym ma być dostępna poprawka, są ograniczone do tego, co jest potrzebne dla jednej biblioteki.

Poniżej znajduje się lista pakietów NuGet klucza dla programu .NET Core:

- [System. Runtime](https://www.nuget.org/packages/System.Runtime) — najbardziej podstawowy pakiet .NET Core, w tym <xref:System.Object>, <xref:System.String> <xref:System.Array>,, <xref:System.Action>, i <xref:System.Collections.Generic.IList%601>.
- [System. Collections](https://www.nuget.org/packages/System.Collections) — zestaw ogólnych kolekcji (głównie), w tym <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>.
- [System .NET. http](https://www.nuget.org/packages/System.Net.Http) — zestaw typów dla komunikacji sieciowej http, w tym <xref:System.Net.Http.HttpClient> i. <xref:System.Net.Http.HttpResponseMessage>
- [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) -zestaw typów do odczytu i zapisu do lokalnego lub w sieci magazynu opartego na dyskach, w tym <xref:System.IO.File> i <xref:System.IO.Directory>.
- [System. LINQ](https://www.nuget.org/packages/System.Linq) — zestaw typów do wykonywania zapytań dotyczących obiektów, w tym `Enumerable` i <xref:System.Linq.ILookup%602>.
- [System. odbicie](https://www.nuget.org/packages/System.Reflection) — zestaw typów do ładowania, sprawdzania i uaktywniania typów, w tym <xref:System.Reflection.Assembly> <xref:System.Reflection.TypeInfo> i. <xref:System.Reflection.MethodInfo>

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

Pakiet jest konwencją pakietu NuGet opisującą zestaw pakietów, które są ze sobą zrozumiałe. Pakietbinding reprezentuje ten zestaw pakietów, tworząc ich zależności. Pakiet może opcjonalnie ustanowić strukturę zestawu pakietów przez określenie struktury.

Poprzednie wersje narzędzi platformy .NET Core (narzędzia oparte na elementach *Project. JSON* i * \*. csproj* ) domyślnie są określane jako struktura i pakiet. Obecnie jest to jednak niejawnie przywoływane przez platformę docelową, dzięki czemu każdy pakiet jest powiązany z platformą docelową. Na przykład `netstandard1.6` struktura odwołuje się do pakietu 1.6.0 w wersji Standard. Library. Podobnie, `netcoreapp2.1` struktura odwołuje się do pakietu Microsoft. servicecore. App Version 2.1.0. Aby uzyskać więcej informacji, zobacz [niejawne odwołanie do pakietu w zestaw .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Kierowanie do struktury i niejawne odwołanie do pakietu oznacza, że w efekcie dodawane jest odwołanie do każdego z jego zależnych pakietów jako jednego gestu. Dzięki temu wszystkie biblioteki w tych pakietach są dostępne dla technologii IntelliSense (lub podobnego środowiska) i do publikowania aplikacji.

Istnieją zalety korzystania z pakietów:

- Oferuje wygodne środowisko użytkownika umożliwiające odwoływanie się do dużego zestawu szczegółowych pakietów.
- Definiuje zestaw pakietów (w tym określonych wersji), które są testowane i współdziałające ze sobą.

Pakiet .NET Standard:

- [Standardowa. Library](https://www.nuget.org/packages/NETStandard.Library) — zawiera opis bibliotek, które są częścią .NET Standard. Dotyczy wszystkich implementacji platformy .NET, które obsługują .NET Standard (na przykład .NET Framework, .NET Core i mono). Ustanawia `netstandard` strukturę.

Najważniejsze pakiety podstawowe platformy .NET:

- [Microsoft. WebCore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) — zawiera opis bibliotek, które są częścią dystrybucji programu .NET Core. Ustanawia `.NETCoreApp` strukturę. Zależy od mniejszej `NETStandard.Library`liczby.
- [Microsoft. AspNetCore. app](https://www.nuget.org/packages/Microsoft.AspNetCore.App) — obejmuje wszystkie obsługiwane pakiety z ASP.NET Core i Entity Framework Core z wyjątkiem tych, które zawierają zależności innych firm. Aby uzyskać więcej informacji, zobacz [Microsoft. AspNetCore. App Package for ASP.NET Core](/aspnet/core/fundamentals/metapackage-app) .
- [Microsoft. AspNetCore. All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) — obejmuje wszystkie obsługiwane pakiety z ASP.NET Core, Entity Framework Core i wewnętrznych i innych zależności używanych przez ASP.NET Core i Entity Framework Core. Aby uzyskać więcej informacji, zobacz [Microsoft. AspNetCore. allbinding dla ASP.NET Core 2. x](/aspnet/core/fundamentals/metapackage) .
- [Microsoft. rdzeń. Portable. Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) — zestaw fasad zgodności, który umożliwia uruchamianie na platformie .NET Core bibliotek klas przenośnych opartych na bibliotece Mscorlib (PCLs).

## <a name="frameworks"></a>Struktury

Pakiety .NET Core każda obsługują zestaw platform środowiska uruchomieniowego. Struktury opisują dostępny zestaw interfejsów API (i potencjalnie inne cechy), na których można polegać podczas określania docelowej danej struktury. Są one w wersji, gdy dodawane są nowe interfejsy API.

Na przykład [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) obsługuje następujące struktury:

- . NETFramework, Version = 4.6
- . Standard, Version = 1.3
- 6 platform Xamarin (na przykład xamarinios10)

Warto odróżnić pierwsze dwa z tych platform, ponieważ są to przykłady dwóch różnych sposobów definiowania struktur:

- `.NETFramework,Version=4.6` Struktura reprezentuje dostępne interfejsy api w .NET Framework 4,6. Można utworzyć biblioteki skompilowane z zestawami odwołań .NET Framework 4,6, a następnie dystrybuować te biblioteki w pakietach NuGet w folderze net46 lib. Zostanie ona użyta w przypadku aplikacji, które są przeznaczone dla .NET Framework 4,6 lub są zgodne. Jest to sposób, w jaki wszystkie struktury mają tradycyjną pracował.

- `.NETStandard,Version=1.3` Struktura jest platformą opartą na pakiecie. Opiera się na pakietach przeznaczonych dla platformy w celu definiowania i uwidaczniania interfejsów API w ramach struktury.

## <a name="package-based-frameworks"></a>Struktury oparte na pakietach

Istnieje Dwukierunkowa relacja między strukturami i pakietami. Pierwsza część definiuje interfejsy API dostępne dla danej platformy, na przykład `netstandard1.3`. Pakiety docelowe `netstandard1.3` (lub zgodne platformy, takie jak `netstandard1.0`) definiują interfejsy API dostępne dla `netstandard1.3`programu. Może to być tak samo jak w przypadku definicji cyklicznej, ale nie jest to możliwe. Zgodnie z ich definicją interfejsu API dla struktury pochodzi z pakietów. Sama struktura nie definiuje żadnych interfejsów API.

Drugą częścią relacji jest wybór zasobów. Pakiety mogą zawierać zasoby dla wielu struktur. Mając odwołanie do zestawu pakietów i/lub pakietów trwałych, struktura jest niezbędna do określenia, który zasób powinien być wybrany, na przykład `net46` lub. `netstandard1.3` Ważne jest, aby wybrać odpowiedni element zawartości. Na przykład element `net46` zawartości nie może być zgodny z .NET Framework 4,0 lub .net Core 1,0.

Tę relację można zobaczyć na poniższej ilustracji. Obiekt docelowy *interfejsu API* i definiuje *strukturę*. *Struktura* jest używana do *wyboru elementu zawartości*. Element *zawartości* udostępnia interfejs API.

![Tworzenie struktury opartej na pakiecie](./media/packages/package-framework.png)

Dwie podstawowe struktury oparte na pakietach używane z platformą .NET Core to:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

.NET Standard ([moniker struktury docelowej](../standard/frameworks.md): `netstandard`) reprezentuje interfejsy API zdefiniowane przez i utworzone w oparciu o [.NET Standard](../standard/net-standard.md). Biblioteki przeznaczone do uruchamiania w wielu środowiskach uruchomieniowych powinny wskazywać tę strukturę. Będą one obsługiwane w przypadku środowiska uruchomieniowego zgodnego z .NET Standard, takiego jak .NET Core, .NET Framework i mono/Xamarin. Każdy z tych środowisk uruchomieniowych obsługuje zestaw wersji .NET Standard, w zależności od tego, które interfejsy API implementują.

`netstandard` Struktura niejawnie odwołuje [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) się do pakietu. Na przykład następujący plik projektu MSBuild wskazuje, że obiekty docelowe `netstandard1.6`projektu, które odwołują się do [ `NETStandard.Library` pakietu "wersja 1,6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Przez dodanie `<NetStandardImplicitPackageVersion>` elementu do pliku projektu, który niejawnie określa wersję pakietu, można określić wersję platformy, która jest starsza niż wersja pakietu. Element `<NetStandardImplicitPackageVersion>` jest stosowany tylko w przypadku określania wartości docelowej .NET Core i .NET Standard. Na przykład następujący plik projektu jest prawidłowy.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Być może wydaje się, że `netstandard1.3` jest on niedziwny, `NETStandard.Library`ale używa wersji 1.6.0. Jest to prawidłowy przypadek użycia, ponieważ pakiet, który obsługuje starsze `netstandard` wersje. Może się tak zdarzyć w przypadku, gdy nastąpi standaryzacja wersja 1.6.0 pakietu, i użycie jej dla wszystkich bibliotek przeznaczonych dla różnych `netstandard` wersji. W tym podejściu należy tylko przywrócić `NETStandard.Library` 1.6.0 i nie starsze wersje.

Cofnięcie jest nieprawidłowe: Określanie wartości docelowej `netstandard1.6` dla 1.3.0 wersji programu `NETStandard.Library`. Nie można wyprowadzić wyższej struktury z niższym pakietem, ponieważ dolny pakiet wersji nie ujawnia żadnych zasobów dla tej wyższej struktury. Schemat obsługi wersji dla pakietów webpackages potwierdza, że pakiety są zgodne z najwyższą wersją opisywanej platformy. Zgodnie ze schematem przechowywania wersji pierwsza wersja programu `NETStandard.Library` ma wartość v 1.6.0, ponieważ zawiera `netstandard1.6` ona zasoby. (W przypadku symetrii z poprzednim przykładem w tym miejscu jest używana 1.3.0 v, ale nie istnieje.)

### <a name="net-core-application"></a>Aplikacja .NET Core

Platforma .NET Core ([moniker struktury docelowej](../standard/frameworks.md): `netcoreapp`) reprezentuje pakiety i skojarzone interfejsy API, które są dostarczane z dystrybucją .NET Core oraz modelem aplikacji konsoli, który zapewnia. Aplikacje platformy .NET Core muszą używać tej struktury, ze względu na model aplikacji konsoli, jako że biblioteki, które mają być uruchamiane tylko na platformie .NET Core. Użycie tej struktury ogranicza aplikacje i biblioteki do uruchamiania tylko na platformie .NET Core.

Pakiet `Microsoft.NETCore.App` jest przeznaczony dla `netcoreapp` struktury. Zapewnia dostęp do bibliotek ~ 60, ~ 40 dostarczonych przez `NETStandard.Library` pakiet i ~ 20 dodatkowych. W celu uzyskania dostępu do dodatkowych interfejsów `netcoreapp` API można odwoływać się do dodatkowych `netstandard`bibliotek, które są przeznaczone dla platform docelowych lub zgodnych.

Większość dodatkowych bibliotek dostarczanych przez `Microsoft.NETCore.App` program jest również `netstandard` ukierunkowana na to, że ich zależności `netstandard` są spełnione przez inne biblioteki. Oznacza to, `netstandard` że biblioteki mogą również odwoływać się do tych pakietów jako zależności.
