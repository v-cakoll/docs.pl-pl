---
title: .NET Standard
description: Dowiedz się więcej o .NET Standard, jego wersjach i implementacjach .NET, które go obsługują.
ms.date: 02/13/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 00b40b771a8608bad7e3f992e3c99367ff6bb131
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452594"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) to formalna specyfikacja interfejsów API .NET, które mają być dostępne we wszystkich implementacjach .NET. Motywacją .NET Standard jest ustanowienie większej jednolitości w ekosystemie .NET. [ECMA 335](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) nadal ustanawia jednorodność zachowania implementacji .NET, a gdy ECMA 335 określa mały zestaw bibliotek standardowych, specyfikacja .NET Standard obejmuje szerszy zakres interfejsów API .NET.

Program .NET Standard umożliwia następujące kluczowe scenariusze:

- Definiuje jednolity zestaw interfejsów API BCL dla wszystkich implementacji platformy .NET do zaimplementowania, niezależnie od obciążenia.
- Umożliwia deweloperom tworzenie przenośnych bibliotek, które są użyteczne w implementacjach platformy .NET przy użyciu tego samego zestawu interfejsów API.
- Zmniejsza lub nawet eliminuje kompilacji warunkowej udostępnionego źródła z powodu interfejsów API .NET, tylko dla interfejsów API os.

Różne implementacje .NET są przeznaczone dla określonych wersji standardu .NET. Każda wersja implementacji .NET anonsuje najwyższą wersję .NET Standard, która obsługuje, instrukcja, która oznacza, że obsługuje również poprzednie wersje. Na przykład .NET Framework 4.6 implementuje .NET Standard 1.3, co oznacza, że udostępnia wszystkie interfejsy API zdefiniowane w .NET Standard w wersji od 1.0 do 1.3. Podobnie .NET Framework 4.6.1 implementuje .NET Standard 1.4, podczas gdy .NET Core 1.0 implementuje .NET Standard 1.6.

## <a name="net-implementation-support"></a>Obsługa implementacji .NET

W poniższej tabeli wymieniono **minimalne** wersje platformy obsługujące każdą wersję standardową .NET. Oznacza to, że nowsze wersje wymienionej platformy obsługują również odpowiednią wersję .NET Standard. Na przykład .NET Core 2.2 obsługuje .NET Standard 2.0 i wcześniejszych.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Aby znaleźć najwyższą wersję programu .NET Standard, na którą można kierować reklamy, wykonaj następujące kroki:

1. Znajdź wiersz, który wskazuje implementację .NET, na której chcesz uruchomić.
2. Znajdź kolumnę w tym wierszu, która wskazuje wersję zaczynającą się od prawej do lewej.
3. Nagłówek kolumny wskazuje wersję standardową .NET, którą obsługuje obiekt docelowy. Można również kierować reklamy na dowolną niższą wersję standardową .NET. Wyższe wersje standardu .NET będą również obsługiwać implementację.
4. Powtórz ten proces dla każdej platformy, na którą chcesz kierować reklamy. Jeśli masz więcej niż jedną platformę docelową, należy wybrać mniejszą wersję wśród nich. Na przykład, jeśli chcesz uruchomić na .NET Framework 4.5 i .NET Core 1.0, najwyższa wersja .NET Standard, której można użyć, to .NET Standard 1.1.

### <a name="which-net-standard-version-to-target"></a>Do której programu .NET Standardowa ma być wersja docelowa

Wybierając wersję .NET Standard, należy wziąć pod uwagę ten kompromis:

- Im wyższa wersja, tym więcej interfejsów API są dostępne dla Ciebie.
- Im niższa wersja, tym więcej platform ją implementuje.

Ogólnie rzecz biorąc zaleca się kierować *najniższą* wersję .NET Standard możliwe. Po znalezieniu najwyższej wersji standardu .NET, na którą możesz kierować reklamy, wykonaj następujące kroki:

1. Kierowanie na następną dolną wersję programu .NET Standard i tworzenie projektu.
2. Jeśli projekt zostanie pomyślnie zbudowany, powtórz krok 1. W przeciwnym razie ponownie kierować do następnej wyższej wersji i jest to wersja, której należy użyć.

Jednak kierowanie na niższe wersje .NET Standard wprowadza szereg zależności pomocy technicznej. Jeśli projekt jest przeznaczony dla .NET Standard 1.x, zaleca się *również* kierowanie .NET Standard 2.0. Upraszcza to wykres zależności dla użytkowników biblioteki, które są uruchamiane na platformach zgodnych z .NET Standard 2.0 i zmniejsza liczbę pakietów potrzebnych do pobrania.

### <a name="net-standard-versioning-rules"></a>Reguły wersji standardowej .NET

Istnieją dwie podstawowe reguły przechowywanie wersji:

