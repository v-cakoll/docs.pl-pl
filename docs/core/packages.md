---
title: Pakiety, metapakiety i struktury
description: Dowiedz się, terminologia dotycząca pakiety, metapakiety i struktury.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: e68c63d26133ac76b718bb3696d16c81bd943dc2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519958"
---
# <a name="packages-metapackages-and-frameworks"></a>Pakiety, metapakiety i struktury

.NET core to platforma z pakietów NuGet. Niektóre produktu środowisk korzyści z szczegółowych definicji pakietów, podczas gdy inne z gruboziarnistych. Aby umożliwić tym duality, produktu jest rozpowszechniany jako zbiór szczegółowych pakietów i następnie opisane we fragmentach gruboziarnisty o typie pakietu nazywane nieformalnie "meta Microsoft.aspnetcore.all".

Obsługuje każdego z pakietów .NET Core, są uruchamiane na wiele implementacji .NET, reprezentowane jako struktury. Niektóre z tych platform są tradycyjnych struktur, takie jak `net46`, reprezentujący programu .NET Framework. Inny zestaw jest nowych platform, które mogą być uważane za "opartej na pakiecie struktury", które określają nowy model do definiowania struktur. Te struktury opartej na pakiecie są całkowicie sformułowany i definiowane za pomocą pakietów stanowiących silnych relacji między pakietami i struktur.

## <a name="packages"></a>Pakiety

