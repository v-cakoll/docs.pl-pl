---
title: Pakiety, Metapackages i platform
description: "Dowiedz się terminologia pakietów, metapackages i platform."
keywords: .NET, .NET core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 609b0845-49e7-4864-957b-21ffe1b93bf2
ms.openlocfilehash: 1d46992d9f5666c87522630c7a4926aaac82475a
ms.sourcegitcommit: 39b65a49271e082add68cb737b48fdbe09d24718
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2017
---
# <a name="packages-metapackages-and-frameworks"></a>Pakiety, Metapackages i platform

Oprogramowanie .NET core to platforma z pakietami NuGet. Niektóre produktu napotyka korzyści z szczegółowych definicji pakietów, podczas gdy inne z coarse-grained. Aby umożliwić tym duality, produkt jest dystrybuowane zgodnie szczegółową pakietów i następnie opisanego w gruboziarnisty fragmenty o typie pakietu nieformalnego o nazwie "metapackage".

Każdego z pakietów platformy .NET Core obsługuje uruchomione na wiele implementacji .NET, reprezentowane jako struktury. Niektóre z tych środowisk tradycyjnych struktur, są tak samo, jak `net46`, reprezentujący programu .NET Framework. Inny zestaw jest nowych struktur, które można traktować jako "na podstawie pakietu struktury", które określają nowy model do definiowania struktury. Te struktury na podstawie pakietu są całkowicie sformułowany i zdefiniowane jako pakietów tworzące umacnianie relacji między pakietami i platform.

## <a name="packages"></a>Pakiety