- Dodatek: Wersje standardu .NET są logicznie koncentrycznymi okręgami: wyższe wersje zawierają wszystkie interfejsy API z poprzednich wersji. Nie ma żadnych zmian krytycznych między wersjami.
- Niezmienny: Po wysłaniu wersje .NET Standard są zamrożone. Nowe interfejsy API po raz pierwszy stają się dostępne w określonych implementacjach .NET, takich jak .NET Core. Jeśli tablica przeglądowa .NET Standard uważa, że nowe interfejsy API powinny być dostępne dla wszystkich implementacji .NET, zostaną one dodane w nowej wersji .NET Standard.

## <a name="specification"></a>Specyfikacja

Specyfikacja standardu .NET jest znormalizowanym zestawem interfejsów API. Specyfikacja jest obsługiwana przez implementatorów platformy .NET, w szczególności firmy Microsoft (w tym .NET Framework, .NET Core i Mono) i Unity. Proces opinii publicznej jest używany w ramach tworzenia nowych wersji .NET Standard za pośrednictwem [usługi GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficjalne artefakty

Oficjalna specyfikacja jest zestawem plików .cs, które definiują interfejsy API, które są częścią standardu. [Katalog ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) w [repozytorium dotnet/standard](https://github.com/dotnet/standard) definiuje standardowe interfejsy API .NET.

[NetStandard.Library](https://www.nuget.org/packages/NETStandard.Library) metapackage[(źródło)](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)opisuje zestaw bibliotek, które definiują (w części) jedną lub więcej wersji .NET Standard.

Dany składnik, `System.Runtime`jak , opisuje:

- Część .NET Standard (tylko jego zakres).
- Wiele wersji programu .NET Standard dla tego zakresu.

Artefakty pochodne są dostarczane, aby umożliwić wygodniejsze odczytywanie i włączyć niektóre scenariusze dewelopera (na przykład przy użyciu kompilatora).

- [Lista interfejsu API w znaczniku](https://github.com/dotnet/standard/tree/master/docs/versions)
- Zestawy odwołań, dystrybuowane jako [pakiety NuGet](../core/packages.md) i odwołuje się [do metapakietu NETStandard.Library.](https://www.nuget.org/packages/NETStandard.Library/)

### <a name="package-representation"></a>Reprezentacja pakietów

Podstawowym nośnikiem dystrybucji dla zestawów referencyjnych .NET Standard są [pakiety NuGet](../core/packages.md). Implementacje są dostarczane na różne sposoby, odpowiednie dla każdej implementacji .NET.

Pakiety NuGet są przeznaczone dla co najmniej jednej [struktury.](frameworks.md) Pakiety standardu .NET są przeznaczone dla struktury ".NET Standard". Można kierować platformy .NET `netstandard` Standard przy użyciu [kompaktowego TFM](frameworks.md) (na `netstandard1.4`przykład). Biblioteki, które są przeznaczone do uruchamiania w wielu programach wykonywania powinny być przeznaczone dla tej struktury. Dla najszerszego zestawu interfejsów API docelowych, `netstandard2.0` ponieważ liczba dostępnych interfejsów API ponad dwukrotnie między .NET Standard 1.6 i 2.0.

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) Metapakiet odwołuje się do pełnego zestawu pakietów NuGet, które definiują standard .NET.  Najczęstszym sposobem `netstandard` nacelu jest odwoływanie się do tego metapakietu. Opisuje i zapewnia dostęp do ~40 bibliotek .NET i skojarzonych interfejsów API, które definiują .NET Standard. Można odwoływać się `netstandard` do dodatkowych pakietów, które są przeznaczone do uzyskania dostępu do dodatkowych interfejsów API.

### <a name="versioning"></a>Obsługa wersji

Specyfikacja nie jest pojedyncza, ale stopniowo rosnący i liniowo wersjonowany zestaw interfejsów API. Pierwsza wersja standardu ustanawia podstawowy zestaw interfejsów API. Kolejne wersje dodają interfejsy API i dziedziczą interfejsy API zdefiniowane przez poprzednie wersje. Nie ma ustalonego przepisu dotyczącego usuwania interfejsów API ze standardu.

.NET Standard nie jest specyficzne dla jednej implementacji .NET, ani nie pasuje do schematu wersji któregokolwiek z tych uruchomień.

Interfejsy API dodane do dowolnej implementacji (takie jak .NET Framework, .NET Core i Mono) można uznać za kandydatów do dodania do specyfikacji, szczególnie jeśli są one uważane za podstawowe w przyrodzie. Nowe [wersje programu .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) są tworzone na podstawie wersji implementacji .NET, co umożliwia kierowanie nowych interfejsów API z .NET Standard PCL. Mechanika wersji są opisane bardziej szczegółowo w [.NET Core Versioning](../core/versions/index.md).

Przechowywanie wersji standardu .NET jest ważne dla użycia. Biorąc pod uwagę .NET Standard, można użyć bibliotek, które są przeznaczone dla tej samej lub niższej wersji. W poniższym podejściu opisano przepływ pracy do używania standardowych list PCL .NET, specyficznych dla kierowania .NET Standard.

- Wybierz wersję standardową .NET, która będzie używana dla urządzenia PCL.
- Użyj bibliotek, które zależą od tej samej wersji .NET Standard lub niższej.
- Jeśli znajdziesz bibliotekę, która zależy od wyższej wersji .NET Standard, musisz przyjąć tę samą wersję lub zdecydować się nie używać tej biblioteki.

## <a name="targeting-net-standard"></a>Kierowanie na .NET Standard

Biblioteki [standardowe .NET](../core/tutorials/libraries.md) można tworzyć przy `netstandard` użyciu kombinacji struktury i metapakietu NETStandard.Library. Można zobaczyć przykłady [kierowania na standard .NET za pomocą narzędzi .NET Core](../core/packages.md).

## <a name="net-framework-compatibility-mode"></a>Tryb zgodności .NET Framework

Począwszy od .NET Standard 2.0 wprowadzono tryb zgodności .NET Framework. Ten tryb zgodności umożliwia projektom .NET Standard odwoływanie się do bibliotek .NET Framework tak, jakby zostały skompilowane dla programu .NET Standard. Odwoływanie się do bibliotek programu .NET Framework nie działa dla wszystkich projektów, takich jak biblioteki, które używają interfejsów API programu Windows Presentation Foundation (WPF).

Aby uzyskać więcej informacji, zobacz [tryb zgodności .NET Framework](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Biblioteki standardu .NET i program Visual Studio

Aby utworzyć biblioteki .NET Standard w programie Visual Studio, upewnij się, że w systemie Windows jest zainstalowany [program Visual Studio 2017 w wersji 15.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) lub nowszej lub Visual Studio dla komputerów Mac w [wersji 7.1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) lub nowszej.

Jeśli w projektach trzeba używać tylko bibliotek .NET Standard 2.0, można to zrobić również w programie Visual Studio 2015. Jednak trzeba NuGet klienta 3.6 lub wyższy zainstalowany. Możesz pobrać klienta NuGet dla programu Visual Studio 2015 ze strony [pliki do pobrania NuGet.](https://www.nuget.org/downloads)

## <a name="comparison-to-portable-class-libraries"></a>Porównanie z przenośnymi bibliotekami klas

.NET Standard zastępuje [przenośne biblioteki klas (PCL).](./cross-platform/cross-platform-development-with-the-portable-class-library.md) Standard .NET poprawia doświadczenie tworzenia bibliotek przenośnych przez kuratorowanie standardowego bcl i ustanowienie większej jednolitości implementacji .NET w wyniku. Biblioteka przeznaczona dla programu .NET Standard jest pcl lub ".NET Standard-based PCL". Istniejące listy PCLs to "profile oparte na pcls".

Profile .NET Standard i PCL zostały utworzone w podobnych celach, ale różnią się również kluczowymi sposobami.

Podobieństwa:

- Zdefiniuj interfejsy API, które mogą być używane do udostępniania kodu binarnego.

Różnice:

- .NET Standard to wyselekcjonowany zestaw interfejsów API, podczas gdy profile PCL są definiowane przez przecięcia istniejących platform.
- .NET Standard wersje liniowe, podczas gdy profile PCL nie.
- Profile PCL reprezentuje platformy firmy Microsoft, podczas gdy .NET Standard jest niezależne od platformy.

### <a name="pcl-compatibility"></a>Zgodność z PCL

.NET Standard jest zgodny z podzbiorem profili PCL. .NET Standard 1.0, 1.1 i 1.2 pokrywają się z zestawem profilów PCL. To nakładanie się zostało utworzone z dwóch powodów:

- Włącz listy PCL oparte na standardzie .NET, aby odwoływać się do list PCL opartych na profilu.
- Włącz listy PCL oparte na profilu, aby były pakowane jako listy PCL oparte na standardzie .NET.

Zgodna PCL oparta na profilu jest dostarczana przez pakiet [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet. Ta zależność jest wymagana podczas odwoływania się do pakietów NuGet, które zawierają listy PCL oparte na profilu.

Listy PCL oparte na `netstandard` profilu pakowane w sposób łatwiejszy w używań niż zwykle pakowane listy PCL oparte na profilu. `netstandard`opakowanie jest zgodne z istniejącymi użytkownikami.

Możesz zobaczyć zestaw profili PCL, które są zgodne ze standardem .NET:

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

- [Wersje standardowe .NET](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [Tworzenie biblioteki standardu .NET](../core/tutorials/library-with-visual-studio.md)
- [Obsługiwane rozwiązania międzyplatformowe](./library-guidance/cross-platform-targeting.md)
