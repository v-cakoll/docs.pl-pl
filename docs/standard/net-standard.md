---
title: .NET Standard
description: Dowiedz się więcej na temat .NET Standard, jej wersji i implementacji platformy .NET, które go obsługują.
author: mairaw
ms.author: mairaw
ms.date: 09/23/2019
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 4fa0153cfa9dd52f4d80301d228dde3f16225bfd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582036"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) to formalna Specyfikacja interfejsów API platformy .NET, które mają być dostępne we wszystkich implementacjach platformy .NET. Uzasadnienie związane z .NET Standardem jest ustanowienie większej jednorodności w ekosystemie platformy .NET. [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) nadal ustala jednolitość dla zachowania implementacji platformy .NET, ale nie ma podobnej specyfikacji dla bibliotek klas bazowych .NET (BCL) dla implementacji biblioteki .NET.

.NET Standard włącza następujące kluczowe scenariusze:

- Definiuje jednolity zestaw interfejsów API BCL dla wszystkich implementacji platformy .NET do implementacji, niezależnie od obciążenia.
- Umożliwia deweloperom tworzenie przenośnych bibliotek, których można użyć w implementacjach platformy .NET, przy użyciu tego samego zestawu interfejsów API.
- Zmniejsza lub nawet eliminuje warunkową kompilację źródła udostępnionego ze względu na interfejsy API platformy .NET, tylko w przypadku interfejsów API systemu operacyjnego.

Różne implementacje platformy .NET przeznaczone dla konkretnych wersji .NET Standard. Każda wersja implementacji platformy .NET anonsuje najwyższą obsługiwaną przez nią wersję .NET Standard, instrukcję, która oznacza, że obsługuje także poprzednie wersje. Na przykład .NET Framework 4,6 implementuje .NET Standard 1,3, co oznacza, że uwidacznia wszystkie interfejsy API zdefiniowane w .NET Standard wersje 1,0 za pośrednictwem 1,3. Podobnie .NET Framework 4.6.1 implementuje .NET Standard 1,4, podczas gdy .NET Core 1,0 implementuje .NET Standard 1,6.

## <a name="net-implementation-support"></a>Obsługa implementacji platformy .NET

W poniższej tabeli wymieniono **minimalne** wersje platformy obsługujące każdą wersję .NET Standard. Oznacza to, że nowsze wersje wymienionej platformy obsługują również odpowiednią wersję .NET Standard. Na przykład platforma .NET Core 2,2 obsługuje .NET Standard 2,0 i starsze.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Aby znaleźć najwyższą wersję .NET Standard, która może być docelowa, wykonaj następujące czynności:

1. Znajdź wiersz wskazujący implementację platformy .NET, która ma zostać uruchomiona.
2. Znajdź w tym wierszu kolumnę, która wskazuje wersję rozpoczynającą od prawej do lewej.
3. Nagłówek kolumny wskazuje wersję .NET Standard obsługiwaną przez element docelowy. Możesz również określić dowolną niższą wersję .NET Standard. Nowsze wersje .NET Standard obsługują również Twoją implementację.
4. Powtórz ten proces dla każdej platformy, która ma być docelowa. Jeśli masz więcej niż jedną platformę docelową, należy wybrać mniejszą wersję między nimi. Na przykład jeśli chcesz uruchomić na .NET Framework 4,5 i .NET Core 1,0, najwyższa .NET Standard wersja, której można użyć, to .NET Standard 1,1.

### <a name="which-net-standard-version-to-target"></a>Która wersja .NET Standard ma być docelowa

W przypadku wybrania wersji .NET Standard należy wziąć pod uwagę tę wymianę:

- Im wyższa wersja, tym więcej interfejsów API są dostępne dla Ciebie.
- Im niższa wersja, tym więcej platform implementuje ją.

Ogólnie rzecz biorąc, zalecamy przeprowadzenie *najmniejszej* możliwej wersji .NET Standard. Po znalezieniu największej wersji .NET Standard można dowiedzieć się, wykonaj następujące kroki:

1. Wybierz następną niższą wersję .NET Standard i skompiluj projekt.
2. Jeśli projekt zostanie pomyślnie skompilowany, Powtórz krok 1. W przeciwnym razie Przekieruj do następnej wyższej wersji i jest to wersja, której chcesz użyć.

Jednak w przypadku mniejszych wersji .NET Standard wprowadzono kilka zależności pomocy technicznej. Jeśli projekt jest obiektem docelowym .NET Standard 1. x, zalecamy *również* przeprowadzenie .NET Standard 2,0. Upraszcza to wykres zależności dla użytkowników biblioteki, które działają na .NET Standard 2,0 zgodnych platform i zmniejsza liczbę pakietów potrzebnych do pobrania.

### <a name="net-standard-versioning-rules"></a>Reguły obsługi wersji .NET Standard

Istnieją dwie podstawowe reguły obsługi wersji:

