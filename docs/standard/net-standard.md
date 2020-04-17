---
title: .NET Standard
description: Dowiedz się więcej o .NET Standard, jego wersjach i implementacjach platformy .NET, które go obsługują.
ms.date: 02/13/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 34074b420547cff802f1835656540be7b8eb58b4
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607483"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) to formalna specyfikacja interfejsów API platformy .NET, które mają być dostępne we wszystkich implementacjach platformy .NET. Motywacją .NET Standard jest ustanowienie większej jednolitości w ekosystemie .NET. [ECMA 335](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) nadal ustanawia jednorodność zachowania implementacji platformy .NET, a podczas gdy ECMA 335 określa mały zestaw standardowych bibliotek, specyfikacja .NET Standard obejmuje szerszy zakres interfejsów API platformy .NET.

Program .NET Standard umożliwia następujące kluczowe scenariusze:

- Definiuje jednolity zestaw interfejsów API BCL dla wszystkich implementacji platformy .NET do zaimplementowania, niezależnie od obciążenia.
- Umożliwia deweloperom tworzenie bibliotek przenośnych, które są używane w implementacjach platformy .NET przy użyciu tego samego zestawu interfejsów API.
- Zmniejsza lub nawet eliminuje kompilacji warunkowej źródła udostępnionego z powodu interfejsów API platformy .NET, tylko dla interfejsów API systemu operacyjnego.

Różne implementacje platformy .NET są przeznaczone dla określonych wersji programu .NET Standard. Każda wersja implementacji platformy .NET anonsuje najwyższą wersję .NET Standard, którą obsługuje, instrukcję, która oznacza, że obsługuje również poprzednie wersje. Na przykład .NET Framework 4.6 implementuje .NET Standard 1.3, co oznacza, że udostępnia wszystkie interfejsy API zdefiniowane w .NET Standard w wersjach 1.0 do 1.3. Podobnie program .NET Framework 4.6.1 implementuje standard .NET Standard 1.4, podczas gdy program .NET Core 1.0 implementuje standard .NET Standard 1.6.

## <a name="net-implementation-support"></a>Pomoc techniczna w zakresie implementacji platformy .NET

W poniższej tabeli wymieniono **minimalne** wersje platformy obsługujące każdą wersję standardu .NET. Oznacza to, że nowsze wersje wymienionej platformy obsługują również odpowiednią wersję standardu .NET. Na przykład .NET Core 2.2 obsługuje .NET Standard 2.0 i starsze.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Aby znaleźć najwyższą wersję standardu .NET, na którą można kierować reklamy, wykonaj następujące czynności:

1. Znajdź wiersz wskazujący implementację platformy .NET, na której chcesz uruchomić.
2. Znajdź kolumnę w tym wierszu, która wskazuje wersję, zaczynając od prawej do lewej.
3. Nagłówek kolumny wskazuje wersję .NET Standard, którą obsługuje obiekt docelowy. Można również kierować dowolną niższą wersję standardu .NET. Wyższe wersje .NET Standard będą również obsługiwać implementację.
4. Powtórz ten proces dla każdej platformy, na którą chcesz kierować reklamy. Jeśli masz więcej niż jedną platformę docelową, powinieneś wybrać mniejszą wersję spośród nich. Na przykład jeśli chcesz uruchomić w programie .NET Framework 4.5 i .NET Core 1.0, najwyższą wersją .NET Standard, której można użyć, jest .NET Standard 1.1.

### <a name="which-net-standard-version-to-target"></a>Która wersja .NET Standard ma być kierowana

Wybierając wersję standardową .NET, należy wziąć pod uwagę ten kompromis:

- Im wyższa wersja, tym więcej interfejsów API jest dostępnych.
- Im niższa wersja, tym więcej platform ją implementuje.

Ogólnie rzecz biorąc zaleca się, aby kierować *najniższą* możliwą wersję programu .NET Standard. Tak więc po znalezieniu najwyższej wersji .NET Standard, na którą możesz kierować reklamy, wykonaj następujące kroki:

1. Kieruj reklamy na następną niższą wersję programu .NET Standard i skompiluj projekt.
2. Jeśli projekt zostanie pomyślnie skompilowy, powtórz krok 1. W przeciwnym razie retarget do następnej wyższej wersji i to jest wersja, której należy użyć.

Jednak kierowanie niższe wersje .NET Standard wprowadza szereg zależności pomocy technicznej. Jeśli projekt jest przeznaczony dla platformy .NET Standard 1.x, zaleca się *również* kierowanie na program .NET Standard 2.0. Upraszcza to wykres zależności dla użytkowników biblioteki, którzy są uruchamiane w ramach zgodnych z programem .NET Standard 2.0 i zmniejsza liczbę pakietów, które muszą pobrać.

### <a name="net-standard-versioning-rules"></a>Reguły przechowywania wersji .NET Standard

Istnieją dwie podstawowe reguły przechowywania wersji:

