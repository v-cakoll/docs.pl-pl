---
title: .NET standard
description: Więcej informacji na temat platformy .NET Standard, jego wersji i implementacje platformy .NET, które go obsługują.
author: mairaw
ms.author: mairaw
ms.date: 07/19/2018
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 91dbbefd247b5e175da7dc3560b6323cbec1972b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892181"
---
# <a name="net-standard"></a>.NET standard

[.NET Standard](https://github.com/dotnet/standard) jest formalną specyfikację interfejsów API platformy .NET, które mają być dostępne na wszystkich implementacji .NET. Motywacją za .NET Standard jest ustanowienie większej jednolitości należący do ekosystemu platformy .NET. [ECMA-335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) ustanowić jednolitość do zachowania w zakresie implementacji .NET, w dalszym ciągu, ale nie ma żadnych podobne specyfikacji dla platformy .NET podstawowej klasy biblioteki (BCL) dla implementacji biblioteki .NET.

.NET Standard umożliwia realizację następujących głównych scenariuszy:

- Definiuje zestaw jednolitych BCL interfejsy API dla wszystkich implementacji .NET, aby zaimplementować, niezależnie od obciążenia.
- Umożliwia deweloperom tworzenia bibliotek przenośnych, które nadają się do różnych implementacji platformy .NET, przy użyciu tego samego zestawu interfejsów API.
- Zmniejsza lub nawet eliminuje warunkowa źródłowy udostępniony z powodu interfejsów API platformy .NET, tylko w przypadku interfejsów API systemu operacyjnego.

Różne implementacje platformy .NET docelowych określonych wersji programu .NET Standard. Każda wersja implementacji .NET anonsuje najwyższy .NET Standard wersję, którą obsługuje ona instrukcję, która oznacza, że obsługuje również poprzednich wersji. Na przykład .NET Framework 4.6 implementuje standardowe 1.3 .NET, co oznacza, że udostępnia wszystkie interfejsy API zdefiniowany w .NET Standard wersji 1.0 za pośrednictwem 1.3. Podobnie .NET Framework 4.6.1 implementuje .NET Standard 1.4, podczas gdy platformy .NET Core 1.0 implementuje .NET Standard w wersji 1.6.

## <a name="net-implementation-support"></a>Obsługa wdrażania platformy .NET

W poniższej tabeli wymieniono wersje minimalną platformy, które obsługują każdej wersji .NET Standard.

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Aby znaleźć najnowsza wersja programu .NET Standard, możesz wybrać docelową, wykonaj następujące czynności:

1. Znajdź wiersz, który wskazuje implementacji .NET, który chcesz uruchomić na.
2. Znajdź kolumny w tym wierszu, wskazująca Twojej wersji od prawej do lewej.
3. Nagłówek kolumny wskazuje wersję .NET Standard, która obsługuje docelowego (i wszystkie niższe wersje .NET Standard będzie obsługiwać ją również).
4. Powtórz ten proces dla każdej platformy, która ma pod kątem. Jeśli masz więcej niż jedną platformę docelową, należy wybrać mniejsze wersji między nimi. Na przykład jeśli chcesz uruchomić w .NET Framework 4.5 i .NET Core 1.0 najwyższa wersja .NET Standard, których można użyć jest .NET Standard 1.1.

### <a name="which-net-standard-version-to-target"></a>Która wersja .NET Standard do obiektu docelowego

Podczas wybierania wersji .NET Standard, należy rozważyć takie rozwiązanie:

- Im wyższa wersja więcej interfejsów API dostępnych dla Ciebie.
- Im niższa wersji, więcej platform go zaimplementować.

Ogólnie rzecz biorąc, firma Microsoft zaleca pod kątem *najniższy* wersji programu .NET Standard to możliwe. Dlatego po znalezieniu najwyższa wersja .NET Standard, którą można wskazać, wykonaj następujące kroki:

1. Docelowa dalej starszej wersji programu .NET Standard i skompiluj projekt.
2. Jeśli projekt jest kompilowany pomyślnie, powtórz krok 1. W przeciwnym razie Przekieruj do następnej wersji wyższej, a to wersja, do której należy użyć.

### <a name="net-standard-versioning-rules"></a>.NET standard reguły kontroli wersji

Istnieją dwie reguły głównej wersji:

- Dodatek: .NET w wersji Standard są logicznie koncentrycznych: nowsze wersje zawierają wszystkie interfejsy API z poprzednich wersji. Brak żadnych istotnych zmian między wersjami.
- Niezmienne: Raz wysłany, wersje .NET Standard są zablokowane. Nowe interfejsy API najpierw staną się dostępne w określonej implementacji .NET, takich jak .NET Core. .NET Standard tablicy przeglądu wierzy, że nowe interfejsy API powinna być dostępna dla wszystkich implementacje platformy .NET, są one dodawane w nowej wersji .NET Standard.

## <a name="specification"></a>Specyfikacja

Specyfikacji .NET Standard to standardowy zestaw interfejsów API. Specyfikacja jest obsługiwana przez implementors .NET, w szczególności Microsoft (w tym .NET Framework, .NET Core i platformy Mono) i Unity. Proces publicznych opinii jest używany jako część ustanawianie nowe wersje .NET Standard za pomocą [GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficjalna artefaktów

Oficjalna specyfikacji to zbiór plików .cs, które definiują interfejsów API, które są częścią standardu. [Katalogu ref](https://github.com/dotnet/standard/tree/master/netstandard/ref) w [repozytorium dotnet/standard](https://github.com/dotnet/standard) definiuje standardowych interfejsów API platformy .NET.

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) meta Microsoft.aspnetcore.all ([źródła](https://github.com/dotnet/standard/blob/master/netstandard/pkg/NETStandard.Library.dependencies.props)) w tym artykule opisano zestaw bibliotek, które definiują (częściowo) przynajmniej jednej wersji .NET Standard.

A biorąc pod uwagę składników, takich jak `System.Runtime`, w tym artykule opisano:

- Część .NET Standard (tylko jego zakres).
- Wiele wersji programu .NET Standard, dla tego zakresu.

Pochodne artefakty znajdują się umożliwiające odczyt bardziej wygodne i niektórych scenariuszy dla deweloperów (np. przy użyciu kompilatora).

- [Listy interfejsów API w języku znaczników markdown](https://github.com/dotnet/standard/tree/master/docs/versions)
- Odwołuje się do zestawów, dystrybuowanych jako [pakiety NuGet](../core/packages.md) i odwołuje [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) meta Microsoft.aspnetcore.all.

### <a name="package-representation"></a>Reprezentacja pakietu

Podstawowy dystrybucji można przeprowadzić przy użyciu .NET Standard zestawy odwołań [pakiety NuGet](../core/packages.md). Implementacje są dostarczane w na różne sposoby, odpowiednia dla każdej implementacji .NET.

Pakiety NuGet docelowe co najmniej jeden [struktur](frameworks.md). Pakiety .NET Standard docelowy framework ".NET Standard". Możesz wybrać docelową .NET Standard przy użyciu framework `netstandard` [compact TFM](frameworks.md) (na przykład `netstandard1.4`). Bibliotek, które są przeznaczone do uruchamiania na wielu modułów wykonawczych powinien dotyczyć ten framework. Dla największego zestawu interfejsów API, docelowa `netstandard2.0` ponieważ liczba dostępnych interfejsów API ponad dwukrotnie między .NET Standard w wersji 1.6 i w wersji 2.0.

[ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library/) Meta Microsoft.aspnetcore.all odwołuje się do pełnego zestawu pakietów NuGet, które definiują .NET Standard.  Najczęstszym sposobem docelowej `netstandard` jest, odwołując się do tego meta Microsoft.aspnetcore.all. Jej opis i zapewnia dostęp do bibliotek .NET około 40 i skojarzone interfejsy API, które definiują .NET Standard. Dodatkowe pakiety można odwoływać się przeznaczonych `netstandard` uzyskać dostęp do dodatkowych interfejsów API.

### <a name="versioning"></a>Przechowywanie wersji

Specyfikacja nie jest liczbie pojedynczej, ale w przyrostowo stałym wzbogacaniu i liniowo określonej wersji zestawu interfejsów API. Pierwsza wersja standard ustanawia zbiór interfejsów API w linii bazowej. Kolejne wersje dodawanie interfejsów API i dziedziczą zdefiniowane przez poprzednie wersje interfejsów API. Istnieje ustanowionych usuwania interfejsów API niż standardowe.

.NET standard nie jest specyficzna dla jednej implementacji .NET nie jest zgodna schematu przechowywania wersji któregokolwiek z tych środowisk uruchomieniowych.

Interfejsy API dodawane do dowolnej z implementacji (na przykład, .NET Framework, .NET Core i platformy Mono) może być traktowany jako kandydatów do dodania do specyfikacji, szczególnie w przypadku, gdy ich są uznawane za podstawowe charakter. Nowe [wersje programu .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) są tworzone w oparciu o wersjach implementacji .NET, dzięki któremu można pod kątem nowych interfejsów API z aplikacji PCL .NET Standard. Mechanika versioning są opisane bardziej szczegółowo w [przechowywanie wersji programu .NET Core](../core/versions/index.md).

Przechowywanie wersji .NET standard jest ważne w przypadku użycia. Podana wersja .NET Standard, można użyć bibliotek przeznaczonych do tego samego lub niższego wersji. Następujące podejście opisuje przepływ pracy dotyczący używania .NET Standard PCLs, specyficzne dla platformy .NET Standard.

- Wybierz wersję .NET Standard do użycia dla swojej aplikacji PCL.
- Korzystać z bibliotek, które są zależne, w tej samej wersji .NET Standard lub niższą.
- Jeśli okaże się bibliotekę, która jest zależna od nowszej wersji .NET Standard, albo należy przyjąć tej samej wersji, lub zrezygnować z tej biblioteki.

## <a name="targeting-net-standard"></a>Przeznaczone dla platformy .NET Standard

Możesz [tworzenia standardowych bibliotek .NET](../core/tutorials/libraries.md) przy użyciu kombinacji `netstandard` framework i meta Microsoft.aspnetcore.all NETStandard.Library. Należy zapoznać się z przykładami [przeznaczonych dla platformy .NET Standard z narzędziami .NET Core](../core/packages.md).

## <a name="net-framework-compatibility-mode"></a>Tryb zgodności w programie .NET framework

Począwszy od .NET Standard 2.0 wprowadzono tryb zgodności w programie .NET Framework. Ten tryb zgodności umożliwia projektów .NET Standard do odwołania do bibliotek .NET Framework tak, jakby były one skompilowane dla platformy .NET Standard. Odwołujące się do bibliotek .NET Framework nie działa dla wszystkich projektów, takich jak biblioteki, które używają Windows Presentation Foundation (WPF) interfejsów API.

Aby uzyskać więcej informacji, zobacz [.NET Framework w trybie zgodności](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Biblioteki .NET standard oraz programu Visual Studio

Aby można było utworzyć biblioteki .NET Standard w programie Visual Studio, upewnij się, [programu Visual Studio 2017 w wersji 15.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) na Windows, lub nowszej lub [programu Visual Studio dla komputerów Mac w wersji 7.1](https://visualstudio.microsoft.com/vs/visual-studio-mac/) na lub nowszej z systemem macOS.

Jeśli musisz korzystać z bibliotek .NET Standard 2.0 w projektach, możesz także zrobić to w programie Visual Studio 2015. Należy jednak NuGet zainstalowany klient 3.6 lub nowszej. Możesz pobrać klienta programu NuGet dla programu Visual Studio 2015 z [NuGet pobiera](https://www.nuget.org/downloads) strony.

## <a name="comparison-to-portable-class-libraries"></a>Porównanie z biblioteki klas przenośnych

.NET standard jest zastępczych dla [biblioteki klas przenośnych (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard ulepsza środowisko tworzenia bibliotek przenośnych curating BCL standardowe i ustanowienie większej jednolitości implementacje platformy .NET w wyniku. Biblioteki, który jest przeznaczony dla .NET Standard jest aplikacji PCL lub ".NET oparta na standardach aplikacji PCL". Istniejące PCLs są "PCLs oparte na profilu".

Profile platformy .NET standard i PCL zostały utworzone w celach podobnych, ale różnią się także w sposób kluczy.

Podobieństwa:

- Definiowanie interfejsów API, który może służyć do udostępniania kodu binarnego.

Różnice:

- .NET standard jest wyselekcjonowany zestaw interfejsów API, natomiast PCL profile są definiowane przez przecięcia z istniejącymi platformami.
- .NET standard liniowo wersji, gdy nie obsługują profile aplikacji PCL.
- Profile aplikacji PCL reprezentuje platformy Microsoft .NET Standard jest niezależne od platformy.

### <a name="pcl-compatibility"></a>Zgodność aplikacji PCL

.NET standard jest zgodny z podzbiorem PCL profilów. .NET standard w wersji 1.0, 1.1 i 1.2 każdego nakładają się na zbiór profilów PCL. To nakładanie został utworzony z dwóch przyczyn:

- Włącz .NET Standard na podstawie PCLs k odkazu PCLs oparte na profilu.
- Włącz na podstawie profilu PCLs pod PCLs oparte na .NET Standard.

Na podstawie profilu zgodności PCL są dostarczane przez [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) pakietu NuGet. Ta zależność jest wymagana podczas odwoływania się do pakietów NuGet, zawierające PCLs oparte na profilu.

Na podstawie profilu PCLs spakowany jako `netstandard` są łatwiejsze korzystanie z niż zazwyczaj umieszczonych PCLs oparte na profilu. `netstandard` pakowanie jest zgodny z istniejącym użytkownikom.

Możesz wyświetlić zestaw PCL profilów, które są zgodne z .NET Standard:

| Profil PCL | .NET standard | Platformy aplikacji PCL
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET framework 4.5, Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | .NET framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | .NET framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8

## <a name="see-also"></a>Zobacz także

- [Wersje programu .NET standard](https://github.com/dotnet/standard/blob/master/docs/versions.md)