.NET core jest dzielony na zestaw pakietów, które zapewniają podstawowych, typów danych wyższego poziomu, typy skład aplikacji i wspólne narzędzia. Każda z tych pakietów reprezentuje pojedynczy zestaw o takiej samej nazwie. Na przykład [System.Runtime](https://www.nuget.org/packages/System.Runtime) zawiera biblioteki System.Runtime.dll. 

Istnieją zalety łączenia Definiowanie pakietów w sposób szczegółowe:

- Szczegółowe pakiety mogą być na własnym harmonogramem stosunkowo krótki testowania innych pakietów.
- Szczegółowych pakietów można obsługiwać różne systemu operacyjnego i procesora CPU.
- Szczegółowych pakietów może zawierać tylko jedną bibliotekę określonych zależności.
- Aplikacje są mniejsze, ponieważ pakiety bez odwołań nie należały do dystrybucji aplikacji.

Niektóre z tych zalet są używane tylko w pewnych okolicznościach. Na przykład .NET Core pakiety zwykle będą dostarczane na tym samym harmonogramem przy użyciu tej samej pomocy technicznej platformy. W przypadku obsługi, poprawki, może być rozpowszechniany i zainstalowany jako małych pojedynczy pakiet aktualizacji. Ze względu na wąskie zakresu zmian weryfikacji i czas, aby udostępnić poprawkę jest ograniczona do potrzebne dla jednej biblioteki.

Oto lista kluczowych pakietów NuGet dla platformy .NET Core:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) — większość podstawowych pakiet .NET Core, w tym <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>, i <xref:System.Collections.Generic.IList%601>.
- [System.Collections —](https://www.nuget.org/packages/System.Collections) — zestaw (zasadniczo) kolekcje ogólne, w tym <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) — zbiór typów komunikacji sieciowej protokołu HTTP, w tym <xref:System.Net.Http.HttpClient> i <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) — zestaw typów do odczytu i zapisu do magazynów lokalnych lub sieciowych opartej na dyskach, w tym <xref:System.IO.File> i <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) — zestaw typów obiektów, w tym zapytań `Enumerable` i <xref:System.Linq.ILookup%602>.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) — zestaw typów dotyczące ładowania, inspekcja i aktywowanie typów, w tym <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> i <xref:System.Reflection.MethodInfo>.

Typowo, zamiast tym pakiety w projektach na podstawie przez pakiet, jest znacznie łatwiejsze do uwzględnienia *meta Microsoft.aspnetcore.all*, czyli zestaw pakietów, które są często używane razem. (Aby uzyskać więcej informacji na temat metapakiety, zobacz następującą sekcję). Jednak jeśli potrzebujesz jeden pakiet, możesz dołączyć ją tak jak w przykładzie poniżej, która odwołuje się do [System.Runtime](https://www.nuget.org/packages/System.Runtime/) pakietu. 

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

Metapakiety są opisujące zestaw pakietów, które są ze sobą znaczące Konwencja pakietu NuGet. Reprezentują one ten zestaw pakietów, definiując je jako zależności. Można opcjonalnie ustanowić umożliwiająca ten zestaw pakietów, określając platformę. 

Poprzednie wersje narzędzia .NET Core (project.json i csproj narzędzi) domyślnie określona platforma i meta Microsoft.aspnetcore.all. Obecnie jednak meta Microsoft.aspnetcore.all niejawnie odwołuje się platformę docelową, aby każdy meta Microsoft.aspnetcore.all jest powiązany z platformy docelowej. Na przykład `netstandard1.6` framework odwołuje się do meta Microsoft.aspnetcore.all wersji 1.6.0 NetStandard.Library. Podobnie `netcoreapp2.1` framework odwołuje się do meta Microsoft.aspnetcore.all pakietów Microsoft.NETCore.App wersja 2.1.0. Aby uzyskać więcej informacji, zobacz [meta Microsoft.aspnetcore.all niejawne odwołanie do pakietu w zestawie SDK programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Przeznaczanie i niejawne odwołanie do meta Microsoft.aspnetcore.all oznacza obowiązuje dodajesz odwołanie do każdego z jego zależne pakiety jako pojedynczego gestu. Temu wszystkich bibliotek w tych pakietów dostępnych dla funkcji IntelliSense (lub podobne możliwości) i publikowania aplikacji.  

Istnieją zalety łączenia metapakiety:

- Zapewnia wygodne można odwoływać się do szerokiej gamy szczegółowych pakietów. 
- Definiuje zestaw pakietów (łącznie z określonych wersji), które są testowane i dobrze współpracować.

.NET Standard meta Microsoft.aspnetcore.all jest:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) — w tym artykule opisano bibliotek, które są częścią ".NET Standard". Ma zastosowanie do wszystkich implementacje platformy .NET (na przykład, .NET Framework, .NET Core i platformy Mono), które obsługują .NET Standard. Ustanawia framework "netstandard".

Kluczowe metapakiety platformy .NET Core są następujące:

- [Pakietów Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) — w tym artykule opisano bibliotek, które są częścią dystrybucji platformy .NET Core. Ustanawia [ `.NETCoreApp` framework](https://github.com/dotnet/core-setup/blob/release/1.1.0/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Zależy na mniejszego `NETStandard.Library`.
- [Pakiet](https://www.nuget.org/packages/Microsoft.AspNetCore.All) — obejmuje wszystkie obsługiwane pakiety z wewnętrznych i innych firm zależności, używane przez program ASP.NET Core i Entity Framework Core, platformy Entity Framework Core i ASP.NET Core. Zobacz [pakiet meta Microsoft.aspnetcore.all dla platformy ASP.NET Core 2.x](/aspnet/core/fundamentals/metapackage) Aby uzyskać więcej informacji.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) — zestaw fasad zgodności, umożliwiających na podstawie mscorlib biblioteki klas przenośnych (PCLs) do uruchamiania na platformie .NET Core.

## <a name="frameworks"></a>Struktury

.NET core pakiety obsługi zestawu Platform środowiska uruchomieniowego. Struktury opisują zestaw interfejsów API dostępnych (i potencjalnie innych parametrów), możesz polegać na gdy miejscem docelowym danej struktury. Są one określonej wersji w miarę dodawania nowych interfejsów API.

Na przykład [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) obsługuje następujące platformy:

- . NETFramework, Version = 4.6
- . NETStandard, Version = 1,3
- 6 platformy Xamarin (na przykład xamarinios10)

Jest to przydatne porównać dwa pierwsze z tych środowisk, ponieważ są one przykłady dwa różne sposoby, że struktury są zdefiniowane.

`.NETFramework,Version=4.6` Framework reprezentuje dostępne interfejsy API w programie .NET Framework 4.6. Można tworzyć biblioteki skompilowany przy użyciu platformy .NET Framework 4.6 zestawy odwołań, a następnie dokonać dystrybucji tych bibliotek w pakietach NuGet w folderze lib net46. Będzie używany w przypadku aplikacji, przeznaczone na platformę .NET Framework 4.6 lub które są zgodne z nim. Jest to sposób tradycyjnie korzystano wszystkich środowisk.

`.NETStandard,Version=1.3` Framework to struktura opartej na pakiecie. Opiera się na pakiety, których platformą docelową platformę, by definiowanie i udostępnianie interfejsów API w ramach.

## <a name="package-based-frameworks"></a>Na podstawie pakietu struktury

Istnieje dwukierunkowa relacja platform i pakietów. Pierwsza część jest zdefiniowanie interfejsami API dostępnymi dla danej platformy, na przykład `netstandard1.3`. Pakiety przeznaczone `netstandard1.3` (lub zgodny platform, na przykład `netstandard1.0`) definiowanie interfejsów API dostępna dla `netstandard1.3`. Które stwierdzenie może wydawać się podobnie jak definicję cykliczną, ale nie jest. Bycia "pakiet" na podstawie definicji interfejsu API dla framework pochodzą z pakietów. Framework sam w sobie nie definiuje żadnych interfejsów API.

Druga część relacji to wybór trwały. Pakiety mogą zawierać zasoby dla wielu platform. Podane odwołanie do zestawu pakiety i/lub metapakiety, struktura jest potrzebne do określenia, którego należy wybrać, na przykład `net46` lub `netstandard1.3`. Należy wybrać prawidłowy zasób. Na przykład `net46` zasobów nie jest prawdopodobne były zgodne z .NET Framework 4.0 lub platformy .NET Core 1.0.


Możesz zobaczyć tę relację na poniższej ilustracji. *API* jest przeznaczony dla i definiuje *framework*. *Framework* służy do *wybór zasobów*. *Zasobów* zapewnia interfejs API.

![Struktura oparta na pakiecie kompozycji](./media/packages/package-framework.png)

Są dwa podstawowe opartej na pakiecie struktury używane z platformą .NET Core:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET standard

.NET Standard (moniker platformy docelowej: `netstandard`) framework reprezentuje interfejsy API zdefiniowany przez i wbudowane w górnej części [.NET Standard](../standard/net-standard.md). Bibliotek, które są przeznaczone do uruchamiania na wielu modułów wykonawczych powinien dotyczyć ten framework. Będą one obsługiwane, w dowolnym .NET Standard zgodne środowiska uruchomieniowego, takich jak .NET Core, .NET Framework i Mono/Xamarin. Każda z tych środowisk uruchomieniowych obsługuje zestaw .NET Standard wersji, w zależności od tego, w których interfejsy API implementują.

`netstandard` Framework niejawnie odwołuje się [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) meta Microsoft.aspnetcore.all. Na przykład następujący plik projektu MSBuild wskazuje, że projekt jest ukierunkowany `netstandard1.6`, która odwołuje się do [ `NETStandard.Library` wersji 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) meta Microsoft.aspnetcore.all.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Jednak framework i meta Microsoft.aspnetcore.all odwołania w pliku projektu nie muszą być zgodne, i możesz użyć `<NetStandardImplicitPackageVersion>` elementu w pliku projektu, aby określić wersję, która jest niższa niż wersja meta Microsoft.aspnetcore.all. Na przykład następujący plik projektu jest nieprawidłowa.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Może się to wydawać dziwne do obiektu docelowego `netstandard1.3` , ale 1.6.0 wersji `NETStandard.Library`. Jest nieprawidłowy przypadek użycia, ponieważ meta Microsoft.aspnetcore.all przechowuje obsługę starszych `netstandard` wersji. Może to być przypadek został standaryzowane 1.6.0 wersję meta Microsoft.aspnetcore.all i użyć jej do wszystkich bibliotek, które rozmaite `netstandard` wersji. W przypadku tej metody, wystarczy do przywrócenia `NETStandard.Library` 1.6.0, a nie jego wcześniejszych wersji. 

Odwrotnej nie jest prawidłowym: Określanie wartości docelowej `netstandard1.6` z 1.3.0 wersję `NETStandard.Library`. Wyższe framework z niższym meta Microsoft.aspnetcore.all, nie może być przeznaczony ponieważ niższe meta Microsoft.aspnetcore.all wersji nie udostępni wszelkie zasoby dla tej struktury wyższy. Schemat przechowywania wersji dla metapakiety potwierdza, czy metapakiety odpowiadają najwyższa wersja Framework, które opisano w nich. Na podstawie schematu przechowywania wersji, a pierwsza wersja `NETStandard.Library` jest v1.6.0, biorąc pod uwagę, że zawiera on `netstandard1.6` zasoby. V1.3.0 jest używana w przykładzie powyżej dla symetrii pracę w przykładzie powyżej, ale w rzeczywistości nie istnieje.

### <a name="net-core-application"></a>Aplikacja platformy .NET core

Aplikacji .NET Core (TFM: `netcoreapp`) reprezentuje framework, pakiety i skojarzone interfejsy API, które są dostarczane z dystrybucji platformy .NET Core i modelu aplikacji konsoli, która zapewnia. Aplikacje platformy .NET core, należy użyć ta struktura, ze względu na przeznaczonych dla modelu aplikacji konsoli, jak bibliotek, które jest przeznaczony do uruchamiania tylko na platformie .NET Core. Za pomocą ta struktura ogranicza aplikacji i bibliotek do uruchamiania tylko na platformie .NET Core. 

`Microsoft.NETCore.App` Cele meta Microsoft.aspnetcore.all `netcoreapp` framework. Zapewnia dostęp do bibliotek około 60, około 40 dostarczone przez `NETStandard.Library` pakietu i ~ 20 więcej w dodatku. Dodatkowe biblioteki można odwoływać się przeznaczonych `netcoreapp` lub zgodny struktur, takich jak `netstandard`, aby uzyskać dostęp do dodatkowych interfejsów API. 

Dodatkowe biblioteki dostarczane przez większość `Microsoft.NETCore.App` również kierować `netstandard` biorąc pod uwagę, że ich zależności przez inne `netstandard` bibliotek. Oznacza to, że `netstandard` bibliotek można także odwoływać się te pakiety jako zależności. 