- Dodatek: wersje .NET Standard są logicznie skoncentrowane koła: wyższe wersje obejmują wszystkie interfejsy API z poprzednich wersji. Nie ma żadnych istotnych zmian między wersjami.
- Niezmienne: po wysłaniu wersje .NET Standard są zamrożone. Nowe interfejsy API najpierw stają się dostępne w określonych implementacjach platformy .NET, takich jak .NET Core. Jeśli na tablicy przeglądu .NET Standard warto udostępnić nowe interfejsy API dla wszystkich implementacji platformy .NET, są one dodawane w nowej wersji .NET Standard.

## <a name="specification"></a>Specyfikacja

Specyfikacja .NET Standard to standardowy zestaw interfejsów API. Specyfikacja jest obsługiwana przez implementacje platformy .NET, w tym dla firmy Microsoft (w tym .NET Framework, .NET Core i mono) i Unity. Publiczny proces przesyłania opinii jest używany w ramach ustanawiania nowych wersji .NET Standard za pomocą usługi [GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficjalne artefakty

Oficjalną specyfikacją jest zestaw plików CS, które definiują interfejsy API, które są częścią standardu. [Katalog ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) w [repozytorium dotnet/Standard](https://github.com/dotnet/standard) definiuje .NET Standard interfejsów API.

Pakiet webpackage [. Library](https://www.nuget.org/packages/NETStandard.Library) ([Źródło](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) opisuje zestaw bibliotek, które definiują (w części) co najmniej jedną wersję .NET Standard.

Dany składnik, taki jak `System.Runtime`, zawiera opis:

- Część .NET Standard (tylko jej zakres).
- Wiele wersji .NET Standard dla tego zakresu.

Są udostępniane artefakty pochodne umożliwiające wygodniejsze odczytywanie i włączanie niektórych scenariuszy deweloperskich (na przykład przy użyciu kompilatora).

- [Lista interfejsów API w promocji](https://github.com/dotnet/standard/tree/master/docs/versions)
- Zestawy odwołań dystrybuowane jako [pakiety NuGet](../core/packages.md) , do których odwołuje się pakiet [.](https://www.nuget.org/packages/NETStandard.Library/)

### <a name="package-representation"></a>Reprezentacja pakietu

Podstawowym nośnikiem dystrybucji dla zestawów odwołań .NET Standard są [pakiety NuGet](../core/packages.md). Implementacje są dostarczane na różne sposoby, odpowiednie dla każdej implementacji platformy .NET.

Pakiety NuGet mają co najmniej jedną [platformę](frameworks.md). Pakiety .NET Standard są przeznaczone dla struktury ".NET Standard". Możesz określić platformę .NET Standard przy użyciu `netstandard` [kompaktowy TFM](frameworks.md) (na przykład `netstandard1.4`). Biblioteki przeznaczone do uruchamiania w wielu środowiskach uruchomieniowych powinny wskazywać tę strukturę. Dla najszerszego zestawu interfejsów API docelowy `netstandard2.0` od liczby dostępnych interfejsów API więcej niż dwa razy między .NET Standard 1,6 i 2,0.

Pakiet [`NETStandard.Library`binding](https://www.nuget.org/packages/NETStandard.Library/) odwołuje się do kompletnego zestawu pakietów NuGet, które definiują .NET Standard.  Najbardziej typowym sposobem na `netstandard` jest odwołujące się do tego pakietu. Opisuje i zapewnia dostęp do bibliotek platformy .NET ~ 40 i skojarzonych z nimi interfejsów API, które definiują .NET Standard. Aby uzyskać dostęp do dodatkowych interfejsów API, można odwoływać się do dodatkowych pakietów, których celem jest `netstandard`.

### <a name="versioning"></a>Przechowywanie wersji

Specyfikacja nie jest pojedyncza, ale przyrostowo rośnie i liniowo zestaw interfejsów API. Pierwsza wersja standardu ustanawia zestaw bazowy interfejsów API. Kolejne wersje dodają interfejsy API i dziedziczą interfejsy API zdefiniowane przez poprzednie wersje. Nie ma ustanowionego udostępniania do usuwania interfejsów API ze standardu.

.NET Standard nie jest specyficzna dla żadnej z implementacji platformy .NET ani nie jest zgodna ze schematem przechowywania wersji żadnego z tych środowisk.

Interfejsy API dodane do dowolnych implementacji (takich jak .NET Framework, .NET Core i mono) mogą być uznawane za kandydatów do dodania do specyfikacji, szczególnie jeśli są uważane za podstawę. Nowe [wersje .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) są tworzone na podstawie wydań implementacji platformy .NET, co umożliwia kierowanie nowych interfejsów API przy użyciu .NET Standard PCL. Informacje o wersji Mechanics są opisane bardziej szczegółowo w temacie [Versioning .NET Core](../core/versions/index.md).

Obsługa wersji .NET Standard jest ważna w przypadku użycia. Mając .NET Standard wersję, można użyć bibliotek przeznaczonych dla tej samej lub niższej wersji. Poniższe podejście opisuje przepływ pracy służący do używania .NET Standard PCLs, charakterystyczny dla .NET Standard określania wartości docelowej.

- Wybierz wersję .NET Standard, która ma być używana na potrzeby PCL.
- Użyj bibliotek, które są zależne od tej samej wersji .NET Standard lub niższej.
- Jeśli znajdziesz bibliotekę, która zależy od nowszej wersji .NET Standard, musisz przyjąć tę samą wersję lub zrezygnować z używania tej biblioteki.

## <a name="targeting-net-standard"></a>.NET Standard określania wartości docelowej

Można [tworzyć .NET Standard bibliotek](../core/tutorials/libraries.md) przy użyciu kombinacji środowiska `netstandard` i programu w wersji Standard. Library. Przykłady [ukierunkowane na .NET standard za pomocą narzędzi .NET Core Tools](../core/packages.md)można znaleźć w temacie.

## <a name="net-framework-compatibility-mode"></a>.NET Framework tryb zgodności

Począwszy od .NET Standard 2,0, wprowadzono .NET Framework tryb zgodności. Ten tryb zgodności umożliwia projektom .NET Standard odwoływanie się do bibliotek .NET Framework, tak jakby były kompilowane dla .NET Standard. Odwoływanie się do bibliotek .NET Framework nie działa dla wszystkich projektów, takich jak biblioteki używające interfejsów API Windows Presentation Foundation (WPF).

Aby uzyskać więcej informacji, zobacz [.NET Framework tryb zgodności](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Biblioteki .NET Standard i Visual Studio

Aby móc tworzyć biblioteki .NET Standard w programie Visual Studio, upewnij się, że masz zainstalowany [program Visual studio 2017 w wersji 15,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) lub nowszej w systemie Windows lub [Visual Studio dla komputerów Mac w wersji 7,1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) lub nowszej macOS.

Jeśli potrzebujesz korzystać tylko z bibliotek .NET Standard 2,0 w projektach, możesz to zrobić również w programie Visual Studio 2015. Konieczne jest jednak zainstalowanie klienta NuGet 3,6 lub nowszego. Klienta NuGet dla programu Visual Studio 2015 można pobrać ze strony [plików do pobrania](https://www.nuget.org/downloads) w programie NuGet.

## <a name="comparison-to-portable-class-libraries"></a>Porównanie z bibliotekami klas przenośnych

.NET Standard jest zamiennikiem [bibliotek klas przenośnych (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard usprawnia proces tworzenia bibliotek przenośnych przez opiekę standardowego BCL i ustanowienie większej jednorodności w ramach implementacji platformy .NET. Biblioteka, która jest przeznaczona dla .NET Standard to PCL lub "PCL oparty na .NET Standard". Istniejący PCLs są "PCLs oparte na profilach".

Profile .NET Standard i PCL zostały utworzone do podobnych celów, ale różnią się również kluczowymi sposobami.

Podobieństwa

- Zdefiniuj interfejsy API, które mogą być używane do udostępniania kodu binarnego.

Wynikających

- .NET Standard jest nadzorowanym zestawem interfejsów API, natomiast profile PCL są definiowane przez przedziały istniejących platform.
- .NET Standard wersje liniowe, natomiast profile PCL nie są obsługiwane.
- Profile PCL reprezentują platformy firmy Microsoft, gdy .NET Standard jest platformą niezależny od.

### <a name="pcl-compatibility"></a>Zgodność z PCL

.NET Standard jest zgodny z podzbiorem profilów PCL. .NET Standard 1,0, 1,1 i 1,2 każde nakładanie się z zestawem profilów PCL. Ten nakładanie zostało utworzone z dwóch powodów:

- Włącz PCLs oparte na .NET Standard, aby odwołać się do PCLs opartego na profilach.
- Włącz PCLs w oparciu o profilowanie jako PCLs oparty na .NET Standard.

Zgodność PCL oparta na profilach jest zapewniana przez pakiet NuGet [Microsoft. Core. Portable. Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) . Ta zależność jest wymagana w przypadku odwoływania się do pakietów NuGet, które zawierają PCLs oparte na profilach.

PCLs oparte na profilach spakowane jako `netstandard` są łatwiejsze do użycia niż zwykle spakowane PCLs oparte na profilach. `netstandard` pakowanie jest zgodne z istniejącymi użytkownikami.

Można wyświetlić zestaw profilów PCL, które są zgodne z .NET Standard:

| Profil PCL | .NET Standard | Platformy PCL
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4,5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8,1
| Profile32   | 1,2           | Windows 8.1, Windows Phone 8,1
| Profile44   | 1,2           | .NET Framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET Framework 4,5, Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET Framework 4,5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8,1, Windows Phone Silverlight 8,1
| Profile111  | 1.1           | .NET Framework 4,5, Windows 8, Windows Phone 8,1
| Profile151  | 1,2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8,1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8,1, Windows Phone Silverlight 8,1
| Profile259  | 1.0           | .NET Framework 4,5, Windows 8, Windows Phone 8,1, Windows Phone Silverlight 8

## <a name="see-also"></a>Zobacz także

- [Wersje .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [Kompilowanie biblioteki .NET Standard](../core/tutorials/library-with-visual-studio.md)
- [Obsługiwane rozwiązania międzyplatformowe](./library-guidance/cross-platform-targeting.md)
