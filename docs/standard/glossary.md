---
title: .NET — słownik
description: Dowiedz się znaczenie wybranych terminów używanych w dokumentacji programu .NET.
keywords: .NET glossary, .NET dictionary, .NET terminology, .NET platform, .NET framework, .NET runtime
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7e9732fb6eaef240d08449635697ba6b8ad9c510
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="net-glossary"></a>.NET — słownik

Podstawowym celem tego słownika jest wyjaśnienie znaczenia wybranego terminów i skrótów, które często pojawiają się w dokumentacji programu .NET, bez definicji.

## <a name="aot"></a>DRZEWA OBIEKTÓW APLIKACJI

Kompilator z wyprzedzeniem o czasie.

Podobnie jak [JIT](#jit), tłumaczy także ten kompilator [IL](#il) do kodu maszyny. W przeciwieństwie do kompilacji JIT kompilacji drzewa obiektów aplikacji odbywa się przed aplikacji jest wykonywane i jest zazwyczaj wykonywane na innym komputerze. Ponieważ drzewa obiektów aplikacji narzędzia łańcuchów nie kompilacji w czasie wykonywania, nie będą musieli zminimalizować czas kompilacji. Oznacza to, że może poświęcić więcej czasu optymalizacji. Ponieważ kontekście drzewa obiektów aplikacji jest całej aplikacji, kompilator drzewa obiektów aplikacji wykonuje także łączenie między modułami i analizy całego programu, co oznacza, że wszystkie odwołania zostaną wykonane i pojedynczy plik wykonywalny jest generowany.

## <a name="aspnet"></a>ASP.NET 

Oryginalny implementacja ASP.NET jest dostarczany z programu .NET Framework.

Czasami ASP.NET jest ogólny termin odnoszący się do obu implementacje ASP.NET, w tym również platformy ASP.NET Core. Co oznacza, że termin niesie w danym przypadku zależy od kontekstu. Odwołuje się do platformy ASP.NET 4.x, aby wyjaśnić, że nie będziesz jej używać ASP.NET oznacza zarówno implementacji. 

Zobacz [dokumentacji ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Między platformami, implementacji wysokiej wydajności typu open source platformy ASP.NET w oparciu .NET Core.

Zobacz [dokumentacji platformy ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>zestaw

A *.dll*/*.exe* pliku, który może zawierać kolekcję interfejsów API, które może być wywoływany przez aplikacje lub innych zestawów.

Zestaw może zawierać typów, takie jak interfejsy, klasy, struktury, wyliczenia i delegaty. Zestawy w projekcie *bin* folderu są czasami określane jako *plików binarnych*. Zobacz też [biblioteki](#library).

## <a name="clr"></a>CLR

Środowisko uruchomieniowe języka wspólnego.

Dokładne znaczenie zależy od kontekstu, ale zazwyczaj odnosi się do środowiska wykonawczego platformy .NET. Środowisko CLR obsługuje alokacją pamięci i zarządzania. Środowisko CLR jest również maszyny wirtualnej, który nie tylko wykonuje aplikacji, ale także generuje i kompiluje kodu na bieżąco przy użyciu kompilatora JIT. Bieżąca implementacja Microsoft CLR to tylko systemu Windows.

## <a name="coreclr"></a>CoreCLR

.NET core środowisko uruchomieniowe języka wspólnego.

Ta CLR składa się z tego samego kodu podstawowej jako środowisko CLR. Pierwotnie, środowisko CoreCLR został środowiska uruchomieniowego programu Silverlight i był przeznaczony do działania na wielu platformach, w szczególności systemu Windows i OS X. w środowisko CoreCLR jest obecnie częścią .NET Core i reprezentuje uproszczonej wersji środowiska CLR. Jest ono nadal międzyplatformowego środowiska uruchomieniowego, teraz tym obsługę wielu dystrybucje systemu Linux. Środowisko CoreCLR jest również maszynę wirtualną z możliwości wykonywania JIT i kod.

## <a name="corefx"></a>CoreFX

Biblioteka klasy podstawowej platformy .NET core (BCL)

Przestrzenie nazw bibliotek, które obejmują System.* (oraz w ograniczonym zakresie Microsoft.*). BCL jest ogólnego przeznaczenia, rozbudowywać wyższego poziomu struktur aplikacji, takich jak ASP.NET Core framework niższego poziomu. Kod źródłowy .NET Core BCL znajduje się w [repozytorium CoreFX](https://github.com/dotnet/corefx). Jednak większość podstawowych interfejsów API .NET są również dostępne w programie .NET Framework, można traktować CoreFX jako rozwidlenia .NET Framework BCL.

## <a name="corert"></a>CoreRT

Środowisko uruchomieniowe .NET core.

W przeciwieństwie do środowiska CLR/na środowisko CoreCLR CoreRT nie jest maszyny wirtualnej, co oznacza, że nie ma wśród nich urządzeń do Generowanie i uruchamianie kodu na bieżąco, ponieważ nie ma wśród nich [JIT](#jit). Jednak zawierać [GC](#gc) z możliwością identyfikacji typu środowiska uruchomieniowego (RTTI) i odbicia. Jednak system jego typ zaprojektowano tak, aby metadanych w celu odbicia nie jest wymagane. Dzięki temu o [drzewa obiektów aplikacji](#aot) narzędzia łańcucha, który umożliwia łączenie zadań zbędny metadanych (ważniejsze) identyfikację kodu, który nie korzysta z aplikacji. CoreRT trwa opracowywanie.

Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="ecosystem"></a>ekosystemu

Wszystkie środowiska uruchomieniowego oprogramowania, narzędzia do programowania i zasoby społecznościowe, które są używane do tworzenia i uruchamiania aplikacji dla danej technologii.

Termin "Ekosystemu platformy .NET" różni się od podobnych warunkach, takich jak "Stosu .NET" w jej włączenia aplikacji innych firm i bibliotek. Oto przykład w zdaniu na wyraz:

- "Motywacją za [.NET Standard](#net-standard) jest ustanowienie większej jednolitości w ekosystemie .NET." 

## <a name="framework"></a>szablon

Ogólnie rzecz biorąc wszechstronny zbiór interfejsów API, które ułatwia opracowywania i wdrażania aplikacji, które są oparte na konkretnej technologii. W tym sensie ogólne platformy ASP.NET Core i formularze systemu Windows to przykłady struktury aplikacji. Zobacz też [biblioteki](#library).

Wyraz "framework" ma więcej określone znaczenie techniczne w następujących warunkach:
* [.NET Framework](#net-framework)
* [Platforma docelowa](#target-framework)
* [TFM (moniker platformy docelowej)](#tfm)

W dokumentacji istniejących "framework" czasami odwołuje się do [implementacji .NET](#implementation-of-net). Na przykład artykuł może wywołać .NET Core framework. Firma Microsoft planuje wyeliminować mylące użycia w dokumentacji.

## <a name="gc"></a>GC

Moduł zbierający elementy bezużyteczne.

Moduł zbierający elementy bezużyteczne jest implementacją automatyczne zarządzanie pamięcią.  Wykaz Globalny zwalnia pamięć zajmowany przez obiekty, które nie są już w użyciu. 

Zobacz [wyrzucanie elementów bezużytecznych](garbage-collection/index.md).

## <a name="il"></a>IL

Język pośredni.

Kompiluj wyższego poziomu języków .NET, takich jak C#, dół zestaw instrukcji niezależny od sprzętu, który jest nazywany języku pośrednim (IL). IL czasami nazywa się MSIL (Microsoft IL) lub CIL (język Common IL).

## <a name="jit"></a>JIT

Kompilatora just in time.

Podobnie jak [drzewa obiektów aplikacji](#aot), tłumaczy ten kompilator [IL](#il) do kodu maszyny, która obsługuje usługę procesora. W przeciwieństwie do drzewa obiektów aplikacji kompilacja JIT wykonywany jest na żądanie i odbywa się na tym samym komputerze, który kod musi być uruchamiane. Ponieważ kompilacja JIT odbywa się podczas wykonywania aplikacji, kompilowania wchodzi w skład w czasie wykonywania. W związku z tym kompilatory JIT trzeba saldo czas optymalizacji kodu oszczędności, które mogą wytwarzać wynikowy kod. Ale JIT zna rzeczywistego sprzętu i można zwolnić deweloperzy z konieczności wysłać różnych implementacji.

## <a name="implementation-of-net"></a>Implementacja programu .NET

Implementacja .NET obejmuje następujące funkcje:

- Jeden lub więcej środowisk uruchomieniowych. Przykłady: CLR, środowisko CoreCLR, CoreRT.
- Biblioteka klas, które implementuje w wersji programu .NET Standard i może zawierać dodatkowe interfejsy API. Przykłady: Klasa podstawowa Biblioteka programu .NET Framework, .NET Core klasy podstawowej biblioteki.
- Opcjonalnie co najmniej jeden struktury aplikacji. Przykłady: ASP.NET, formularzy systemu Windows i WPF znajdują się w programie .NET Framework.
- Opcjonalnie narzędzia do programowania. Niektóre narzędzia do programowania są współużytkowane przez wiele implementacji.

Przykłady implementacji .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Platforma uniwersalna systemu Windows (UWP)](#uwp)

## <a name="library"></a>biblioteka

Kolekcja interfejsów API, które może być wywoływany przez aplikacje lub inne biblioteki. Biblioteka .NET składa się z co najmniej jeden [zestawy](#assembly).

Biblioteka słów i [framework](#framework) są często używane jako synonim.

## <a name="metapackage"></a>metapackage

Pakiet NuGet, który ma żadnej biblioteki oddzielnie, ale jest tylko listę zależności. Dołączonych pakietów można opcjonalnie ustanowić interfejsu API dla struktury docelowej.

Zobacz [pakietów, Metapackages i platform](../core/packages.md)

## <a name="mono"></a>Mono

Mono jest implementację .NET, która jest głównie używane, gdy wymagana jest mała środowiska wykonawczego. To środowisko uruchomieniowe, które uprawnienia aplikacji platformy Xamarin Android, Mac, iOS, systemu tvOS i watchOS i koncentruje się przede wszystkim na aplikacje, które wymagają niewielkie rozmiary.

Obsługuje wszystkie obecnie opublikowanej wersji platformy .NET Standard.

W przeszłości Mono zaimplementowana większych interfejsu API programu .NET Framework i emulowane niektóre najpopularniejsze funkcje w systemie Unix. Czasami służy do uruchamiania aplikacji .NET, które zależą od tych funkcji w systemie Unix.

Mono jest zwykle używana z kompilatora just in time, ale także kompilatora pełnej statyczne (kompilacja z wyprzedzeniem o czasie) używaną na platformach, np. z systemem iOS.

Aby dowiedzieć się więcej na temat Mono, zobacz [Mono dokumentacji](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Termin określający [.NET Standard](#net-standard) i wszystkie [implementacje .NET](#implementation-of-net) i obciążeń. Zawsze pisany wielkimi literami, nie ".Net".

Zobacz [.NET — przewodnik](index.md)

## <a name="net-core"></a>.NET Core 

Implementacja między platformami, wysokiej wydajności typu open source platformy .NET. Zawiera podstawowe środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR), drzewa obiektów aplikacji podstawowego środowiska wykonawczego (rozwijany CoreRT), podstawowa Biblioteka klasy podstawowej i Core SDK.

Zobacz [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>Oprogramowanie .NET core interfejsu wiersza polecenia

Łańcuch między platformami, narzędzi do tworzenia aplikacji platformy .NET Core.

Zobacz [narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core](../core/tools/index.md).

## <a name="net-core-sdk"></a>Oprogramowanie .NET core SDK

Zestaw biblioteki i narzędzia, które umożliwiają deweloperom tworzenie aplikacji platformy .NET Core i bibliotek. Obejmuje [interfejsu wiersza polecenia platformy .NET Core](#net-core-cli) do tworzenia aplikacji, bibliotek .NET Core i środowiska uruchomieniowego do tworzenia i uruchamiania aplikacji i dotnet pliku wykonywalnego (*dotnet.exe*) uruchamia polecenia interfejsu wiersza polecenia i są uruchomione aplikacje.

Zobacz [Omówienie zestawu SDK .NET Core](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementacja programu .NET, na którym działa tylko w systemie Windows. Obejmuje środowiska uruchomieniowego języka wspólnego (CLR), Biblioteka klasy podstawowej i bibliotek platformy aplikacji, takich jak ASP.NET, formularze systemu Windows i WPF.

Zobacz [.NET Framework — przewodnik](../framework/index.md).

## <a name="net-native"></a>Architektura .NET Native

Łańcuch narzędzi kompilatora tworzącego kodu natywnego z wyprzedzeniem elementu time drzewa obiektów (aplikacji), zamiast just-in-time (JIT).

Kompilacja odbywa się na komputerze dewelopera, podobnie jak działa kompilatorze i konsolidatorze C++. Usunięcie nieużywanych kodu, a zużywa więcej czasu optymalizacji go. Wyodrębnia kod z biblioteki, a scala je w pliku wykonywalnego. Wynik jest jeden moduł, który reprezentuje całej aplikacji.

Platformy uniwersalnej systemu Windows była obsługiwana przez platformę .NET Native pierwszy struktury aplikacji. Firma Microsoft obsługuje teraz tworzenia konsoli natywnych aplikacji dla systemu Windows, system macOS i Linux.

Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET standard

Formalną specyfikację interfejsów API architektury .NET, które są dostępne w każdej implementacji .NET.

Specyfikacja .NET Standard jest niekiedy nazywany biblioteki w dokumentacji. Ponieważ biblioteki zawiera implementacji interfejsu API, nie tylko specyfikacje (interfejsy), jest mylący, aby wywołać .NET Standard, "library". Firma Microsoft planuje wyeliminować wykorzystanie z dokumentacji, z wyjątkiem w odniesieniu do nazwy .NET Standard metapackage (`NETStandard.Library`).

Zobacz [.NET Standard](net-standard.md).

## <a name="ngen"></a>NARZĘDZIE NGEN

Generowanie Native (obraz).

Ta technologia można traktować jako trwałe kompilatora JIT. Zazwyczaj kompiluje kodu na komputerze, na którym wykonywany jest kod, ale kompilacji zazwyczaj występuje podczas instalacji.

## <a name="package"></a>Pakiet

Pakiet NuGet &mdash; lub po prostu pakietu &mdash; jest *.zip* plików z jednego lub więcej zestawów o tej samej nazwie, oraz dodatkowe metadane, takie jak nazwisko autora.

*.Zip* plik ma *.nupkg* rozszerzenia i mogą zawierać zasoby, takie jak *.dll* plików i *.xml* plików do użytku z wielu elementu docelowego struktury i wersje. Podczas instalowania aplikacji lub w bibliotece, odpowiednie zasoby są zaznaczone, oparty na platformie docelowej określonej przez aplikację lub biblioteki. Zasoby, które definiują interfejsu znajdują się w *ref* folderu i zasoby, które definiują implementacji znajdują się w *lib* folderu.

## <a name="platform"></a>platforma

System operacyjny i sprzętu, który jest uruchamiany na, takie jak Windows, system macOS, Linux, iOS i Android.

Poniżej przedstawiono przykłady użycia w zdaniach:

- ".NET core jest implementacja i platform .NET". 
- "PCL profile reprezentują platform firmy Microsoft, gdy .NET Standard jest niezależny od platformy."

Dokumentacja platformy .NET często używa "Platformy .NET" oznacza implementacja .NET albo stosu .NET, w tym wszystkich implementacji. Obie te metody użycia zazwyczaj można pobrać mylić z podstawowe znaczenie (systemu operacyjnego/sprzęt), dlatego firma Microsoft planuje wyeliminować te użycia w dokumentacji.

## <a name="runtime"></a>środowisko uruchomieniowe

Środowiska wykonania programu zarządzanych.

System operacyjny jest częścią środowiska uruchomieniowego, ale nie jest częścią środowiska uruchomieniowego .NET. Oto kilka przykładów środowisk uruchomieniowych .NET:

- Środowisko uruchomieniowe języka wspólnego (CLR)
- Podstawowe środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR)
- Architektura .NET native (dla platformy uniwersalnej systemu Windows)
- Środowisko uruchomieniowe mono

Czasami dokumentację .NET używa "runtime" oznacza implementację programu .NET. Na przykład w następujących zdania "runtime" powinna zostać zastąpiona "wdrożenia":

- "Różnych środowisk uruchomieniowych .NET implementuje określonych wersji platformy .NET Standard".
- "Bibliotek, które są przeznaczone do uruchamiania na wiele środowisk uruchomieniowych powinien tej platformy docelowej." (odwołujące się do platformy .NET Standard)
- "Różnych środowisk uruchomieniowych .NET implementuje określonych wersji platformy .NET Standard. … Każda wersja środowiska uruchomieniowego .NET anonsuje najnowsza wersja platformy .NET Standard obsługiwanych..."

Firma Microsoft planuje wyeliminować ten niespójne użycie. 

## <a name="stack"></a>stack

Zestaw programowania technologie, które są stosowane razem w celu tworzenia i uruchamiania aplikacji.

"Stosu .NET" odnosi się do wszystkich implementacji .NET i .NET Standard. Wyrażenie "stos .NET" może odwoływać się do jednego wdrożenia programu .NET. 

## <a name="target-framework"></a>Platforma docelowa

Kolekcja aplikacji .NET lub biblioteki korzysta z interfejsów API.

Aplikacji lub biblioteki można wersja docelowa platformy .NET Standard (na przykład, .NET Standard 2.0), która jest specyfikacją standardowy zestaw interfejsów API we wszystkich wdrożeniach .NET. To aplikacja lub biblioteki można również wersja docelowa platformy konkretnej implementacji .NET, w tym przypadku go pobiera dostępu do konkretnej implementacji interfejsów API. Na przykład aplikacja, która jest przeznaczony dla platformy Xamarin.iOS uzyskuje dostęp do otoki dostarczane do platformy Xamarin iOS interfejsu API.

Dla niektórych docelowych platform (na przykład, .NET Framework) dostępnych interfejsach API są definiowane przez zestawy, które instaluje implementacji programu .NET w systemie, które mogą zawierać struktury aplikacji interfejsów API (na przykład ASP.NET, WinForms). Dla struktury docelowej na podstawie pakietu (na przykład standardowe .NET i .NET Core) framework interfejsy API są definiowane przez pakiety zainstalowane w aplikacji lub biblioteki. W takim przypadku platforma docelowa określa niejawnie metapackage, który odwołuje się do wszystkich pakietów, które składają się platformę.

Zobacz [platform docelowych](frameworks.md).

## <a name="tfm"></a>TFM

Moniker platformy docelowej.

Standardowym formacie token służący do określania platformę docelową aplikacji .NET lub biblioteki. Docelowych platform zwykle odwołuje się krótką nazwę, taką jak `net462`. TFMs długiej (np. NETFramework, Version = 4.6.2) istnieje, ale nie są zwykle używane do określ platformę docelową.

Zobacz [platform docelowych](frameworks.md).

## <a name="uwp"></a>Platforma UWP

Platforma uniwersalna systemu Windows.

Implementacja programu .NET, który jest używany do tworzenia nowoczesnych, obsługą dotyku aplikacji systemu Windows, jak i oprogramowania dla Internetu rzeczy (IoT). Zostało zaprojektowane do ujednolicenie różne typy urządzeń, które chcesz docelowych, łącznie z komputerami, tablety, phablets, telefony i nawet Xbox. Platformy uniwersalnej systemu Windows udostępnia wiele usług, takich jak scentralizowane sklepu, środowiska wykonawczego (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT). Aplikacje mogą być napisane w języku C++, C#, VB.NET i JavaScript. Korzystając z języka C# i VB.NET, interfejsów API architektury .NET są udostępniane przez oprogramowanie .NET Core.

## <a name="see-also"></a>Zobacz także

[.NET — przewodnik](index.md)  
[.NET framework — przewodnik](../framework/index.md)  
[.NET Core](../core/index.md)  
[Omówienie programu ASP.NET](/aspnet/index#pivot=aspnet)  
[Przegląd platformy ASP.NET Core](/aspnet/index#pivot=core)  

