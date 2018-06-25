---
title: .NET standard
description: Informacje o .NET Standard, jego wersje i implementacje .NET, które ją obsługują.
author: mairaw
ms.author: mairaw
ms.date: 05/18/2018
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 8f4490edfc06fcc3ec06daffdb0966ac9ee72e23
ms.sourcegitcommit: ceca5a1c027627abcca2767567703c3879f33325
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36298178"
---
# <a name="net-standard"></a>.NET standard

[.NET Standard](https://github.com/dotnet/standard) jest formalną specyfikację interfejsów API architektury .NET, które mają być dostępne na wszystkich implementacji .NET. Motywacją za .NET Standard jest ustanowienie większej jednolitości w ekosystemie .NET. [ECMA-335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) ustanowić jednolitość zachowania implementacji .NET, w dalszym ciągu, ale nie specyfikacji podobne dla .NET Base klasy biblioteki (BCL) w przypadku implementacji biblioteki .NET nie istnieje. 

Standardowa .NET umożliwia realizację następujących podstawowych scenariuszy: 

- Definiuje zestaw uniform BCL interfejsy API dla wszystkich implementacji .NET w celu wdrożenia, niezależnie od obciążenia.
- Umożliwia deweloperom tworzenia przenośnych bibliotek, które są można używać we wdrożeniach .NET, przy użyciu tego samego zestawu interfejsów API.
- Zmniejsza lub nawet eliminuje kompilacja warunkowa udostępnionego źródła z powodu interfejsów API architektury .NET, tylko dla interfejsów API systemu operacyjnego.

Różne implementacje .NET docelowych określonych wersji platformy .NET Standard. Każda implementacja .NET w wersji anonsuje najwyższej .NET Standard wersji obsługiwanych, instrukcja, która oznacza, że obsługuje również poprzednie wersje. Na przykład .NET Framework 4.6 implementuje standardowe 1.3 .NET, co oznacza ujawnia on zdefiniowany w wersji .NET Standard 1.0 za pośrednictwem 1.3 wszystkich interfejsów API. Podobnie .NET Framework 4.6.1 implementuje standardowe 1.4 .NET, podczas .NET Core 1.0 implementuje standardowe 1.6 .NET.

## <a name="net-implementation-support"></a>Obsługa wdrażania .NET

W poniższej tabeli wymieniono wszystkich wersji platformy .NET Standard i obsługiwane platformy:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Do odnalezienia najnowszej wersji programu .NET Standard który może współpracować, wykonaj następujące czynności:
1. Znajdź wiersz, który wskazuje implementacji .NET, który chcesz uruchomić na.
2. Znajdź kolumny w tym wiersza, który wskazuje wersji od prawej do lewej.
3. Nagłówek kolumny wskazuje wersję .NET Standard obsługującego urządzenie docelowe (i wszystkich wersji platformy .NET Standard niższe będzie obsługiwać ją również).
4. Powtórz ten proces dla wszystkich platform, które ma być docelowa. Jeśli masz więcej niż jednej platformie docelowej, należy wybrać wersję mniejszą między nimi. Na przykład jeśli chcesz uruchomić program .NET Framework 4.5 i .NET Core 1.0, najnowsza wersja platformy .NET Standard, których można używać jest .NET Standard 1.1.

### <a name="which-net-standard-version-to-target"></a>Która wersja platformy .NET Standard do obiektu docelowego

W przypadku wybrania wersji platformy .NET Standard, należy rozważyć takie rozwiązanie:

- Dostępne są nowszej wersji, więcej interfejsów API.
- Im niższa wersji platformy więcej go zaimplementować.

Ogólnie rzecz biorąc, zalecamy pod kątem *najniższy* wersji możliwe .NET Standard. Dlatego po znalezieniu najwyższa wersja .NET Standard, którą można wskazać, wykonaj następujące kroki:
1. Docelowa dalej starszej wersji .NET Standard i skompilowanie projektu.
2. Jeśli projekt tworzy się pomyślnie, powtórz krok 1. W przeciwnym razie Przekieruj do nowszej wersji dalej i wersji, które powinny być używane.

### <a name="net-standard-versioning-rules"></a>.NET standard reguły kontroli wersji

Istnieją dwie reguły kontroli wersji głównej:

- Dodatek: Standardowy wersje programu .NET są logicznie koncentrycznych: nowszych wersjach uwzględnienie wszystkich interfejsów API z poprzednich wersji. Między wersjami nie wprowadzono żadnych zmian podziału.
- Niezmienne. Po dostarczonym, wersje .NET Standard są zablokowane. Nowe interfejsy API najpierw staną się dostępne w określonej implementacji .NET, takich jak .NET Core. .NET Standard Radę zdaniem nowych interfejsów API powinna zostać udostępniona wszędzie, zostanie ona dodana w nowej wersji platformy .NET Standard.

## <a name="comparison-to-portable-class-libraries"></a>Porównanie z bibliotek klas przenośnych

.NET standard nie zastępuje [przenośne klasy bibliotek PCL ()](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard ulepsza środowisko tworzenia przenośnych bibliotek mogą BCL standardowe i w związku z tym ustanowienie większej jednolitości implementacje .NET. Biblioteka przeznaczonego dla platformy .NET Standard jest PCL lub ".NET oparta na standardach PCL". Istniejące PCLs są "PCLs oparte na profilu".

Profile platformy .NET standard i PCL zostały utworzone do podobnych celów, ale też różnią się w sposób klucza.

Podobieństwa:

- Definiuje interfejsów API, który może służyć do udostępniania kodu binarnego.

Różnice:

- .NET standard jest nadzorowanego zestawu interfejsów API, podczas gdy PCL profile są definiowane przez przecięcia z istniejącymi platformami.
- .NET standard liniowo wersji, podczas gdy profile PCL nie.
- Profile PCL reprezentuje platformy Microsoft .NET Standard jest niezależny od platformy.

## <a name="specification"></a>Specyfikacja

Specyfikacja .NET Standard jest zestaw standardowych interfejsów API. Specyfikacja jest obsługiwana przez implementors .NET, w szczególności firma Microsoft (w tym .NET Framework, .NET Core i Mono) i Unity. Proces publicznego opinii jest używany w ramach ustanowienia nowe wersje .NET Standard za pośrednictwem [GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficjalna artefaktów

Specyfikacja oficjalnego to zestaw plików .cs, które definiują interfejsów API, które są częścią standardowej. [Katalogu ref](https://github.com/dotnet/standard/tree/master/netstandard/ref) w [repozytorium dotnet/standard](https://github.com/dotnet/standard) definiuje standardowych interfejsów API platformy .NET.

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) metapackage ([źródła](https://github.com/dotnet/standard/blob/master/netstandard/pkg/NETStandard.Library.dependencies.props)) opisano zestaw bibliotek, które definiują (częściowo) co najmniej jeden wersje .NET Standard.

Danego składnika, takiego jak zestaw System.Runtime, opisano:

- Część .NET Standard (tylko jej zakresu).
- Wiele wersji .NET Standard, dla tego zakresu.

Pochodnych artefakty są dostarczane, można włączyć odczytu bardziej wygodne i włączenia określonych scenariuszy developer (na przykład przy użyciu kompilatora).

- [Lista interfejsu API w języku znaczników markdown](https://github.com/dotnet/standard/tree/master/docs/versions)
- Odwołuje się do zestawów dystrybuowanych jako [pakietów NuGet](../core/packages.md) i odwołuje się [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) metapackage.

### <a name="package-representation"></a>Reprezentacja pakietu

Mechanizm dystrybucji głównej dla platformy .NET Standard zestawów odwołań jest [pakietów NuGet](../core/packages.md). Implementacje są dostarczane na różne sposoby właściwe dla poszczególnych implementacji .NET.

Pakiety NuGet target co najmniej jeden [struktury](frameworks.md). Pakiety .NET Standard target framework ".NET Standard". Celem może być za pomocą .NET Framework standardowe `netstandard` [compact TFM](frameworks.md) (na przykład `netstandard1.4`). Bibliotek, które są przeznaczone do uruchamiania na wiele środowisk uruchomieniowych powinna wskazywać platforma. 

`NETStandard.Library` Metapackage odwołuje się do pełnego zestawu pakietów NuGet, które definiują .NET Standard.  Typowym sposobem docelowej `netstandard` jest za pomocą odwołań do tego metapackage. Zawiera opis, a zapewnia dostęp do bibliotek .NET ~ 40 i skojarzone interfejsy API, który definiuje .NET Standard. Dodatkowe pakiety można odwołać obiektu docelowego `netstandard` uzyskać dostęp do dodatkowych interfejsów API. 

### <a name="versioning"></a>Przechowywanie wersji

Specyfikacja nie jest liczbie pojedynczej, ale w przyrostowo powiększania i liniowo wersjonowany zestaw interfejsów API. Pierwszą wersję standard ustanawia linii bazowej zestaw interfejsów API. Kolejne wersje Dodaj interfejsów API i dziedziczą interfejsów API zdefiniowany przez poprzednie wersje. Nie ma żadnego ustalonych przepisu usuwania interfejsów API zgodne ze standardem.

.NET standard nie jest specyficzne dla jednego implementacji .NET nie jest zgodny schemat przechowywania wersji któregokolwiek z tych środowisk uruchomieniowych.

Dodano interfejsy API do żadnej implementacji (na przykład, .NET Framework .NET Core i Mono) mogą być traktowane jako kandydatów do dodania do specyfikacji, zwłaszcza w przypadku, gdy ich są uznawane za podstawowych charakter. Nowy [wersje programu .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) są tworzone w oparciu wersjach implementacji .NET, umożliwiając pod kątem nowych interfejsów API z PCL standardowe .NET. Sposobu przechowywania wersji są opisane bardziej szczegółowo w [.NET Core Versioning](../core/versions/index.md).

Przechowywanie wersji platformy .NET standard jest ważne w przypadku użycia. Podana wersja platformy .NET Standard, można użyć bibliotek, które odnoszą się do tej samej lub niższej wersji. Następujące podejście opisano przepływ pracy dotyczący użycia .NET PCLs standardowe, specyficzne dla przeznaczonych dla platformy .NET Standard.

- Wybierz wersję .NET Standard na potrzeby Twojego PCL.
- W tej samej wersji platformy .NET Standard lub niższy, należy użyć bibliotek, które są zależne.
- Jeśli okaże się biblioteki, która jest zależna od wyższą wersję .NET Standard, albo należy przyjąć tej samej wersji lub zrezygnować z tej biblioteki.

### <a name="pcl-compatibility"></a>Zgodność PCL

.NET standard jest zgodny z podzbiorem PCL profilów. .NET standard 1.0, 1.1 i 1.2 każdego nakładają się na zbiór profilów PCL. To nakładanie został utworzony z dwóch przyczyn:

- Włącz .NET Standard na podstawie PCLs odwołać PCLs oparte na profilu.
- Włącz oparte na profilu PCLs spakowanych jako PCLs oparte na .NET Standard.

Profil na podstawie zgodności PCL są dostarczane przez [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) pakietu NuGet. Ta zależność jest wymagana podczas odwoływania się do pakietów NuGet, które zawierają PCLs oparte na profilu.

Oparte na profilu PCLs dostarczana w `netstandard` łatwiej wykorzystać niż zwykle spakowanych PCLs oparte na profilu. `netstandard` opakowanie jest zgodny z istniejących użytkowników.

Można wyświetlić zbioru profilów PCL, które są zgodne z .NET Standard: 

| Profil PCL | .NET standard | PCL platformy
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | Program .NET framework 4.5, Windows Phone Silverlight 8
| Profile78   | 1.0           | Program .NET framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | Program .NET framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | Program .NET framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8


## <a name="targeting-net-standard"></a>Przeznaczonych dla platformy .NET Standard

Możesz [kompilacji standardowych bibliotek .NET](../core/tutorials/libraries.md) przy użyciu kombinacji `netstandard` framework i NETStandard.Library metapackage. Widać przykłady [przeznaczonych dla platformy .NET Standard przy użyciu narzędzi platformy .NET Core](../core/packages.md).

## <a name="see-also"></a>Zobacz także
[Wersje standard programu .NET](https://github.com/dotnet/standard/blob/master/docs/versions.md)
