---
title: Słownik platformy .NET
description: Sprawdź znaczenie wybranych terminów używanych w dokumentacji programu .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: caff1ee4c8e3ad133016b774fdb235bd1ef59637
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106924"
---
# <a name="net-glossary"></a>Słownik platformy .NET

Głównym celem tego słownika jest wyjaśnienie znaczenia wybranych terminów i akronimów, które często pojawiają się w dokumentacji programu .NET bez definicji.

## <a name="aot"></a>AOT

Kompilator przed czasem.

Podobnie jak w przypadku [JIT](#jit), ten kompilator tłumaczy również [Il](#il) na kod maszynowy. W przeciwieństwie do kompilacji JIT kompilacja AOT jest wykonywana przed wykonaniem aplikacji i zwykle jest wykonywana na innym komputerze. Ponieważ nie są kompilowane w czasie wykonywania, nie trzeba minimalizować czasu kompilowania z użyciem narzędzi AOT. Oznacza to, że mogą oni poświęcać więcej czasu na optymalizację. Ponieważ kontekst AOT jest całą aplikacją, kompilator AOT wykonuje również łączenie między modułami i analizę całego programu, co oznacza, że wszystkie odwołania są obserwowane i tworzony jest pojedynczy plik wykonywalny.

Zobacz [CoreRT](#corert) i [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET 

Oryginalna implementacja ASP.NET, która jest dostarczana z .NET Framework.

Czasami ASP.NET jest terminem parasola, który odwołuje się do obu implementacji ASP.NET, w tym ASP.NET Core. Oznacza to, że termin odbywa się w każdym podanym wystąpieniu jest określony przez kontekstu. Zapoznaj się z ASP.NET 4. x, jeśli chcesz, aby było jasne, że nie używasz ASP.NET do oznaczania obu implementacji. 

Zobacz [dokumentację ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Wieloplatformowa implementacja ASP.NET typu open source oparta na platformie .NET Core.

Zobacz [dokumentację ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>zestaw

Plik *. dll*/ *. exe* , który może zawierać kolekcję interfejsów API, które mogą być wywoływane przez aplikacje lub inne zestawy.

Zestaw może zawierać typy, takie jak interfejsy, klasy, struktury, wyliczenia i Delegaty. Zestawy w folderze *bin* projektu są czasami określane jako *pliki binarne*. Zobacz również [Biblioteka](#library).

## <a name="clr"></a>CLR

Środowisko uruchomieniowe języka wspólnego.

Dokładne znaczenie zależy od kontekstu, ale zazwyczaj odnosi się to do środowiska uruchomieniowego .NET Framework. Środowisko CLR obsługuje alokacje pamięci i zarządzanie nimi. Środowisko CLR jest również maszyną wirtualną, która nie tylko wykonuje aplikacje, ale również generuje i kompiluje kod na bieżąco przy użyciu kompilatora [JIT](#jit) . Bieżąca implementacja środowiska Microsoft CLR jest tylko w systemie Windows.

## <a name="coreclr"></a>CoreCLR

Środowisko uruchomieniowe języka wspólnego platformy .NET Core.

To środowisko CLR jest zbudowane z tej samej bazy kodu, co środowisko CLR. Pierwotnie CoreCLR było środowisko uruchomieniowe programu Silverlight i zostało zaprojektowane tak, aby było uruchamiane na wielu platformach, a w systemach Windows i OS X. CoreCLR jest teraz częścią programu .NET Core i reprezentuje uproszczoną wersję środowiska CLR. Nadal jest to środowisko uruchomieniowe dla wielu [platform](#cross-platform) , w tym teraz obsługiwane są różne dystrybucje systemu Linux. CoreCLR jest również maszyną wirtualną z możliwościami wykonywania JIT i kodu.

## <a name="corefx"></a>CoreFX

Podstawowa Biblioteka klas .NET Core (BCL)

Przestrzenie nazw zestawu, biblioteki, które tworzą Microsoft. i System.* (a w ograniczonym zakresie Microsoft.*). BCL jest ogólnym celem, na niższym poziomie, które platformy aplikacji wyższego poziomu, takie jak ASP.NET Core, Kompiluj na. Kod źródłowy programu .NET Core BCL jest zawarty w [repozytorium CoreFX](https://github.com/dotnet/corefx). Jednak większość interfejsów API platformy .NET Core jest również dostępna w .NET Framework, więc można traktować CoreFX jako rozwidlenie .NET Framework BCL.

## <a name="corert"></a>CoreRT

Środowisko uruchomieniowe platformy .NET Core.

W przeciwieństwie do środowiska CLR/CoreCLR, CoreRT nie jest maszyną wirtualną, co oznacza, że nie obejmuje ona obiektów do generowania i uruchamiania kodu na bieżąco, ponieważ nie zawiera on [JIT](#jit). Zawiera on jednak funkcję [GC](#gc) i możliwość identyfikacji typu czasu wykonywania (RTTI) i odbicie. Jednak jego system typów został zaprojektowany tak, aby metadane odbicia nie były wymagane. Umożliwia to korzystanie z łańcucha narzędzi [AOT](#aot) , który może łączyć zbędne metadane i (dokładniej) identyfikować kod nieużywany przez aplikację. CoreRT jest w trakcie opracowywania.

Zobacz [wprowadzenie do .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="cross-platform"></a>na wiele platform

Możliwość tworzenia i uruchamiania aplikacji, która może być używana w wielu różnych systemach operacyjnych, takich jak Linux, Windows i iOS, bez konieczności ponownego pisania dla każdej z nich. Umożliwia to ponowne użycie kodu i spójność między aplikacjami na różnych platformach.

## <a name="ecosystem"></a>uwolnieni

Wszystkie oprogramowanie środowiska uruchomieniowego, narzędzia programistyczne i zasoby społeczności, które są używane do kompilowania i uruchamiania aplikacji dla danej technologii.

Termin "ekosystem .NET" różni się od podobnych warunków, takich jak "stos .NET" w ramach dołączania do aplikacji i bibliotek innych firm. Oto przykład w zdaniu:

- "Motywacja za [.NET Standard](#net-standard) polega na ustanowieniu większej jednorodności w ekosystemie .NET". 

## <a name="framework"></a>szablon

Ogólnie kompleksowe zbieranie interfejsów API, które ułatwiają tworzenie i wdrażanie aplikacji opartych na określonej technologii. W tym ogólnym sensie ASP.NET Core i Windows Forms są przykładami struktur aplikacji. Zobacz również [Biblioteka](#library).

Słowo "Framework" ma bardziej charakterystyczne znaczenie techniczne w następujących warunkach:
- [.NET Framework](#net-framework)
- [Platforma docelowa](#target-framework)
- [TFM (moniker struktury docelowej)](#tfm)

W istniejącej dokumentacji "struktura" czasami odnosi się do [implementacji platformy .NET](#implementation-of-net). Na przykład artykuł może wywoływać platformę .NET Core. Firma Microsoft planuje wyeliminować to mylące użycie z dokumentacji.

## <a name="gc"></a>GC

Moduł zbierający elementy bezużyteczne.

Moduł wyrzucania elementów bezużytecznych jest implementacją automatycznego zarządzania pamięcią.  GC zwalnia pamięć zajętą przez obiekty, które nie są już używane. 

Zobacz [odzyskiwanie pamięci](garbage-collection/index.md).

## <a name="il"></a>IL

Język pośredni.

Języki platformy .NET wyższego poziomu, takie C#jak, Kompiluj w dół do zestawu instrukcji niezależny od sprzętu, który jest nazywany językiem pośrednim (IL). Kod IL jest czasami określany jako MSIL (Microsoft IL) lub CIL (Common IL).

## <a name="jit"></a>JIT

Kompilator just in Time.

Podobnie jak w przypadku [drzewa AOT](#aot), ten kompilator tłumaczy [Il](#il) na kod maszynowy, który jest rozpoznawany przez procesor. W przeciwieństwie do drzewa AOT, kompilacja JIT odbywa się na żądanie i jest wykonywana na tym samym komputerze, na którym kod musi być uruchomiony. Ponieważ kompilacja JIT odbywa się podczas wykonywania aplikacji, czas kompilacji jest częścią czasu wykonywania. W efekcie kompilatory JIT muszą zrównoważyć czas spędzony na optymalizowaniu kodu przed oszczędnościami, które może wyprodukować ten kod. Jednak kompilator JIT wie o rzeczywistym sprzęcie i może zwolnić deweloperów, którzy muszą dostarczać różne implementacje.

## <a name="implementation-of-net"></a>Implementacja platformy .NET

Implementacja programu .NET obejmuje następujące elementy:

- Co najmniej jedno środowisko uruchomieniowe. Przykłady: CLR, CoreCLR, CoreRT.
- Biblioteka klas implementująca wersję .NET Standard i może zawierać dodatkowe interfejsy API. Przykłady: .NET Framework podstawowa Biblioteka klas, podstawowa Biblioteka klas .NET Core.
- Opcjonalnie co najmniej jedna struktura aplikacji. Przykłady: W .NET Framework znajdują się ASP.NET, Windows Forms i WPF.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Przykłady implementacji platformy .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Platforma uniwersalna systemu Windows (UWP)](#uwp)

## <a name="library"></a>biblioteka

Kolekcja interfejsów API, które mogą być wywoływane przez aplikacje lub inne biblioteki. Biblioteka .NET składa się z co najmniej jednego [](#assembly)zestawu.

Słowa Library i [Framework](#framework) są często używane.

## <a name="metapackage"></a>Pakiet

Pakiet NuGet, który nie ma własnej biblioteki, ale jest tylko listą zależności. Dołączone pakiety mogą opcjonalnie ustanowić interfejs API dla platformy docelowej.

Zobacz [pakiety, aplikacje i struktury](../core/packages.md)

## <a name="mono"></a>Mono

Mono to wieloplatformowa implementacja [](#cross-platform) platformy .NET, która jest używana głównie w przypadku, gdy wymagane jest małe środowisko uruchomieniowe. Jest to środowisko uruchomieniowe, które umożliwia aplikacjom platformy Xamarin w systemach Android, Mac, iOS, systemu tvOS i systemu watchOS i koncentruje się głównie na aplikacjach, które wymagają małego rozmiaru.

Obsługuje ona wszystkie aktualnie opublikowane wersje .NET Standard.

W przeszłości, mono zaimplementowano większy interfejs API .NET Framework i emuluje niektóre z najpopularniejszych możliwości w systemie UNIX. Jest on czasami używany do uruchamiania aplikacji .NET, które są zależne od tych funkcji w systemie UNIX.

Mono jest zazwyczaj używany z kompilatorem just-in-Time, ale również zawiera pełny statyczny kompilator (kompilacja przed czasem), która jest używana na platformach takich jak iOS.

Aby dowiedzieć się więcej o programie mono, zobacz [dokumentację narzędzia mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Termin parasol dla [.NET Standard](#net-standard) i wszystkie implementacje i obciążenia [platformy .NET](#implementation-of-net) . Zawsze wersaliki, nigdy ".NET".

Zobacz [Przewodnik po platformie .NET](index.md)

## <a name="net-core"></a>.NET Core 

Implementacja platformy .NET na wielu platformach i o wysokiej wydajności. Obejmuje podstawowe środowisko uruchomieniowe języka wspólnego (CoreCLR), podstawowe środowisko uruchomieniowe AOT (CoreRT, w programowaniu), podstawową bibliotekę klas podstawowych i podstawowy zestaw SDK.

Zobacz [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>Interfejs wiersza polecenia platformy .NET Core

Międzyplatformowe łańcucha narzędzi do tworzenia aplikacji platformy .NET Core.

Zobacz [Narzędzia interfejsu wiersza polecenia platformy .NET Core](../core/tools/index.md).

## <a name="net-core-sdk"></a>zestaw .NET Core SDK

Zestaw bibliotek i narzędzi umożliwiających deweloperom tworzenie aplikacji i bibliotek platformy .NET Core. Zawiera [interfejs wiersza polecenia platformy .NET Core](#net-core-cli) do kompilowania aplikacji, bibliotek .NET Core i środowiska uruchomieniowego na potrzeby kompilowania i uruchamiania aplikacji oraz plików wykonywalnych dotnet (*dotnet. exe*), które uruchamiają polecenia CLI i uruchamiają aplikacje.

Zobacz [zestaw .NET Core SDK przegląd](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementacja programu .NET, która działa tylko w systemie Windows. Obejmuje środowisko uruchomieniowe języka wspólnego (CLR), bibliotekę klas podstawowych i biblioteki struktury aplikacji, takie jak ASP.NET, Windows Forms i WPF.

Zobacz [przewodnik .NET Framework](../framework/index.md).

## <a name="net-native"></a>Architektura .NET Native

Łańcuch narzędzi kompilatora, który generuje kod natywny (AOT), w przeciwieństwie do just-in-Time (JIT).

Kompilacja odbywa się na komputerze dewelopera, podobnie jak w przypadku C++ działania kompilatora i konsolidatora. Usuwa nieużywany kod i poświęca więcej czasu na optymalizację. Wyodrębnia kod z bibliotek i scala je do pliku wykonywalnego. Wynikiem jest pojedynczy moduł, który reprezentuje całą aplikację.

PLATFORMY UWP była pierwszą platformą aplikacji obsługiwaną przez .NET Native. Teraz obsługujemy tworzenie natywnych aplikacji konsolowych dla systemów Windows, macOS i Linux.

Zobacz [wprowadzenie do .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Formalna Specyfikacja interfejsów API platformy .NET, które są dostępne w każdej implementacji platformy .NET.

Specyfikacja .NET Standard jest czasami nazywana biblioteką w dokumentacji. Ponieważ biblioteka zawiera implementacje interfejsu API, a nie tylko specyfikacje (interfejsy), nie prowadzi do wywołania .NET Standard "biblioteki". Firma Microsoft planuje wyeliminować to użycie z dokumentacji, z wyjątkiem odwołującego się do nazwy pakietu .NET Standard (`NETStandard.Library`).

Zobacz [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Generowanie natywne (obraz).

Tę technologię można traktować jako trwały kompilator JIT. Zwykle kompiluje kod na komputerze, na którym wykonywany jest kod, ale kompilacja zwykle występuje w czasie instalacji.

## <a name="package"></a>Package

Pakiet &mdash; NuGet lub tylko pakiet &mdash; to plik *. zip* z co najmniej jednym zestawem o tej samej nazwie wraz z dodatkowymi metadanymi, takimi jak nazwa autora.

Plik *. zip* ma rozszerzenie *. nupkg* i może zawierać elementy zawartości, takie jak pliki *. dll* i pliki *. XML* , do użycia z wieloma platformami i wersjami docelowymi. Po zainstalowaniu w aplikacji lub bibliotece odpowiednie zasoby są wybierane na podstawie platformy docelowej określonej przez aplikację lub bibliotekę. Elementy zawartości definiujące interfejs znajdują się w folderze *ref* , a zasoby, które definiują implementację, znajdują się w folderze *lib* .

## <a name="platform"></a>platforma

System operacyjny i sprzęt, na którym działa program, na przykład Windows, macOS, Linux, iOS i Android.

Poniżej przedstawiono przykłady użycia w zdaniach:

- ".NET Core to wieloplatformowa implementacja platformy .NET". 
- "Profile PCL reprezentują platformy firmy Microsoft, podczas gdy .NET Standard jest niezależny od na platformę".

Dokumentacja platformy .NET często używa "platformy .NET" do oznaczania implementacji platformy .NET lub stosu .NET, w tym wszystkich implementacji. Oba te sposoby użycia mają na celu pomylić z podstawowym (system operacyjny/sprzętowy) znaczeniem, dlatego planujemy wyeliminować te zastosowania z dokumentacji.

## <a name="runtime"></a>środowisko uruchomieniowe

Środowisko wykonawcze dla programu zarządzanego.

System operacyjny jest częścią środowiska uruchomieniowego, ale nie należy do środowiska uruchomieniowego .NET. Poniżej przedstawiono kilka przykładów środowiska uruchomieniowego platformy .NET:

- Środowisko uruchomieniowe języka wspólnego (CLR)
- Podstawowe środowisko uruchomieniowe języka wspólnego (CoreCLR)
- .NET Native (dla platformy UWP)
- Środowisko uruchomieniowe mono

Dokumentacja platformy .NET czasami używa "środowiska uruchomieniowego" do oznaczania implementacji platformy .NET. Na przykład w następujących zdaniach "środowisko uruchomieniowe" należy zastąpić "implementacją":

- "Różne środowiska uruchomieniowe platformy .NET implementują określone wersje .NET Standard".
- "Biblioteki, które są przeznaczone do uruchamiania w wielu środowiskach uruchomieniowych, powinny być ukierunkowane na tę platformę". (odwołujące się do .NET Standard)
- "Różne środowiska uruchomieniowe platformy .NET implementują określone wersje .NET Standard. … Każda wersja środowiska uruchomieniowego .NET anonsuje najwyższą wersję .NET Standard obsługiwaną przez program... "

Planujemy wyeliminować to niespójne użycie. 

## <a name="stack"></a>stack

Zestaw technologii programistycznych, które są używane razem do kompilowania i uruchamiania aplikacji.

"Stos .NET" odnosi się do .NET Standard i wszystkich implementacji platformy .NET. Fraza "stos platformy .NET" może odnosić się do jednej implementacji platformy .NET. 

## <a name="target-framework"></a>Platforma docelowa

Kolekcja interfejsów API, na których opiera się aplikacja lub biblioteka platformy .NET.

Aplikacja lub biblioteka może być ukierunkowana na wersję .NET Standard (na przykład .NET Standard 2,0), która jest specyfikacją standardowego zestawu interfejsów API we wszystkich implementacjach platformy .NET. Aplikacja lub biblioteka może być również ukierunkowana na wersję konkretnej implementacji platformy .NET, w takim przypadku uzyskuje dostęp do interfejsów API specyficznych dla implementacji. Na przykład aplikacja przeznaczona dla platformy Xamarin. iOS uzyskuje dostęp do otok interfejsu API systemu iOS dostarczonych przez platformę Xamarin.

W przypadku niektórych platform docelowych (na przykład .NET Framework) dostępne interfejsy API są definiowane przez zestawy, które są instalowane przez implementację .NET w systemie, który może obejmować interfejsy API platformy aplikacji (na przykład ASP.NET, WinForms). W przypadku platform docelowych opartych na pakietach (takich jak .NET Standard i .NET Core) interfejsy API platformy są definiowane przez pakiety zainstalowane w aplikacji lub bibliotece. W takim przypadku platforma docelowa niejawnie określa pakiet, który odwołuje się do wszystkich pakietów, które razem tworzą strukturę.

Zobacz [platformę](frameworks.md)docelową.

## <a name="tfm"></a>TFM

Moniker platformy docelowej.

Standardowy format tokenu służący do określania docelowej platformy aplikacji lub biblioteki platformy .NET. Struktury docelowe są zwykle przywoływane przez krótką nazwę, na `net462`przykład. Long-form TFMs (na przykład. NETFramework, Version = 4.6.2) istnieje, ale nie są zwykle używane do określania platformy docelowej.

Zobacz [platformę](frameworks.md)docelową.

## <a name="uwp"></a>Platforma UWP

Platforma uniwersalna systemu Windows.

Implementacja platformy .NET, która jest używana do tworzenia nowoczesnych aplikacji i oprogramowania systemu Windows z obsługą dotykową dla Internet rzeczy (IoT). Ma ona na celu ujednolicenie różnych typów urządzeń, które mogą być ukierunkowane, w tym komputerów, tabletów, phablets, telefonów, a nawet z konsoli Xbox. Usługa platformy UWP udostępnia wiele usług, takich jak scentralizowany magazyn aplikacji, środowisko wykonawcze i zestaw interfejsów API systemu Windows, które mają być używane zamiast Win32 (WinRT). Aplikacje mogą być zapisywane w C++, C#, VB.NET i JavaScript. W przypadku C# używania i VB.NET interfejsy API platformy .NET są udostępniane przez platformę .NET Core.

## <a name="see-also"></a>Zobacz także

- [.NET — przewodnik](index.md)
- [.NET framework — przewodnik](../framework/index.md)
- [.NET Core](../core/index.md)
- [ASP.NET — Omówienie](/aspnet/index#pivot=aspnet)
- [Przegląd ASP.NET Core](/aspnet/index#pivot=core)
