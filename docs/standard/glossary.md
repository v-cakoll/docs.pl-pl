---
title: Słownik platformy .NET
description: Dowiedz się, jak awioduje znaczenie wybranych terminów używanych w dokumentacji .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 8da1d858835210590a80a624fb8989fbfe8e0a91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400436"
---
# <a name="net-glossary"></a>Słownik platformy .NET

Głównym celem tego glosariusza jest wyjaśnienie znaczeń wybranych terminów i akronimów, które często pojawiają się w dokumentacji .NET bez definicji.

## <a name="aot"></a>AOT

Kompilator z wyprzedzeniem.

Podobnie jak [JIT](#jit), ten kompilator tłumaczy również [IL](#il) na kod maszynowy. W przeciwieństwie do kompilacji JIT kompilacji AOT dzieje się przed wykonaniem aplikacji i jest zwykle wykonywane na innym komputerze. Ponieważ łańcuchy narzędzi AOT nie są kompilowane w czasie wykonywania, nie muszą minimalizować czasu spędzonego na kompilacji. Oznacza to, że mogą poświęcić więcej czasu na optymalizację. Ponieważ kontekst AOT jest cała aplikacja, kompilator AOT wykonuje również łączenie modułów krzyżowych i analizy całego programu, co oznacza, że wszystkie odwołania są przestrzegane i jeden plik wykonywalny jest produkowany.

Zobacz [CoreRT](#corert) i [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET

Oryginalny ASP.NET implementacji, która jest dostarczana z .NET Framework.

Czasami ASP.NET jest terminem parasolowym, który odnosi się zarówno do ASP.NET implementacji, w tym ASP.NET Core. Znaczenie, że termin niesie w danym przypadku jest określana przez kontekst. Zapoznaj się z ASP.NET 4.x, jeśli chcesz wyjaśnić, że nie używasz ASP.NET oznacza obie implementacje.

Zobacz [dokumentację ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Wieloplatformowa, wydajna implementacja open source ASP.NET zbudowana na platformie .NET Core.

Zobacz [ASP.NET dokumentację core](/aspnet/#pivot=core).

## <a name="assembly"></a>zestaw

Plik *.dll*/*.exe,* który może zawierać kolekcję interfejsów API, które mogą być wywoływane przez aplikacje lub inne zestawy.

Zestaw może zawierać typy, takie jak interfejsy, klasy, struktury, wyliczenia i delegatów. Zestawy w folderze *bin* projektu są czasami nazywane *plikami binarnymi.* Zobacz też [biblioteka](#library).

## <a name="clr"></a>CLR

Czas wykonywania języka wspólnego.

Dokładne znaczenie zależy od kontekstu, ale zwykle odnosi się do czasu wykonywania .NET Framework. Clr obsługuje alokację pamięci i zarządzanie. ŚRODOWISKO CLR jest również maszyną wirtualną, która nie tylko wykonuje aplikacje, ale także generuje i kompiluje kod w locie przy użyciu kompilatora [JIT.](#jit) Bieżąca implementacja programu Microsoft CLR to tylko system Windows.

## <a name="coreclr"></a>CoreCLR (Rdzeń CLR)

Program .NET Core Common Language Runtime.

Ten clr jest zbudowany z tej samej bazy kodu jako CLR. Pierwotnie CoreCLR był środowiskom uruchomieniowym programu Silverlight i został zaprojektowany do uruchamiania na wielu platformach, w szczególności windows i OS X. CoreCLR jest teraz częścią .NET Core i reprezentuje uproszczoną wersję CLR. Nadal jest to [wieloplatformowy](#cross-platform) czas pracy, w tym obsługa wielu dystrybucji systemu Linux. CoreCLR jest również maszyną wirtualną z możliwościami jit i wykonywania kodu.

## <a name="corefx"></a>CoreFX (Polski)

Biblioteka klas podstawowych .NET Core (BCL)

Zestaw bibliotek, które składają się na System. \* (i w ograniczonym\*zakresie Microsoft. ) przestrzeni nazw. BCL jest ogólnego przeznaczenia, niższego poziomu struktury, że ramy aplikacji wyższego poziomu, takich jak ASP.NET Core, opierać się na. Kod źródłowy bcl .NET Core jest zawarty w [repozytorium runtime .NET Core](https://github.com/dotnet/runtime). Jednak większość interfejsów API .NET Core są również dostępne w .NET Framework, dzięki czemu można myśleć o CoreFX jako rozwidlęce .NET Framework BCL.

## <a name="corert"></a>CoreRT (corert)

Program .NET Core.

W przeciwieństwie do CLR/CoreCLR, CoreRT nie jest maszyną wirtualną, co oznacza, że nie zawiera urządzeń do generowania i uruchamiania kodu w locie, ponieważ nie zawiera [JIT](#jit). Obejmuje jednak [GC](#gc) i możliwość identyfikacji typu runtime (RTTI) i odbicia. Jednak jego system typów został zaprojektowany tak, aby metadane do odbicia nie są wymagane. Dzięki temu o łańcuch narzędzi [AOT,](#aot) które można połączyć z dala zbędne metadane i (co ważniejsze) zidentyfikować kod, który nie używa aplikacji. CoreRT jest w fazie rozwoju.

Zobacz [Wprowadzenie do .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="cross-platform"></a>na wiele platform

Możliwość tworzenia i wykonywania aplikacji, która może być używana w wielu różnych systemach operacyjnych, takich jak Linux, Windows i iOS, bez konieczności ponownego pisania specjalnie dla każdego z nich. Umożliwia to ponowne użycie kodu i spójność między aplikacjami na różnych platformach.

## <a name="ecosystem"></a>Ekosystemu

Całe oprogramowanie środowiska uruchomieniowego, narzędzia programistyczne i zasoby społeczności, które są używane do tworzenia i uruchamiania aplikacji dla danej technologii.

Termin "ekosystem.NET" różni się od podobnych terminów, takich jak ".NET stack" w jego włączenie aplikacji innych firm i bibliotek. Oto przykład w zdaniu:

- "Motywacją standardu [.NET](#net-standard) jest ustanowienie większej jednolitości w ekosystemie .NET."

## <a name="framework"></a>szablon

Ogólnie rzecz biorąc, kompleksowy zbiór interfejsów API, który ułatwia tworzenie i wdrażanie aplikacji, które są oparte na określonej technologii. W tym sensie ogólnym ASP.NET Core i Windows Forms są przykładami struktur aplikacji. Zobacz też [biblioteka](#library).

Słowo "framework" ma bardziej szczegółowe znaczenie techniczne w następujących kategoriach:

- [.NET Framework](#net-framework)
- [ramy docelowe](#target-framework)
- [TFM (pseudonim struktury docelowej)](#tfm)

W istniejącej dokumentacji "framework" czasami odnosi się do [implementacji .NET](#implementation-of-net). Na przykład artykuł może wywołać .NET Core framework. Planujemy wyeliminować to mylące użycie z dokumentacji.

## <a name="gc"></a>GC

Moduł zbierający elementy bezużyteczne.

Moduł zbierający elementy bezużyteczne jest implementacją automatycznego zarządzania pamięcią.  GC zwalnia pamięć zajmowaną przez obiekty, które nie są już używane.

Zobacz [Wyrzucanie elementów bezużytecznych](garbage-collection/index.md).

## <a name="il"></a>IL

Język pośredni.

Języki .NET wyższego poziomu, takie jak C#, kompilują się do zestawu instrukcji sprzętowo-agnostycznych, który nazywa się językiem pośrednim (IL). IL jest czasami określane jako MSIL (Microsoft IL) lub CIL (Common IL).

## <a name="jit"></a>JIT

Kompilator just-in-time.

Podobnie jak [AOT](#aot), ten kompilator tłumaczy [IL](#il) na kod maszynowy, który rozumie procesor. W przeciwieństwie do AOT kompilacji JIT odbywa się na żądanie i jest wykonywana na tym samym komputerze, że kod musi działać na. Ponieważ kompilacja JIT występuje podczas wykonywania aplikacji, czas kompilacji jest częścią czasu wykonywania. W związku z tym kompilatory JIT muszą równoważyć czas poświęcony na optymalizację kodu z oszczędnościami, które może wygenerować wynikowy kod. Ale JIT zna rzeczywisty sprzęt i może uwolnić programistów od konieczności wysłania różnych implementacji.

## <a name="implementation-of-net"></a>wdrożenie programu .NET

Implementacja programu .NET obejmuje następujące elementy:

- Co najmniej jeden bieg. Przykłady: CLR, CoreCLR, CoreRT.
- Biblioteka klas, która implementuje wersję standardu .NET i może zawierać dodatkowe interfejsy API. Przykłady: Biblioteka klas podstawowych .NET Framework, biblioteka podstawowych klas .NET Core.
- Opcjonalnie co najmniej jedna struktura aplikacji. Przykłady: ASP.NET, Formularze systemu Windows i WPF są zawarte w programie .NET Framework.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Przykłady implementacji .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Platforma uniwersalna systemu Windows (UWP)](#uwp)

## <a name="library"></a>biblioteka

Kolekcja interfejsów API, które mogą być wywoływane przez aplikacje lub inne biblioteki. Biblioteka .NET składa się z jednego lub większej [liczby zestawów](#assembly).

Biblioteki słów i [framework](#framework) są często używane synonimie.

## <a name="metapackage"></a>Metapakiet

Pakiet NuGet, który nie ma własnej biblioteki, ale jest tylko lista zależności. Dołączone pakiety mogą opcjonalnie ustanowić interfejs API dla struktury docelowej.

Zobacz [pakiety, metapakiety i struktury](../core/packages.md)

## <a name="mono"></a>Mono

Mono jest open source, [cross-platform](#cross-platform) .NET implementacji, która jest używana głównie wtedy, gdy wymagane jest małe źródło. Jest to środowisko wykonawcze, które zasila aplikacje Xamarin na Androida, Mac, iOS, tvOS i watchOS i koncentruje się przede wszystkim na aplikacjach, które wymagają niewielkich rozmiarów.

Obsługuje wszystkie aktualnie opublikowane wersje .NET Standard.

W przeszłości mono implementowane większy interfejs API .NET Framework i emulował niektóre z najbardziej popularnych funkcji na Unix. Czasami jest używany do uruchamiania aplikacji .NET, które opierają się na tych możliwości ach w uniksie.

Mono jest zwykle używany z kompilatorem just-in-time, ale zawiera również pełny kompilator statyczny (kompilacja z wyprzedzeniem), który jest używany na platformach takich jak iOS.

Aby dowiedzieć się więcej o mono, zobacz [dokumentację Mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Termin parasolowy dla [.NET Standard](#net-standard) i wszystkich implementacji i obciążeń [.NET.](#implementation-of-net) Zawsze kapitalizowane, nigdy ".Net".

Zobacz [przewodnik .NET](index.md)

## <a name="net-core"></a>.NET Core

Implementacja programu .NET o dużej wydajności i wydajności. Zawiera core common language runtime (CoreCLR), core AOT Runtime (CoreRT, w rozwoju), core base class library i Core SDK.

Zobacz [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>Interfejs wiersza polecenia platformy .NET Core

Wieloplatformowy łańcuch narzędzi do tworzenia aplikacji .NET Core.

Zobacz [.NET Core CLI](../core/tools/index.md).

## <a name="net-core-sdk"></a>Zestaw .NET Core SDK

Zestaw bibliotek i narzędzi, które umożliwiają deweloperom tworzenie aplikacji i bibliotek .NET Core. Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.

Zobacz [omówienie sdk rdzenia .NET .](../core/sdk.md)

## <a name="net-framework"></a>.NET Framework

Implementacja .NET, która jest uruchamiana tylko w systemie Windows. Zawiera środowisko uruchomieniowe języka wspólnego (CLR), bibliotekę klas podstawowych i biblioteki struktury aplikacji, takie jak ASP.NET, Formularze systemu Windows i WPF.

Zobacz [.NET Framework Guide](../framework/index.md).

## <a name="net-native"></a>Architektura .NET Native

Łańcuch narzędzi kompilatora, który tworzy kod macierzysty z wyprzedzeniem (AOT), w przeciwieństwie do just-in-time (JIT).

Kompilacja odbywa się na komputerze dewelopera podobny do sposobu kompilator c++ i konsolidator działa. Usuwa nieużywany kod i poświęca więcej czasu na jego optymalizację. Wyodrębnia kod z bibliotek i scala je z plikiem wykonywalnym. Wynik jest pojedynczy moduł, który reprezentuje całą aplikację.

Platforma UWP była pierwszą strukturą aplikacji obsługiwaną przez serwer .NET Native. Teraz obsługujemy tworzenie natywnych aplikacji konsolowych dla systemów Windows, macOS i Linux.

Zobacz [Wprowadzenie do .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Formalna specyfikacja interfejsów API .NET, które są dostępne w każdej implementacji .NET.

Specyfikacja standardu .NET jest czasami nazywana biblioteką w dokumentacji. Ponieważ biblioteka zawiera implementacje interfejsu API, nie tylko specyfikacje (interfejsy), nazywanie .NET Standard "biblioteką" jest mylące. Planujemy wyeliminować to użycie z dokumentacji, z wyjątkiem odwołania do nazwy`NETStandard.Library`metapakietu .NET Standard ( ).

Zobacz [.NET Standard](net-standard.md).

## <a name="ngen"></a>Ngen

Generacja natywna (obrazu).

Tę technologię można pomyśleć jako trwały kompilator JIT. Zazwyczaj kompiluje kod na komputerze, na którym wykonywany jest kod, ale kompilacja zwykle występuje w czasie instalacji.

## <a name="package"></a>Pakiet

Pakiet &mdash; NuGet lub tylko &mdash; pakiet jest plik *zip* z jednym lub więcej zestawów o tej samej nazwie wraz z dodatkowych metadanych, takich jak nazwa autora.

Plik *zip* ma rozszerzenie *.nupkg* i może zawierać zasoby, takie jak pliki *dll* i *xml,* do użytku z wieloma platformami docelowymi i wersjami. Po zainstalowaniu w aplikacji lub bibliotece odpowiednie zasoby są wybierane na podstawie struktury docelowej określonej przez aplikację lub bibliotekę. Zasoby, które definiują interfejs znajdują się w folderze *ref,* a zasoby definiujące implementację znajdują się w folderze *lib.*

## <a name="platform"></a>platforma

System operacyjny i sprzęt, na który działa, takich jak Windows, macOS, Linux, iOS i Android.

Oto przykłady użycia w zdaniach:

- ".NET Core to implementacja programu .NET na wielu platformach".
- "Profile PCL reprezentują platformy firmy Microsoft, podczas gdy standard .NET jest nieskrępowy dla platformy".

Dokumentacja platformy .NET często używa "platformy.NET" oznacza implementację .NET lub stos .NET, w tym wszystkie implementacje. Oba te użycia mają tendencję do mylone z podstawowym (OS / hardware) znaczenie, więc planujemy wyeliminować te użycia z dokumentacji.

## <a name="runtime"></a>środowisko uruchomieniowe

Środowisko wykonywania programu zarządzanego.

Środowisko operacyjne jest częścią środowiska środowiska uruchomieniowego, ale nie jest częścią środowiska uruchomieniowego .NET. Oto kilka przykładów uruchomień programu .NET:

- Środowisko uruchomieniowe języka wspólnego (CLR)
- Podstawowy czas wykonywania języka wspólnego (CoreCLR)
- Natywna .NET (dla programu UWP)
- Czas pracy mono

Dokumentacja .NET czasami używa "runtime" oznacza implementację .NET. Na przykład w następujących zdaniach "runtime" należy zastąpić "implementacji":

- "Różne uruchomienia .NET implementują określone wersje standardu .NET."
- "Biblioteki, które są przeznaczone do uruchamiania w wielu serwerach uruchamianych powinny być przeznaczone dla tej struktury." (w odniesieniu do .NET Standard)
- "Różne uruchomienia programu .NET implementują określone wersje standardu .NET. … Każda wersja programu .NET jest anonsuje najwyższą wersję standardu .NET, która obsługuje ..."

Planujemy wyeliminować to niespójne użycie.

## <a name="stack"></a>stack

Zestaw technologii programowania, które są używane razem do tworzenia i uruchamiania aplikacji.

"Stos .NET" odnosi się do standardu .NET i wszystkich implementacji .NET. Wyrażenie "stos .NET" może odwoływać się do jednej implementacji .NET.

## <a name="target-framework"></a>ramy docelowe

Kolekcja interfejsów API, na których opiera się aplikacja lub biblioteka .NET.

Aplikacja lub biblioteka może kierować na wersję .NET Standard (na przykład .NET Standard 2.0), która jest specyfikacją standardowego zestawu interfejsów API we wszystkich implementacjach .NET. Aplikacja lub biblioteka może również kierować wersję określonej implementacji .NET, w którym to przypadku uzyskuje dostęp do interfejsów API specyficznych dla implementacji. Na przykład aplikacja, która jest przeznaczona dla interfejsu Xamarin.iOS, uzyskuje dostęp do otoki interfejsu API z interfejsem iOS dostarczonych przez interfejsy Xamarin.

W przypadku niektórych platform docelowych (na przykład .NET Framework) dostępne interfejsy API są definiowane przez zestawy, które implementacja .NET instaluje w systemie, co może obejmować interfejsy API platformy aplikacji (na przykład ASP.NET, WinForms). W przypadku platform docelowych opartych na pakiecie (takich jak .NET Standard i .NET Core) interfejsy API struktury są definiowane przez pakiety zainstalowane w aplikacji lub bibliotece. W takim przypadku platformy docelowej niejawnie określa metapakiet, który odwołuje się do wszystkich pakietów, które razem tworzą framework.

Zobacz [platformy docelowe](frameworks.md).

## <a name="tfm"></a>Tfm

Moniker framework docelowy.

Znormalizowany format tokenu do określania struktury docelowej aplikacji lub biblioteki .NET. Platformdocelowych są zazwyczaj odwołuje się krótką nazwę, takich jak `net462`. Długie tfmy (takie jak . NETFramework,Version=4.6.2) istnieją, ale nie są zazwyczaj używane do określania struktury docelowej.

Zobacz [platformy docelowe](frameworks.md).

## <a name="uwp"></a>Platforma UWP

Uniwersalna platforma systemu Windows.

Implementacja .NET, która jest używana do tworzenia nowoczesnych aplikacji i oprogramowania systemu Windows z obsługą dotyku dla Internetu rzeczy (IoT). Został zaprojektowany w celu uniewinnienia różnych typów urządzeń, na które chcesz kierować reklamy, w tym komputerów, tabletów, phabletów, telefonów, a nawet konsoli Xbox. Platforma UWP udostępnia wiele usług, takich jak scentralizowany sklep z aplikacjami, środowisko wykonywania (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT). Aplikacje można zapisywać w językach C++, C#, Visual Basic i JavaScript. Korzystając z języka C# i Języka Visual Basic, interfejsy API .NET są dostarczane przez .NET Core.

## <a name="see-also"></a>Zobacz też

- [.NET — przewodnik](index.md)
- [.NET framework — przewodnik](../framework/index.md)
- [.NET Core](../core/index.md)
- [Przegląd ASP.NET](/aspnet/index#pivot=aspnet)
- [ASP.NET Podstawowe omówienie](/aspnet/index#pivot=core)
