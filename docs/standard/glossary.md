---
title: Słownik platformy .NET
description: Poznaj znaczenie wybranych terminów używanych w dokumentacji platformy .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 590d44ac64bc2b86ed0a082ae5185cf60b28c36c
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291564"
---
# <a name="net-glossary"></a>Słownik platformy .NET

Głównym celem tego glosariusza jest wyjaśnienie znaczenia wybranych terminów i akronimów, które często pojawiają się w dokumentacji platformy .NET bez definicji.

## <a name="aot"></a>AOT

Kompilator z wyprzedzeniem.

Podobnie jak [JIT](#jit), ten kompilator tłumaczy również [IL](#il) do kodu maszynowego. W przeciwieństwie do kompilacji JIT kompilacji AOT dzieje się przed wykonaniem aplikacji i jest zwykle wykonywane na innym komputerze. Ponieważ łańcuchy narzędzi AOT nie skompilować w czasie wykonywania, nie trzeba minimalizować czas spędzony na kompilowaniu. Oznacza to, że mogą poświęcić więcej czasu na optymalizację. Ponieważ kontekst obiektu aplikacji AOT jest całą aplikacją, kompilator aplikacji AOT wykonuje również łączenie między modułami i analizę całego programu, co oznacza, że wszystkie odwołania są przestrzegane i powstaje pojedynczy plik wykonywalny.

Zobacz [CoreRT](#corert) i [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET

Oryginalna implementacja ASP.NET, która jest dostarczana z platformą .NET Framework.

Czasami ASP.NET jest terminem parasolowym, który odnosi się zarówno do implementacji ASP.NET, w tym ASP.NET Core. Znaczenie, że termin niesie w danym wystąpieniu zależy od kontekstu. Jeśli chcesz wyjaśnić, że nie używasz ASP.NET oznacza obie implementacje, należy zapoznać się z ASP.NET 4.x.

Zobacz [ASP.NET dokumentację](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Wieloplatformowa, wydajna, otwarta implementacja ASP.NET oparta na programie .NET Core.

Zobacz [ASP.NET Dokumentacja core](/aspnet/#pivot=core).

## <a name="assembly"></a>zestaw

Plik *.dll*/*.exe,* który może zawierać kolekcję interfejsów API, które mogą być wywoływane przez aplikacje lub inne zestawy.

Zestaw może zawierać typy, takie jak interfejsy, klasy, struktury, wyliczenia i delegatów. Zestawy w folderze *bin* projektu są czasami określane jako *pliki binarne*. Zobacz też [biblioteka](#library).

## <a name="clr"></a>CLR

Środowisko wykonawcze języka wspólnego.

Dokładne znaczenie zależy od kontekstu, ale środowisko uruchomieniowe języka wspólnego zwykle odnosi się do środowiska wykonawczego programu .NET Framework. CLR obsługuje alokacji pamięci i zarządzania. CLR jest również maszyną wirtualną, która nie tylko wykonuje aplikacje, ale także generuje i kompiluje kod w locie przy użyciu kompilatora [JIT.](#jit) Bieżąca implementacja programu Microsoft CLR jest dostępna tylko w systemie Windows.

## <a name="coreclr"></a>CoreCLR (CoreCLR)

.NET Core Wspólny język środowiska uruchomieniowego.

Ten CLR jest zbudowany z tej samej bazy kodu co CLR. Pierwotnie CoreCLR był czasem wykonywania Silverlight i został zaprojektowany do pracy na wielu platformach, w szczególności Windows i OS X. CoreCLR jest teraz częścią .NET Core i reprezentuje uproszczoną wersję CLR. Nadal jest to środowisko uruchomieniowe [między platformami,](#cross-platform) teraz w tym obsługa wielu dystrybucji Linuksa. CoreCLR jest również maszyną wirtualną z możliwościami JIT i wykonywania kodu.

## <a name="corefx"></a>CoreFX ( CoreFX )

Biblioteka klas podstawowych .NET Core (BCL)

Zestaw bibliotek, które składają się na System. \* (i w ograniczonym\*zakresie Microsoft. ) przestrzenie nazw. BCL jest ogólnego przeznaczenia, niższego poziomu struktury, które wyższego poziomu struktury aplikacji, takich jak ASP.NET Core, opierać się na. Kod źródłowy listy BCL .NET Core znajduje się w [repozytorium środowiska uruchomieniowego .NET Core](https://github.com/dotnet/runtime). Jednak większość interfejsów API .NET Core są również dostępne w .NET Framework, dzięki czemu można myśleć CoreFX jako rozwidlenia .NET Framework BCL.

## <a name="corert"></a>CoreRT ( CoreRT )

.NET Core środowiska uruchomieniowego.

W przeciwieństwie do CLR/CoreCLR, CoreRT nie jest maszyną wirtualną, co oznacza, że nie zawiera urządzeń do generowania i uruchamiania kodu w locie, ponieważ nie zawiera [JIT](#jit). Obejmuje ona jednak [gc](#gc) i możliwość identyfikacji typu w czasie wykonywania (RTTI) i odbicia. Jednak jego system typu jest zaprojektowany tak, że metadane do odbicia nie jest wymagane. Nie wymagających metadanych umożliwia posiadanie łańcucha narzędzi [AOT,](#aot) które można połączyć zbędnych metadanych i (co ważniejsze) zidentyfikować kod, który aplikacja nie używa. CoreRT jest w fazie rozwoju.

Zobacz [Wprowadzenie do platformy .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="cross-platform"></a>na wiele platform

Możliwość tworzenia i wykonywania aplikacji, która może być używana w wielu różnych systemach operacyjnych, takich jak Linux, Windows i iOS, bez konieczności przepisywania specjalnie dla każdego z nich. Umożliwia to ponowne użycie kodu i spójność między aplikacjami na różnych platformach.

## <a name="ecosystem"></a>Ekosystemu

Wszystkie oprogramowanie wykonawcze, narzędzia programistyczne i zasoby społeczności, które są używane do tworzenia i uruchamiania aplikacji dla danej technologii.

Termin "ekosystem.NET" różni się od podobnych terminów, takich jak "stos.NET" w jego włączenie aplikacji i bibliotek innych firm. Oto przykład w zdaniu:

- "Motywacją standardu [.NET](#net-standard) jest ustanowienie większej jednolitości w ekosystemie .NET."

## <a name="framework"></a>szablon

Ogólnie rzecz biorąc kompleksowy zbiór interfejsów API, który ułatwia tworzenie i wdrażanie aplikacji, które są oparte na określonej technologii. W tym ogólnym znaczeniu ASP.NET Core i Windows Forms są przykładami struktur aplikacji. Zobacz też [biblioteka](#library).

Słowo "framework" ma bardziej szczegółowe znaczenie techniczne w następujących terminach:

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

Języki platformy .NET wyższego poziomu, takie jak C#, kompilują się do zestawu instrukcji niezależnego od sprzętu, który jest nazywany językiem pośrednim (IL). IL jest czasami określane jako MSIL (Microsoft IL) lub CIL (Common IL).

## <a name="jit"></a>JIT

Kompilator just-in-time.

Podobnie jak [AOT](#aot), ten kompilator tłumaczy [IL](#il) do kodu maszynowego, który procesor rozumie. W przeciwieństwie do AOT kompilacji JIT odbywa się na żądanie i jest wykonywana na tym samym komputerze, na który kod musi działać na. Ponieważ kompilacja JIT występuje podczas wykonywania aplikacji, czas kompilacji jest częścią czasu wykonywania. W związku z tym kompilatory JIT muszą zrównoważyć czas spędzony na optymalizacji kodu względem oszczędności, które można utworzyć wynikowy kod. Ale JIT zna rzeczywisty sprzęt i może uwolnić programistów od konieczności wysyłki różnych implementacji.

## <a name="implementation-of-net"></a>wdrożenie platformy .NET

Implementacja platformy .NET obejmuje:

- Co najmniej jeden środowiska uruchomieniowe. Przykłady: CLR, CoreCLR, CoreRT.
- Biblioteka klas, która implementuje wersję standardu .NET i może zawierać dodatkowe interfejsy API. Przykłady: biblioteka klas podstawowych programu .NET Framework, biblioteka klas podstawowych .NET Core.
- Opcjonalnie co najmniej jedna struktura aplikacji. Przykłady: ASP.NET, Windows Forms i WPF są uwzględnione w programie .NET Framework.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Przykłady implementacji platformy .NET:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Platforma uniwersalna systemu Windows (UWP)](#uwp)

## <a name="library"></a>biblioteka

Kolekcja interfejsów API, które mogą być wywoływane przez aplikacje lub inne biblioteki. Biblioteka .NET składa się z jednego lub kilku [zestawów](#assembly).

Słowa biblioteka i [ramy](#framework) są często używane synonimicznie.

## <a name="metapackage"></a>Metapakiet

Pakiet NuGet, który nie ma własnej biblioteki, ale jest tylko listą zależności. Dołączone pakiety można opcjonalnie ustanowić interfejsu API dla struktury docelowej.

Zobacz [pakiety, metapakiety i struktury](../core/packages.md)

## <a name="mono"></a>Mono

Mono jest open source, [wieloplatformowej](#cross-platform) implementacji .NET, który jest używany głównie, gdy wymagane jest małe środowisko uruchomieniowe. Jest to środowisko wykonawcze, które zasila aplikacje platformy Xamarin na systemach Android, Mac, iOS, tvOS i watchOS i koncentruje się głównie na aplikacjach, które wymagają niewielkiego footprintu.

Obsługuje wszystkie aktualnie opublikowane wersje .NET Standard.

W przeszłości Mono implementował większy interfejs API programu .NET Framework i emulował niektóre z najbardziej popularnych funkcji uniksu. Czasami jest używany do uruchamiania aplikacji platformy .NET, które opierają się na tych możliwościach w uniksie.

Mono jest zwykle używany z kompilatorem just-in-time, ale posiada również kompilator statyczny (kompilacja przed czasem), który jest używany na platformach takich jak iOS.

Aby dowiedzieć się więcej o mono, zobacz [dokumentację mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Termin parasolowy dla [platformy .NET Standard](#net-standard) i wszystkich implementacji i obciążeń [platformy .NET.](#implementation-of-net) Zawsze w pełni skapitalizowane, nigdy ".Net".

Zobacz [przewodnik po sieci .NET](index.md)

## <a name="net-core"></a>.NET Core

Wieloplatformowa, wydajna implementacja open source platformy .NET. Zawiera core common language runtime (CoreCLR), Core AOT Runtime (CoreRT, w rozwoju), podstawową bibliotekę klas podstawowych i core SDK.

Zobacz [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>Interfejs wiersza polecenia platformy .NET Core

Wieloplatformowy toolchain do tworzenia aplikacji .NET Core.

Zobacz [.NET Core CLI](../core/tools/index.md).

## <a name="net-core-sdk"></a>Zestaw .NET Core SDK

Zestaw bibliotek i narzędzi, które umożliwiają deweloperom tworzenie aplikacji i bibliotek .NET Core. Zawiera [plik .NET Core CLI](#net-core-cli) do tworzenia aplikacji, biblioteki .NET Core i środowisko wykonawcze do tworzenia i uruchamiania aplikacji oraz plik wykonywalny dotnet *(dotnet.exe),* który uruchamia polecenia interfejsu wiersza polecenia i uruchamia aplikacje.

Zobacz [.NET Core SDK Omówienie](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implementacja platformy .NET, która działa tylko w systemie Windows. Zawiera wspólny czas wykonywania języka (CLR), biblioteki klas podstawowych i bibliotek framework aplikacji, takich jak ASP.NET, Windows Forms i WPF.

Zobacz [.NET Framework Guide](../framework/index.yml).

## <a name="net-native"></a>Architektura .NET Native

Łańcuch narzędzi kompilatora, który tworzy kod macierzysty z wyprzedzeniem (AOT), w przeciwieństwie do just-in-time (JIT).

Kompilacja odbywa się na komputerze dewelopera podobne do sposobu pracy kompilatora języka C++ i konsolidatora. Usuwa nieużyny kod i spędza więcej czasu na jego optymalizacji. Wyodrębnia kod z bibliotek i scala je z plikiem wykonywalnym. Wynikiem jest pojedynczy moduł, który reprezentuje całą aplikację.

Platformy uniwersalnej systemu wizowego był pierwszym framework aplikacji obsługiwanych przez .NET Native. Teraz obsługujemy tworzenie natywnych aplikacji konsoli dla systemów Windows, macOS i Linux.

Zobacz [Wprowadzenie do platformy .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Formalna specyfikacja interfejsów API platformy .NET, które są dostępne w każdej implementacji platformy .NET.

Specyfikacja standardu .NET jest czasami nazywana biblioteką w dokumentacji. Ponieważ biblioteka zawiera implementacje interfejsu API, nie tylko specyfikacje (interfejsy), jest mylące, aby wywołać .NET Standard "biblioteki". Planujemy wyeliminować to użycie z dokumentacji, z wyjątkiem nazwy metapakiety`NETStandard.Library`.NET Standard ( ).

Zobacz [.NET Standard](net-standard.md).

## <a name="ngen"></a>Ngen

Generowanie natywne (obraz).

Tę technologię można potraktować jako trwały kompilator JIT. Zwykle kompiluje kod na komputerze, na którym wykonywany jest kod, ale kompilacja zazwyczaj występuje w czasie instalacji.

## <a name="package"></a>Pakiet

Pakiet &mdash; NuGet lub po &mdash; prostu pakiet jest plikiem *zip* z co najmniej jednym zestawem o tej samej nazwie wraz z dodatkowymi metadanymi, takimi jak nazwa autora.

Plik *zip* ma rozszerzenie *.nupkg* i może zawierać zasoby, takie jak pliki *dll* i pliki *xml,* do użytku z wieloma strukturami docelowymi i wersjami. Po zainstalowaniu w aplikacji lub bibliotece odpowiednie zasoby są wybierane na podstawie struktury docelowej określonej przez aplikację lub bibliotekę. Zasoby definiujące interfejs znajdują się w folderze *ref,* a zasoby definiujące implementację znajdują się w folderze *lib.*

## <a name="platform"></a>platforma

System operacyjny i sprzęt, na który działa, takich jak Windows, macOS, Linux, iOS i Android.

Oto przykłady użycia w zdaniach:

- Program ".NET Core jest wieloplatformową implementacją platformy .NET."
- "Profile PCL reprezentują platformy firmy Microsoft, podczas gdy standard .NET jest niezależny od platformy."

Dokumentacja platformy .NET często używa platformy ".NET" oznacza implementację stosu .NET lub stosu .NET, w tym wszystkie implementacje. Oba te użycia mają tendencję do mylić z podstawowym (OS / hardware) znaczenie, więc planujemy wyeliminować te użycia z dokumentacji.

## <a name="runtime"></a>środowisko uruchomieniowe

Środowisko wykonywania dla programu zarządzanego.

System operacyjny jest częścią środowiska wykonawczego, ale nie jest częścią środowiska uruchomieniowego .NET. Oto kilka przykładów środowiska uruchomieniowego platformy .NET:

- Środowisko uruchomieniowe języka wspólnego (CLR)
- Podstawowy wspólny język runtime (CoreCLR)
- Natywny platformy .NET (dla platformy uniwersalnej systemu sieciowych)
- Mono środowisko wykonawcze

Dokumentacja platformy .NET czasami używa "środowiska uruchomieniowego" oznacza implementację platformy .NET. Na przykład w następujących zdaniach "środowisko uruchomieniowe" należy zastąpić wyrazem "implementacja":

- "Różne środowiska wykonawcze platformy .NET implementują określone wersje programu .NET Standard."
- "Biblioteki, które są przeznaczone do uruchamiania w wielu środowiskach uruchomieniowych należy kierować tej struktury." (odnosząc się do standardu .NET)
- "Różne środowiska wykonawcze platformy .NET implementują określone wersje programu .NET Standard. … Każda wersja środowiska uruchomieniowego .NET anonsuje najwyższą wersję .NET Standard, która obsługuje ..."

Planujemy wyeliminować to niespójne użycie.

## <a name="stack"></a>stack

Zestaw technologii programowania, które są używane razem do tworzenia i uruchamiania aplikacji.

"Stos .NET" odnosi się do standardu .NET i wszystkich implementacji platformy .NET. Wyrażenie "stos .NET" może odnosić się do jednej implementacji .NET.

## <a name="target-framework"></a>ramy docelowe

Kolekcja interfejsów API, na których opiera się aplikacja lub biblioteka .NET.

Aplikacja lub biblioteka może kierować wersję programu .NET Standard (na przykład .NET Standard 2.0), która jest specyfikacją dla standardowego zestawu interfejsów API we wszystkich implementacjach platformy .NET. Aplikacja lub biblioteka może również kierować wersję określonej implementacji platformy .NET, w którym to przypadku uzyskuje dostęp do interfejsów API specyficznych dla implementacji. Na przykład aplikacja, która jest przeznaczona dla platformy Xamarin.iOS pobiera dostęp do otoki interfejsu API systemu iOS dostarczone przez platformę Xamarin.

W przypadku niektórych platform docelowych (na przykład programu .NET Framework) dostępne interfejsy API są definiowane przez zestawy instalowane przez implementację platformy .NET w systemie, które mogą obejmować interfejsy API struktury aplikacji (na przykład ASP.NET, WinForms). W przypadku platform docelowych opartych na pakiecie (takich jak .NET Standard i .NET Core) interfejsy API struktury są definiowane przez pakiety zainstalowane w aplikacji lub bibliotece. W takim przypadku struktura docelowa niejawnie określa metapakiet, który odwołuje się do wszystkich pakietów, które razem tworzą strukturę.

Zobacz [Struktury docelowe](frameworks.md).

## <a name="tfm"></a>Tfm

Moniker struktury docelowej.

Standardowy format tokenu do określania struktury docelowej aplikacji lub biblioteki .NET. Struktury docelowe są zazwyczaj odwołuje się do `net462`krótkiej nazwy, takich jak . TFM o długiej formie (np. NETFramework,Version=4.6.2) istnieją, ale nie są zazwyczaj używane do określania struktury docelowej.

Zobacz [Struktury docelowe](frameworks.md).

## <a name="uwp"></a>Platforma UWP

Uniwersalna platforma Windows.

Implementacja platformy .NET, która służy do tworzenia nowoczesnych aplikacji i oprogramowania systemu Windows z obsługą dotykową dla Internetu rzeczy (IoT). Został zaprojektowany w celu ujednolicenia różnych typów urządzeń, na które możesz chcieć kierować reklamy, w tym komputerów, tabletów, telefonów, a nawet konsoli Xbox. Platformy uniwersalnej systemu Windows udostępnia wiele usług, takich jak scentralizowany sklep z aplikacjami, środowisko wykonywania (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT). Aplikacje mogą być zapisywane w językach C++, C#, Visual Basic i JavaScript. Podczas korzystania z języka C# i Visual Basic interfejsy API platformy .NET są dostarczane przez program .NET Core.

## <a name="see-also"></a>Zobacz też

- [Przewodnik po sieci .NET](index.md)
- [.NET framework — przewodnik](../framework/index.yml)
- [.NET Core](../core/index.md)
- [ASP.NET Przegląd](/aspnet/index#pivot=aspnet)
- [ASP.NET rdzeń](/aspnet/index#pivot=core)
