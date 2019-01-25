---
title: Słownik platformy .NET
description: Dowiedz się, znaczenie wybranych terminów używanych w dokumentacji platformy .NET.
author: tdykstra
ms.author: tdykstra
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: b9654bf7f6cbc1019d00db986ba883cbab0abbb5
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857982"
---
# <a name="net-glossary"></a>Słownik platformy .NET

Podstawowym celem tego słownika jest wyjaśnić znaczenie wybranych terminów i skrótów, które pojawiają się często w dokumentacji platformy .NET, bez definicji.

## <a name="aot"></a>AOT

Kompilator Ahead of time.

Podobnie jak [JIT](#jit), to kompilator tłumaczy także [IL](#il) do kodu maszynowego. W przeciwieństwie do kompilacji JIT kompilacja AOT odbywa się przed aplikacji jest wykonywany i zwykle odbywa się na innym komputerze. Ponieważ łańcuchy narzędzi kompilacji AOT nie kompilacji w czasie wykonywania, nie muszą oni zminimalizować czas kompilacji. Oznacza to, że mogą poświęcać więcej optymalizacji czasu. Ponieważ kontekst AOT całej aplikacji, kompilator AOT wykonuje również połączeń między modułami i analizy całego programu, co oznacza, że wszystkie odwołania zostaną wykonane prawidłowo, a pojedynczy plik wykonywalny jest generowany.

Zobacz [CoreRT](#corert) i [architektura .NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET 

Oryginalna implementacja ASP.NET, który jest dostarczany z .NET Framework.

Czasami program ASP.NET to ogólny termin, który odwołuje się do obu implementacjach ASP.NET, łącznie z platformą ASP.NET Core. Co oznacza, że określenie niesie ze sobą w danym przypadku zależy od kontekstu. Odnoszą się do platformy ASP.NET 4.x, jeśli chcesz było jasne, że nie korzystania z platformy ASP.NET jako oznaczenie obu implementacjach. 

Zobacz [dokumentacja platformy ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Dla wielu platform, wdrożenia o wysokiej wydajności, typu open source platformy ASP.NET oparta na module .NET Core.

Zobacz [dokumentacji platformy ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>zestaw

A *.dll*/*.exe* pliku, który może zawierać zbiór interfejsów API, które mogą być wywoływane przez aplikacje lub innych zestawów.

Zespół może obejmować typów, takich jak interfejsy, klasy, struktury, wyliczenia i delegaty. Zestawy w projekcie *bin* folderu są czasami określane jako *pliki binarne*. Zobacz też [biblioteki](#library).

## <a name="clr"></a>CLR

Środowisko uruchomieniowe języka wspólnego.

Dokładne znaczenie zależy od kontekstu, ale zazwyczaj odnosi się do środowiska uruchomieniowego programu .NET Framework. Środowisko CLR obsługuje alokacji pamięci i zarządzania. Środowisko CLR jest również maszynę wirtualną, który nie tylko wykonuje aplikacji, ale także generuje i kompiluje kodu na bieżąco za pomocą [JIT](#jit) kompilatora. Bieżąca implementacja firmy Microsoft CLR jest Windows tylko.

## <a name="coreclr"></a>CoreCLR

.NET core środowiska uruchomieniowego języka wspólnego.

Ta CLR składa się z tego samego kodu podstawowego jako środowiska CLR. Początkowo CoreCLR został środowiska uruchomieniowego Silverlight i był przeznaczony do działania na wielu platformach, specjalnie Windows i OS X. CoreCLR jest teraz częścią programu .NET Core i przedstawia uproszczoną wersję środowiska CLR. Nadal jest [dla wielu platform](#cross-platform) środowiska uruchomieniowego, teraz łącznie z obsługą wielu dystrybucji systemu Linux. CoreCLR jest również maszynę wirtualną oraz możliwości JIT i kod realizacji.

## <a name="corefx"></a>CoreFX

Biblioteki klas podstawowych platformy .NET (BCL)

Przestrzenie nazw zestawu, biblioteki, które tworzą Microsoft.* i System.* (a w ograniczonym zakresie Microsoft.*). BCL jest ogólnego przeznaczenia, framework niższego poziomu, które wyższego poziomu struktur aplikacji, takich jak ASP.NET Core. Kod źródłowy .NET Core BCL jest zawarty w [repozytorium CoreFX](https://github.com/dotnet/corefx). Jednak większość interfejsów API programu .NET Core są również dostępne w .NET Framework, dzięki czemu można traktować CoreFX jako rozwidlenie .NET Framework BCL.

## <a name="corert"></a>CoreRT

Środowisko uruchomieniowe platformy .NET core.

W przeciwieństwie do CLR/CoreCLR, CoreRT nie jest maszyna wirtualna, co oznacza, nie zawiera urządzeń do generowania i uruchamianie kodu na bieżąco, ponieważ nie zawiera [JIT](#jit). Jednakże obejmują [GC](#gc) z możliwością Identyfikacja typu czasu wykonywania (RTTI) i odbicie. Jednak jego typu system został zaprojektowany tak, aby metadanych dla odbicie nie jest wymagane. Dzięki temu masz [AOT](#aot) narzędzia łańcucha, który umożliwia łączenie away zbędny metadanych (co ważniejsze) Zidentyfikuj kod, który nie korzysta z aplikacji. CoreRT jest w trakcie opracowywania.

Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="cross-platform"></a>na wiele platform

Możliwość tworzenia i wykonywanie aplikacji, która może być używany w wielu różnych systemach operacyjnych, takich jak Linux, Windows i iOS, bez konieczności ponownego pisania specjalnie dla każdej z nich. Umożliwia to ponowne użycie kodu i spójności między aplikacjami na różnych platformach.

## <a name="ecosystem"></a>ecosystem

Wszystkie środowiska uruchomieniowego oprogramowania, narzędzi deweloperskich i zasoby społecznościowe, które są używane do tworzenia i uruchamiania aplikacji dla danej technologii.

Termin "Ekosystemu .NET" różni się od podobnych warunkach, takie jak "Stos technologii .NET" w jej włączenia aplikacji innych firm i bibliotek. Oto przykład w zdaniu:

- "Motywacja za [.NET Standard](#net-standard) jest zapewnienie większej jednolitości należący do ekosystemu platformy .NET." 

## <a name="framework"></a>szablon

Ogólnie rzecz biorąc kompleksowy zbiór interfejsów API, które ułatwia tworzenia i wdrażania aplikacji, które są oparte na określonej technologii. W tym sensie ogólne ASP.NET Core i Windows Forms to przykłady struktur aplikacji. Zobacz też [biblioteki](#library).

Słowo "framework" ma bardziej szczegółowe techniczne znaczenie w następujących warunkach:
* [.NET Framework](#net-framework)
* [Platforma docelowa](#target-framework)
* [TFM (moniker platformy docelowej)](#tfm)

W istniejącą dokumentacją "framework" czasami odnosi się do [implementacji .NET](#implementation-of-net). Na przykład artykułu mogą korzystać z platformy .NET Core framework. Planujemy wyeliminować to użycie pomylenia z dokumentacji.

## <a name="gc"></a>GC

Moduł wyrzucania elementów bezużytecznych.

Moduł odśmiecania pamięci jest implementacją automatyczne zarządzanie pamięcią.  Wykaz Globalny zwalnia pamięć zajęta przez obiekty, które nie są już w użyciu. 

Zobacz [wyrzucania elementów bezużytecznych](garbage-collection/index.md).

## <a name="il"></a>IL

Język pośredni.

Skompiluj wyższego poziomu języków .NET, takich jak C#, dół, aby zestaw instrukcji niezależność od sprzętu, który nosi nazwę języka pośredniego (IL). IL jest czasami określane jako MSIL (Microsoft IL) lub listę CIL (Common IL).

## <a name="jit"></a>JIT

Kompilator just in time.

Podobnie jak [AOT](#aot), to kompilator tłumaczy [IL](#il) do kodu maszynowego, która określa procesor. W przeciwieństwie do kompilacji AOT kompilacja JIT ma miejsce na żądanie i odbywa się na tym samym komputerze, który kod musi zostać uruchomiony. Ponieważ kompilacja JIT odbywa się podczas wykonywania aplikacji, czas kompilacji jest częścią w czasie wykonywania. W związku z tym kompilatory JIT muszą równoważyć czas Optymalizacja kodować oszczędności, które mogą wytwarzać wynikowy kod. Ale JIT zna rzeczywistej sprzętu i można zwolnić deweloperów od konieczności wysyłania różne implementacje.

## <a name="implementation-of-net"></a>Implementacja programu .NET

Implementacja interfejsu .NET obejmuje następujące funkcje:

- Co najmniej jeden środowisk uruchomieniowych. Przykłady: CLR, CoreCLR, CoreRT.
- Biblioteka klas, który implementuje wersji programu .NET Standard i może zawierać dodatkowe interfejsy API. Przykłady: Podstawowej biblioteki klas .NET Framework, biblioteki klas podstawowych platformy .NET.
- Opcjonalnie co najmniej jeden struktury aplikacji. Przykłady: ASP.NET, Windows Forms i WPF znajdują się w programie .NET Framework.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Przykłady implementacji platformy .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Platforma uniwersalna systemu Windows (UWP)](#uwp)

## <a name="library"></a>biblioteka

Kolekcja interfejsów API, które mogą być wywoływane przez aplikacje lub inne biblioteki. Biblioteka .NET składa się z co najmniej jeden [zestawy](#assembly).

Biblioteka słów i [framework](#framework) są często używane synonimów.

## <a name="metapackage"></a>meta Microsoft.aspnetcore.all

Pakiet NuGet, którego Brak biblioteki oddzielnie, ale jest tylko listę zależności. Dołączonych pakietów opcjonalnie utworzyć interfejs API dla platformy docelowej.

Zobacz [pakiety, Metapakiety i struktury](../core/packages.md)

## <a name="mono"></a>Mono

Narzędzie mono jest typu open source, [dla wielu platform](#cross-platform) implementacji .NET, która jest głównie używane, gdy wymagana jest mały środowiska uruchomieniowego. To środowisko uruchomieniowe, które obsługuje aplikacje platformy Xamarin na systemów Android, Mac, iOS, tvOS i watchOS i koncentruje się głównie na aplikacje, które wymagają o niewielkich rozmiarach.

Obsługuje on wszystkie obecnie opublikowane wersje .NET Standard.

W przeszłości narzędzie Mono zaimplementowana większych interfejsu API programu .NET Framework i emulowane niektóre najpopularniejsze funkcje, w systemach Unix. To jest czasami używane do uruchamiania aplikacji .NET, które zależą od tych funkcji w systemach Unix.

Narzędzie mono jest zwykle używany z kompilator just-in-time, ale także kompilatora pełnej statyczne (kompilacja z wyprzedzeniem of-time), jaka jest używana na platformach, np. iOS.

Aby dowiedzieć się więcej na temat platformy Mono, zobacz [dokumentacja narzędzia Mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Ogólny termin dla [.NET Standard](#net-standard) i wszystkie [implementacji .NET](#implementation-of-net) i obciążeń. Zawsze wielką literą, nigdy nie ".Net".

Zobacz [.NET — przewodnik](index.md)

## <a name="net-core"></a>.NET Core 

Implementacja dla wielu platform, wysokiej wydajności, typu open source platformy .NET. Obejmuje podstawowe środowisko uruchomieniowe języka wspólnego (CoreCLR), środowisko uruchomieniowe AOT Core (w trakcie opracowywania CoreRT), Biblioteka klasy podstawowej Core i Core SDK.

Zobacz [platformy .NET Core](../core/index.md).

## <a name="net-core-cli"></a>.NET core interfejsu wiersza polecenia

Łańcuch dla wielu platform, narzędzi do tworzenia aplikacji platformy .NET Core.

Zobacz [narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core](../core/tools/index.md).

## <a name="net-core-sdk"></a>Zestaw SDK dla platformy .NET core

Zestaw bibliotek i narzędzi, które umożliwiają deweloperom tworzenie aplikacji .NET Core oraz bibliotek. Obejmuje [interfejsu wiersza polecenia platformy .NET Core](#net-core-cli) do tworzenia biblioteki .NET Core i środowiska uruchomieniowego do tworzenia i uruchamiania aplikacji i dotnet pliku wykonywalnego aplikacji (*dotnet.exe*) uruchomieniu polecenia interfejsu wiersza polecenia i umożliwia uruchamianie aplikacji.

Zobacz [Omówienie zestawu SDK programu .NET Core](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementacja platformy .NET, który jest uruchamiany tylko na Windows. Zawiera środowisko uruchomieniowe języka wspólnego (CLR), Biblioteka klasy podstawowej i bibliotek platformy aplikacji, takich jak ASP.NET, Windows Forms i WPF.

Zobacz [.NET Framework — przewodnik](../framework/index.md).

## <a name="net-native"></a>Architektura .NET Native

Łańcucha narzędzi kompilatora, która wywołuje kod macierzysty z wyprzedzeniem of-time (AOT), w przeciwieństwie do just-in-time (JIT).

Kompilacji odbywa się na komputerze dewelopera, podobnie jak działa kompilatora i konsolidatora C++. Nieużywany kod jest usuwany, a zużywa więcej czasu, zoptymalizowania go. On wyodrębnia kod z bibliotek i scala te listy w pliku wykonywalnego. Wynik jest pojedynczym module, który reprezentuje całej aplikacji.

Platformy uniwersalnej systemu Windows była pierwszym struktury aplikacji obsługiwane przez .NET Native. Firma Microsoft obsługuje teraz tworzenie aplikacji konsoli natywne aplikacje dla Windows, macOS i Linux.

Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Formalną specyfikację interfejsów API platformy .NET, które są dostępne w każdej implementacji .NET.

Specyfikacji .NET Standard, jest czasami nazywane biblioteki w dokumentacji. Ponieważ biblioteki zawiera implementacje interfejsu API, nie tylko specyfikacjami (interfejsy) jest mylący, aby wywołać .NET Standard, "library". Planujemy wyeliminować to użycie z dokumentacji, z wyjątkiem w odniesieniu do nazw programu .NET Standard meta Microsoft.aspnetcore.all (`NETStandard.Library`).

Zobacz [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Generowanie natywne (obraz).

Ta technologia można traktować jako trwałe kompilatora JIT. Zazwyczaj kompiluje kod na komputerze, gdy kod jest wykonywany, ale kompilacji zazwyczaj występuje w czasie instalacji.

## <a name="package"></a>Pakiet

Pakiet NuGet &mdash; lub po prostu pakietu &mdash; jest *zip* plików z jednego lub więcej zestawów o takiej samej nazwie, oraz dodatkowe metadane, takie jak imię i nazwisko autora.

*Zip* plik ma *.nupkg* rozszerzenia i mogą zawierać zasoby, takie jak *.dll* plików i *.xml* plików do użytku z wielu elementu docelowego platformy i wersje. Podczas instalowania aplikacji lub w bibliotece, odpowiednie zasoby są zaznaczone, oparte na platformie docelowej, określone przez aplikację lub bibliotekę. Zasoby, które definiują interfejs znajdują się w *ref* folder i zasoby, które definiują wdrożenia znajdują się w *lib* folderu.

## <a name="platform"></a>platforma

System operacyjny i sprzęt, na których ono działa, takich jak Windows, macOS, Linux, iOS i Android.

Poniżej przedstawiono przykłady użycia w zdaniach:

- ".NET core to implementacja dla wielu platform .NET". 
- "PCL profile reprezentują platform firmy Microsoft, gdy .NET Standard jest niezależny od platformy."

Dokumentacja platformy .NET jest często używane "Platformy .NET" oznacza implementacji .NET albo stosu .NET, w tym wszystkich implementacjach. Oba te sposoby użycia zwykle pobieranie mylić z podstawowe znaczenie (system operacyjny/sprzęt), więc planujemy wyeliminować te użycia z dokumentacji.

## <a name="runtime"></a>środowisko uruchomieniowe

Środowisko wykonawcze programu zarządzanych.

System operacyjny jest częścią środowiska wykonawczego, ale nie jest częścią środowiska uruchomieniowego .NET. Poniżej przedstawiono kilka przykładów środowiska uruchomieniowe platformy .NET:

- Środowisko uruchomieniowe języka wspólnego (CLR)
- Podstawowe środowisko uruchomieniowe języka wspólnego (CoreCLR)
- Architektura .NET native (dla platformy uniwersalnej systemu Windows)
- Środowisko uruchomieniowe mono

Dokumentacja platformy .NET czasami używa "środowiska uruchomieniowego" oznacza implementacji .NET. Na przykład w następujących zdania "środowiska uruchomieniowego" należy zastąpić je klasą "wdrożenia":

- "Różne środowiska uruchomieniowe platformy .NET zaimplementować określonych wersji programu .NET Standard".
- "Bibliotek, które są przeznaczone do uruchamiania na wielu modułów wykonawczych powinny target framework to". (odwołujące się do usługi .NET w warstwie standardowa)
- "Różne środowiska uruchomieniowe platformy .NET zaimplementować określonych wersji programu .NET Standard. … Każda wersja środowiska uruchomieniowego .NET anonsuje najwyższa wersja .NET Standard, który obsługuje..."

Planujemy wyeliminować ten niespójne użycie. 

## <a name="stack"></a>stack

Zestaw programowanie technologii, które są używane razem do kompilowania i uruchamiania aplikacji.

"Stos .NET" odnosi się do wszystkich implementacji .NET i .NET Standard. Fraza "stos .NET" może odwoływać się do jednej implementacji .NET. 

## <a name="target-framework"></a>Platforma docelowa

Kolekcja interfejsów API, które aplikacji platformy .NET lub biblioteki opiera się na.

Aplikacji lub biblioteki mogą określać docelową wersję .NET Standard (na przykład .NET Standard 2.0), który jest specyfikacja standardowy zestaw interfejsów API we wszystkich wdrożeniach platformy .NET. Aplikacji lub biblioteki można również przeznaczać wersję konkretnej implementacji .NET, w której jest zamierzone, zapisz go pobiera dostęp do interfejsów API specyficzne dla implementacji. Na przykład aplikację, który jest przeznaczony dla platformy Xamarin.iOS uzyskuje dostęp do otoki dostarczone do platformy Xamarin dla systemu iOS interfejsu API.

Dla niektórych platform docelowych (na przykład, .NET Framework) dostępne interfejsy API są definiowane przez zestawy implementacji .NET są instalowane w systemie, które mogą zawierać struktury aplikacji interfejsów API (na przykład ASP.NET, formularze winform). Dla platform docelowych na podstawie pakietów (np. .NET Standard i .NET Core) framework interfejsy API są definiowane przez pakiety zainstalowane w aplikacji lub biblioteki. W takim przypadku platforma docelowa określa niejawnie meta Microsoft.aspnetcore.all, który odwołuje się do wszystkich pakietów, które razem tworzą platformę.

Zobacz [ustalać platformy docelowe](frameworks.md).

## <a name="tfm"></a>TFM

Moniker platformy docelowej.

Standardowy format tokenu do określenia platformy docelowej aplikacji platformy .NET lub biblioteki. Platformy docelowe zazwyczaj odwołuje się krótką nazwę, taką jak `net462`. Długiej krótkich nazw platform (np. NETFramework, Version = 4.6.2) istnieje, ale nie są zwykle używane do określ platformę docelową.

Zobacz [ustalać platformy docelowe](frameworks.md).

## <a name="uwp"></a>Platforma UWP

Platforma Universal Windows.

Implementacja programu .NET, który służy do tworzenia nowoczesnych, obsługą dotyku aplikacje Windows, jak i oprogramowania dla Internetu rzeczy (IoT). Ustalono, aby zunifikować różnych typów urządzeń, które ma pod kątem, w tym komputerów, tabletów, phablets, telefony i nawet konsoli Xbox. Platformy uniwersalnej systemu Windows zapewnia wiele usług, takich jak w sklepie z aplikacjami scentralizowanego, środowisko wykonawcze (AppContainer) i zestaw interfejsów API Windows, zamiast Win32 (WinRT). Aplikacje mogą być napisane w języku C++, C#, VB.NET i JavaScript. Korzystając z języka C# i VB.NET, interfejsów API platformy .NET są dostarczane przez platformy .NET Core.

## <a name="see-also"></a>Zobacz także

- [.NET — przewodnik](index.md)
- [.NET framework — przewodnik](../framework/index.md)
- [.NET Core](../core/index.md)
- [Omówienie programu ASP.NET](/aspnet/index#pivot=aspnet)
- [Omówienie platformy ASP.NET Core](/aspnet/index#pivot=core)