Oprogramowanie .NET core jest podzielony na zestaw pakietów, zapewniających podstawowych, wyższego poziomu typy danych, typy kompozycji aplikacji i typowych narzędzi. Każdy z tych pakietów reprezentują jednym zestawie o takiej samej nazwie. Na przykład [System.Runtime](https://www.nuget.org/packages/System.Runtime) zawiera biblioteki System.Runtime.dll. 

Istnieją pewne zalety Definiowanie pakietów w sposób szczegółowych:

- Szczegółowe pakiety mogą być w swoim własnym harmonogramem z ograniczonym testowania z innymi pakietami.
- Szczegółowe pakietów zapewniają różne obsługi systemu operacyjnego i procesora CPU.
- Zależności określonych może zawierać tylko jedną bibliotekę szczegółowych pakietów.
- Aplikacje są mniejsze, ponieważ pakiety bez odwołań nie staną się częścią dystrybucji aplikacji.

Niektóre z tych zalet są używane tylko w pewnych okolicznościach. Na przykład pakietami podstawowymi NET zwykle wyśle na ten sam harmonogram z obsługą tej samej platformy. W przypadku obsługi poprawek można dystrybuować i zainstalowany jako małych pojedynczy pakiet aktualizacji. Ze względu na wąsko zdefiniowany zakresu zmian sprawdzanie poprawności i czasu, aby udostępnić poprawka jest ograniczona do potrzebna dla jednej biblioteki.

Poniżej przedstawiono listę kluczy pakietów NuGet dla platformy .NET Core:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) -najbardziej podstawowych pakietu .NET Core, w tym <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>, i <xref:System.Collections.Generic.IList%601>.
- [System.Collections —](https://www.nuget.org/packages/System.Collections) — zestaw (głównie) kolekcje ogólne, w tym <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) — zestaw typów dla protokołu HTTP do komunikacji sieciowej, w tym <xref:System.Net.Http.HttpClient> i <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) — zestaw typów odczytu i zapisu w lokalnym lub sieciowym dysku magazynem opartym na protokole, łącznie z <xref:System.IO.File> i <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) — zestaw typów obiektów, w tym zapytań `Enumerable` i <xref:System.Linq.ILookup%602>.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) — zestaw typów ładowania, kontrolę i aktywowanie typów, w tym <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> i <xref:System.Reflection.MethodInfo>.

Zazwyczaj zamiast tym pakiety w projektach na podstawie przez pakiet, znacznie łatwiej jest obejmują *metapackage*, czyli zestawowi pakietów, które są często używane razem. (Aby uzyskać więcej informacji o metapackages, zobacz sekcję poniżej). Jednak gdy będziesz potrzebować pojedynczy pakiet, można dołączyć go tak jak w przykładzie poniżej odwołującego [System.Runtime](https://www.nuget.org/packages/System.Runtime/) pakietu. 

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

## <a name="metapackages"></a>Metapackages

Metapackages są Konwencja pakietu NuGet opisujące zestaw pakietów, które są ze sobą łatwy do rozpoznania. Reprezentują ten zestaw pakietów przez umieszczenie ich zależności. Można opcjonalnie ustanowić framework dla tego zestawu pakietów przez określenie struktury. 

Poprzednie wersje narzędzi platformy .NET Core (pliku project.json i narzędzia oparte na csproj) domyślnie określony zarówno struktury, jak i metapackage. Obecnie jednak metapackage niejawnie odwołuje się platformy docelowej, dzięki czemu każdy metapackage jest związany z platformy docelowej. Na przykład `netstandard1.6` framework odwołuje się do metapackage wersji 1.6.0 NetStandard.Library. Podobnie `netcoreapp1.1` framework odwołuje się do metapackage Microsoft.NETCore.App wersji 1.1.0. Aby uzyskać więcej informacji, zobacz [metapackage niejawne odwołanie do pakietu w .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Przeznaczanie dla platformy i niejawne odwołanie do metapackage oznacza, że skutkuje dodajesz odwołanie do każdego z jego pakietów zależnych jako pojedynczy gestu. Dzięki temu wszystkich bibliotek w tych pakietach dostępne dla IntelliSense (lub podobne możliwości) i publikowania aplikacji.  

Zalety korzystania metapackages są:

- Zapewnia obsługę wygodny do odwołania duży zbiór szczegółowych pakietów. 
- Definiuje zestaw pakietów (w tym określonych wersji), które są przetestowane i siebie.

.NET Standard metapackage jest:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) — w tym artykule opisano bibliotek, które są częścią ".NET Standard". Dotyczy wszystkich implementacji .NET (na przykład, .NET Framework, .NET Core i Mono), które obsługują .NET Standard. Ustanawia framework "krótkich nazw netstandard".

Klucza metapackages .NET Core są:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) — w tym artykule opisano bibliotek, które są częścią dystrybucji .NET Core. Ustanawia [ `.NETCoreApp` framework](https://github.com/dotnet/core-setup/blob/master/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Zależy od na mniejszy `NETStandard.Library`.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) — zestaw zgodności fasad, pozwalających na podstawie mscorlib przenośnej biblioteki klas (PCLs) do uruchamiania na .NET Core.

## <a name="frameworks"></a>Struktury

Oprogramowanie .NET core pakietów obsługuje zestaw platform środowiska uruchomieniowego. Struktury opisano dostępne zestaw interfejsów API (i potencjalnie innych parametrów) czy użytkownik może wykorzystywać podczas target framework danego. Są one określonej wersji w miarę dodawania nowych interfejsów API.

Na przykład [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) obsługuje następujące struktury:

- . NETFramework, Version = 4.6
- . Krótkich nazw NETStandard, Version = 1,3
- 6 platformy Xamarin (na przykład xamarinios10)

Warto natomiast dwa pierwsze z tych struktur, ponieważ są one przykłady dwa różne sposoby zdefiniowania struktury.

`.NETFramework,Version=4.6` Framework reprezentuje dostępnych interfejsów API w .NET Framework 4.6. Możesz utworzyć różne bibliotek skompilowana przy użyciu programu .NET Framework 4.6 zestawów odwołań, a następnie rozpowszechnić te biblioteki w pakietach NuGet w folderze net46 lib. Będzie używany dla aplikacji, których docelowe .NET Framework 4.6 lub które są zgodne z nim. Jest to sposób tradycyjnie pracowali wszystkich platform.

`.NETStandard,Version=1.3` Framework to struktura na podstawie pakietu. Jest zależne od pakietów przeznaczonych dla framework do definiowania i uwidacznia interfejsów API w ramach.

## <a name="package-based-frameworks"></a>Na podstawie pakietu struktury

Istnieje relacja dwukierunkowego między platform i pakietów. Pierwsza część jest zdefiniowanie z interfejsami API dostępnymi dla danej platformy, na przykład `netstandard1.3`. Pakietów kierowanych `netstandard1.3` (lub zgodne platform, takich jak `netstandard1.0`) zdefiniowanie z interfejsami API dostępnymi dla `netstandard1.3`. Który może dźwiękowej jak definicję cykliczną, ale nie jest. Na podstawie stanowi "na podstawie pakietu", definicję interfejsu API w ramach pochodzi z pakietów. Platformę sam nie definiuje żadnych interfejsów API.

Druga część relacji to wybór trwały. Pakiety mogą zawierać zasobów dla wielu struktur. Podane odwołanie do zestawu pakiety i/lub metapackages, platformę są potrzebne, aby określić, którego zasobu należy wybrać, na przykład `net46` lub `netstandard1.3`. Należy wybrać poprawny zasobów. Na przykład `net46` zasobów prawdopodobnie nie był zgodny z programu .NET Framework 4.0 lub .NET Core 1.0.

![Struktura oparta na pakiecie kompozycji](./media/packages/package-framework.png)

Widać tę relację na ilustracji powyżej. *Interfejsu API* elementów docelowych i definiuje *framework*. *Framework* służy do *wybór trwały*. *Zasobów* umożliwia interfejsu API.

Są dwa podstawowe na podstawie pakietu struktury używane z platformą .NET Core:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET standard

.NET Standard (target framework moniker: `netstandard`) framework reprezentuje interfejsów API zdefiniowany przez i oparty na [.NET Standard](../standard/net-standard.md). Bibliotek, które są przeznaczone do uruchamiania na wiele środowisk uruchomieniowych powinna wskazywać platforma. Będą one obsługiwane na standardowe .NET runtime zgodne, takich jak .NET Core, .NET Framework i Mono/Xamarin. Każdy z tych środowisk uruchomieniowych obsługuje zestaw .NET Standard wersji, w zależności od tego, które interfejsy API wdrażania.

`netstandard` Framework niejawnie odwołuje się do [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) metapackage. Na przykład następujący plik projektu programu MSBuild wskazuje, że elementy docelowe projektu `netstandard1.6`, które odwołania [ `NETStandard.Library` wersji 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) metapackage.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Jednak framework i metapackage odwołania w pliku projektu musi być zgodny i można użyć `<NetStandardImplicitPackageVersion>` elementu w pliku projektu, aby określić framework w wersji, która jest starsza niż wersja metapackage. Na przykład następujący plik projektu jest nieprawidłowa.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Może wydawać się dziwne do docelowego `netstandard1.3` , ale 1.6.0 wersji `NETStandard.Library`. Jest nieprawidłowy przypadek użycia, ponieważ metapackage zapewnia obsługę starszych `netstandard` wersji. Może to być case już standaryzowane do 1.6.0 wersji metapackage i użyć jej do wszystkich bibliotek, które są docelowo różnych `netstandard` wersji. Z tej metody, wystarczy przywrócić `NETStandard.Library` 1.6.0 i nie starszych wersji. 

Sytuacja odwrotna nie jest prawidłowym: przeznaczonych dla `netstandard1.6` z 1.3.0 wersji `NETStandard.Library`. Wyższy framework z niższym metapackage, nie może wskazać, ponieważ niższe metapackage wersji nie powoduje to udostępnienie wszystkie zasoby dla tej struktury wyższy. Przechowywanie wersji systemu metapackages potwierdza, czy metapackages pasuje do najwyższej wersji framework, które opisano w nich. Z systemu kontroli wersji, pierwszej wersji `NETStandard.Library` jest v1.6.0, biorąc pod uwagę, że zawiera on `netstandard1.6` zasoby. V1.3.0 jest używany w powyższym przykładzie dla symetrycznego z powyższym przykładzie, ale faktycznie nie istnieje.

### <a name="net-core-application"></a>Aplikacja programu .NET core

Aplikacja .NET Core (TFM: `netcoreapp`) reprezentuje framework pakietów i skojarzone interfejsy API, które są dostarczane z dystrybucji .NET Core i model aplikacji konsoli, która zapewnia. Aplikacje .NET core muszą używać tej platformy, z powodu przeznaczonych dla modelu aplikacji konsoli, jak biblioteki, w których jest przeznaczony do uruchamiania tylko na platformy .NET Core. Przy użyciu tej platformy, ogranicza aplikacji i bibliotek uruchomiona tylko na platformy .NET Core. 

`Microsoft.NETCore.App` Celów metapackage `netcoreapp` framework. Zapewnia dostęp do biblioteki ~ 60 ~ 40 dostarczonych przez `NETStandard.Library` pakietu i ~ 20 więcej w dodatku. Można odwoływać się do dodatkowych bibliotek przeznaczonych `netcoreapp` lub zgodne struktur, takich jak `netstandard`, aby uzyskać dostęp do dodatkowych interfejsów API. 

Większość dodatkowe biblioteki udostępnione przez `Microsoft.NETCore.App` również kierować `netstandard` biorąc pod uwagę, że ich zależności w innych `netstandard` biblioteki. Oznacza to, że `netstandard` biblioteki można także odwoływać tych pakietów jako zależności. 