- Dodatek: .NET Wersje standardowe są logicznie koncentryczne okręgi: wyższe wersje zawierają wszystkie interfejsy API z poprzednich wersji. Nie ma żadnych przełomowych zmian między wersjami.
- Niezmienne: Po wysłaniu wersje .NET Standard są zamrażane. Nowe interfejsy API stają się najpierw dostępne w określonych implementacjach platformy .NET, takich jak .NET Core. Jeśli rada opinii .NET Standard uważa, że nowe interfejsy API powinny być dostępne dla wszystkich implementacji platformy .NET, są dodawane w nowej wersji standardu platformy .NET.

## <a name="specification"></a>Specyfikacja

Specyfikacja .NET Standard jest znormalizowanym zestawem interfejsów API. Specyfikacja jest obsługiwana przez implementatory platformy .NET, w szczególności firmy Microsoft (w tym .NET Framework, .NET Core i Mono) i Unity. Publiczny proces opinii jest używany jako część tworzenia nowych wersji .NET Standard za pośrednictwem [gitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficjalne artefakty

Oficjalna specyfikacja to zestaw plików .cs definiujących interfejsy API, które są częścią standardu. Katalog [ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) w [repozytorium dotnet/standard](https://github.com/dotnet/standard) definiuje standardowe interfejsy API platformy .NET.

[NetStandard.Library](https://www.nuget.org/packages/NETStandard.Library) metapackage ([źródło](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) opisuje zestaw bibliotek, które definiują (częściowo) jedną lub więcej wersji .NET Standard.

Dany składnik, `System.Runtime`jak , opisuje:

- Część .NET Standard (tylko jego zakres).
- Wiele wersji programu .NET Standard dla tego zakresu.

Artefakty pochodne są dostarczane w celu umożliwienia bardziej wygodne czytanie i włączyć niektóre scenariusze dewelopera (na przykład przy użyciu kompilatora).

- [Lista API w obniżce](https://github.com/dotnet/standard/tree/master/docs/versions)
- Zestawy odwołań, dystrybuowane jako [pakiety NuGet](../core/packages.md) i odwołuje [się do netstandard.Library](https://www.nuget.org/packages/NETStandard.Library/) metapackage.

### <a name="package-representation"></a>Reprezentacja pakietów

Podstawowym pojazdem dystrybucji dla zestawów referencyjnych .NET Standard są [pakiety NuGet](../core/packages.md). Implementacje są dostarczane na różne sposoby, odpowiednie dla każdej implementacji platformy .NET.

Pakiety NuGet są przeznaczone dla jednej lub więcej [struktur.](frameworks.md) Pakiety .NET Standard są przeznaczone dla struktury ".NET Standard". Można kierować platformę .NET `netstandard` Standard framework przy użyciu `netstandard1.4` [kompaktowego TFM](frameworks.md) (na przykład ). Biblioteki, które są przeznaczone do uruchamiania w wielu środowiskach uruchomieniowych należy kierować tej struktury. W przypadku najszerszego zestawu interfejsów `netstandard2.0` API obiekt docelowy, ponieważ liczba dostępnych interfejsów API wzrosła ponad dwukrotnie między standardem .NET 1.6 a 2.0.

Metapakiet [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) odwołuje się do pełnego zestawu pakietów NuGet, które definiują .NET Standard.  Najczęstszym sposobem kierowania `netstandard` jest odwoływanie się do tego metapakiety. Opisuje i zapewnia dostęp do bibliotek .NET ~40 i skojarzonych interfejsów API definiujących standard .NET. Można odwoływać się `netstandard` do dodatkowych pakietów, które docelowe, aby uzyskać dostęp do dodatkowych interfejsów API.

### <a name="versioning"></a>Przechowywanie wersji

Specyfikacja nie jest pojedyncza, ale przyrostowo rosnący i liniowo wersjonalnie wersjona zestaw interfejsów API. Pierwsza wersja standardu ustanawia zestaw bazowy interfejsów API. Kolejne wersje dodają interfejsy API i dziedziczą interfejsy API zdefiniowane przez poprzednie wersje. Nie ma ustalonego przepisu na usunięcie interfejsów API ze standardu.

.NET Standard nie jest specyficzne dla jednej implementacji .NET, ani nie pasuje do schematu przechowywania wersji któregokolwiek z tych środowiska wykonawczego.

Interfejsy API dodane do dowolnej implementacji (takie jak .NET Framework, .NET Core i Mono) można uznać za kandydatów do dodania do specyfikacji, szczególnie jeśli są one uważane za podstawowe. Nowe [wersje programu .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) są tworzone na podstawie wersji implementacji platformy .NET, co umożliwia kierowanie nowych interfejsów API ze standardu .NET PCL. Mechanika przechowywania wersji jest opisana bardziej szczegółowo w [wersji .NET Core.](../core/versions/index.md)

.NET Wersja standardowa jest ważna dla użycia. Biorąc pod uwagę wersję .NET Standard, można użyć bibliotek, które są przeznaczone dla tej samej lub niższej wersji. W poniższym podejściu opisano przepływ pracy przy użyciu .NET Standardowe listy PCL, specyficzne dla .NET Standard targeting.

- Wybierz wersję standardową platformy .NET, która będzie używana dla pcl.
- Użyj bibliotek, które zależą od tej samej wersji .NET Standard lub niższej.
- Jeśli znajdziesz bibliotekę, która zależy od wyższej wersji .NET Standard, musisz przyjąć tę samą wersję lub zdecydować, aby nie używać tej biblioteki.

## <a name="target-net-standard"></a>Docelowy standard .NET

[Biblioteki standardowe platformy .NET](../core/tutorials/libraries.md) można tworzyć `netstandard` przy użyciu kombinacji struktury i sieci NETStandard.Library. Przykłady kierowania .NET Standard za [pomocą narzędzi .NET Core](../core/packages.md)można zobaczyć .

## <a name="net-framework-compatibility-mode"></a>Tryb zgodności programu .NET Framework

Począwszy od .NET Standard 2.0, wprowadzono tryb zgodności programu .NET Framework. Ten tryb zgodności umożliwia projektom .NET Standard odwoływanie się do bibliotek programu .NET Framework tak, jakby zostały skompilowane dla platformy .NET Standard. Odwoływanie się do bibliotek programu .NET Framework nie działa dla wszystkich projektów, takich jak biblioteki korzystające z interfejsów API programu Windows Presentation Foundation (WPF).

Aby uzyskać więcej informacji, zobacz [tryb zgodności programu .NET Framework](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Biblioteki .NET Standard i visual studio

Aby utworzyć biblioteki .NET Standard w programie Visual Studio, upewnij się, że w systemie macOS zainstalowano [program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub Visual Studio 2017 w wersji 15.3 lub nowszej. [Visual Studio for Mac version 7.1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Jeśli wystarczy używać bibliotek .NET Standard 2.0 w projektach, można to również zrobić w programie Visual Studio 2015. Jednak należy nuget klienta 3.6 lub nowsze zainstalowane. Klienta NuGet dla programu Visual Studio 2015 można pobrać ze strony [pobierania NuGet.](https://www.nuget.org/downloads)

## <a name="comparison-to-portable-class-libraries"></a>Porównanie z przenośnymi bibliotekami klas

Program .NET Standard zastępuje [przenośne biblioteki klas (PCL).](./cross-platform/cross-platform-development-with-the-portable-class-library.md) .NET Standard poprawia doświadczenie tworzenia bibliotek przenośnych przez kuratorowanie standardowej listy BCL i ustanowienie większej jednolitości implementacji .NET w wyniku. Biblioteka przeznaczona dla platformy .NET Standard to PCL lub ".NET Standard-based PCL". Istniejące listy PCL to "pcls oparte na profilach".

Profile .NET Standard i PCL zostały utworzone w podobnych celach, ale różnią się również kluczowymi sposobami.

Podobieństwa:

- Zdefiniuj interfejsy API, które mogą być używane do binarnego udostępniania kodu.

Różnice:

- .NET Standard jest wyselekcjonowanym zestawem interfejsów API, podczas gdy profile PCL są definiowane przez przecięcia istniejących platform.
- .NET Standardowe wersje liniowe, podczas gdy profile PCL nie.
- Profile PCL reprezentują platformy firmy Microsoft, podczas gdy program .NET Standard jest niezależny od platformy.

### <a name="pcl-compatibility"></a>Zgodność z PCL

Program .NET Standard jest zgodny z podzbiorem profili PCL. .NET Standard 1.0, 1.1 i 1.2 nakładają się na zestaw profili PCL. To nakładanie się utworzono z dwóch powodów:

- Włącz standardowe listy PCLs .NET, aby odwoływać się do list PCL opartych na profilach.
- Włącz profile PCLs mają być pakowane jako .NET Standard PCLs.

Zgodność pcl oparta na profilu jest dostarczana przez pakiet [NuGet firmy Microsoft.NETCore.Portable.Compatibility.](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) Ta zależność jest wymagana podczas odwoływania się do pakietów NuGet, które zawierają listy PCLs oparte na profilu.

Listy PCLs oparte na `netstandard` profilach są pakowane, ponieważ są łatwiejsze w korzystanie niż zazwyczaj spakowane listy PCL oparte na profilu. `netstandard`opakowania są kompatybilne z istniejącymi użytkownikami.

Możesz zobaczyć zestaw profili PCL zgodnych z programem .NET Standard:

| Profil PCL | .NET Standard | Platformy PCL
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profil7    | 1.1           | .NET Framework 4.5, Windows 8
| Profil31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profil32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profil44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profil49   | 1.0           | .NET Framework 4.5, Windows Phone Silverlight 8
| Profil78   | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profil84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profil111  | 1.1           | .NET Framework 4.5, Windows 8, Windows Phone 8.1
| Profil151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profil157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profil259  | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8

## <a name="see-also"></a>Zobacz też

- [Wersje standardowe platformy .NET](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [Tworzenie biblioteki standardowej platformy .NET](../core/tutorials/library-with-visual-studio.md)
- [Obsługiwane rozwiązania międzyplatformowe](./library-guidance/cross-platform-targeting.md)
