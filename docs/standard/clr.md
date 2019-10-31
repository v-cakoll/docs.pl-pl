---
title: Omówienie środowiska uruchomieniowego języka wspólnego (CLR) — .NET Framework
ms.date: 04/02/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
ms.custom: updateeachrelease
ms.openlocfilehash: c866e3d1a4de31361843f5c071510fd18247cb39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132812"
---
# <a name="common-language-runtime-clr-overview"></a>Środowisko uruchomieniowe języka wspólnego (CLR) — Omówienie

.NET Framework zapewnia środowisko uruchomieniowe o nazwie środowisko uruchomieniowe języka wspólnego, które uruchamia kod i udostępnia usługi, które ułatwiają proces tworzenia aplikacji.

Kompilatory i narzędzia udostępniają funkcjonalność środowiska uruchomieniowego języka wspólnego i umożliwiają pisanie kodu, który korzysta z tego środowiska wykonywania zarządzanego. Kod opracowywany przy użyciu kompilatora języka, który jest przeznaczony dla środowiska uruchomieniowego, jest nazywany kodem zarządzanym; korzyści płynące z takich funkcji, jak integracja między językami, obsługa wyjątków między językami, ulepszone zabezpieczenia, obsługa wersji i wdrażanie, uproszczony model interakcji ze składnikami oraz funkcje debugowania i profilowania.

> [!NOTE]
> Kompilatory i narzędzia umożliwiają tworzenie danych wyjściowych, które mogą być zużywane przez środowisko uruchomieniowe języka wspólnego, ponieważ system typów, format metadanych i środowisko uruchomieniowe (wirtualny system wykonywania) są zdefiniowane przez Standard publiczny, w języku ECMA Common Specyfikacja infrastruktury. Aby uzyskać więcej informacji, [Zobacz C# specyfikacje ECMA i Common Language Infrastructure](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Aby umożliwić środowisko uruchomieniowe dostarczania usług do kodu zarządzanego, kompilatory języka muszą emitować metadane opisujące typy, elementy członkowskie i odwołania w kodzie. Metadane są przechowywane w kodzie; Każdy załadowany plik wykonywalny (PE) środowiska uruchomieniowego CLR zawiera metadane. Środowisko uruchomieniowe używa metadanych do lokalizowania i ładowania klas, układania wystąpień w pamięci, rozwiązywania wywołań metod, generowania kodu natywnego, wymuszania zabezpieczeń i ustawiania granic kontekstu czasu wykonywania.

Środowisko wykonawcze automatycznie obsługuje układ obiektu i zarządza odwołaniami do obiektów, zwalniając je, gdy nie są już używane. Obiekty, których okresy istnienia są zarządzane w ten sposób, są nazywane danymi zarządzanymi. Wyrzucanie elementów bezużytecznych eliminuje przecieki pamięci, a także inne typowe błędy programistyczne. Jeśli Twój kod jest zarządzany, możesz użyć danych zarządzanych, danych niezarządzanych lub zarówno danych zarządzanych, jak i niezarządzanych w aplikacji .NET Framework. Ponieważ kompilatory języka dostarczają własne typy, takie jak typy pierwotne, może nie zawsze znać (lub koniecznie wiedzieć), czy Twoje dane są zarządzane.

Środowisko uruchomieniowe języka wspólnego ułatwia projektowanie składników i aplikacji, których obiekty współdziałają w różnych językach. Obiekty wpisywane w różnych językach mogą komunikować się ze sobą, a ich zachowania mogą być ściśle zintegrowane. Na przykład można zdefiniować klasę, a następnie użyć innego języka do uzyskania klasy z oryginalnej klasy lub wywołać metodę w klasie oryginalnej. Można również przekazać wystąpienie klasy do metody klasy, która jest zapisywana w innym języku. Ta integracja między językami jest możliwa, ponieważ kompilatory i Narzędzia językowe przeznaczone dla środowiska uruchomieniowego korzystają ze wspólnego systemu typów zdefiniowanego przez środowisko uruchomieniowe i stosują reguły środowiska uruchomieniowego do definiowania nowych typów, a także do tworzenia, używania, utrwalania i powiązanie z typami.

W ramach swoich metadanych wszystkie składniki zarządzane zawierają informacje o składnikach i zasobach, z których zostały zbudowane. Środowisko uruchomieniowe korzysta z tych informacji, aby upewnić się, że składnik lub aplikacja mają określone wersje wszystkich potrzeb, co sprawia, że kod może być nieprzerwany z powodu pewnej zależności niewypełnienia. Informacje o rejestracji i dane o stanie nie są już przechowywane w rejestrze, gdzie mogą być trudne do ustanowienia i utrzymania. Zamiast tego informacje o typach, które definiujesz (wraz z ich zależnościami), są przechowywane w kodzie jako metadane, co sprawia, że zadania związane z replikacją i usuwaniem składników są znacznie mniej skomplikowane.

Kompilatory i narzędzia języka udostępniają funkcjonalność środowiska uruchomieniowego w sposób, który ma być przydatny i intuicyjny dla deweloperów. Oznacza to, że niektóre funkcje środowiska uruchomieniowego mogą być bardziej zauważalne w jednym środowisku niż w innym. Sposób działania środowiska uruchomieniowego zależy od tego, jakiego kompilatora języka lub jakich narzędzi używasz. Na przykład jeśli jesteś deweloperem Visual Basic, możesz zauważyć, że w środowisku uruchomieniowym języka wspólnego język Visual Basic ma więcej funkcji zorientowanych obiektowo niż wcześniej. Środowisko uruchomieniowe zapewnia następujące korzyści:

- Usprawnienia wydajności.

- Możliwość łatwego korzystania ze składników utworzonych w innych językach.

- Rozszerzalne typy udostępniane przez bibliotekę klas.

- Funkcje języka, takie jak dziedziczenie, interfejsy i przeciążanie dla programowania zorientowanego obiektowo.

- Obsługa jawnej bezpłatnej wielowątkowości, która umożliwia tworzenie aplikacji wielowątkowych i skalowalnych.

- Obsługa wyjątków strukturalnych.

- Obsługa atrybutów niestandardowych.

- Odzyskiwanie pamięci.

- Użycie delegatów zamiast wskaźników funkcji w celu zwiększenia bezpieczeństwa typu i bezpieczeństwa. Aby uzyskać więcej informacji na temat delegatów, zobacz [Common Type System](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Wersje środowiska CLR

Numer wersji .NET Framework nie musi odpowiadać numerowi wersji środowiska CLR, który zawiera. W poniższej tabeli przedstawiono sposób skorelowania dwóch numerów wersji:

|Wersja programu .NET Framework|Zawiera wersję środowiska CLR|
|----------------------------|--------------------------|
|1.0|1.0|
|1.1|1.1|
|2.0|2.0|
|3.0|2.0|
|3.5|2.0|
|4|4|
|4,5 (w tym 4.5.1 i 4.5.2)|4|
|4,6 (w tym 4.6.1 i 4.6.2)|4|
|4,7 (w tym 4.7.1 i 4.7.2)|4|
|4,8|4|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Proces zarządzanego wykonania](managed-execution-process.md)|Opisuje kroki wymagane do skorzystania z środowiska uruchomieniowego języka wspólnego.|
|[Automatyczne zarządzanie pamięcią](automatic-memory-management.md)|Opisuje, jak moduł wyrzucania elementów bezużytecznych przydziela i zwalnia pamięć.|
|[Przegląd .NET Framework](../framework/get-started/overview.md)|Opisuje kluczowe pojęcia .NET Framework, takie jak wspólny system typów, współdziałanie między językami, wykonywanie zarządzane, domeny aplikacji i zestawy.|
|[System typu wspólnego](./base-types/common-type-system.md)|Opisuje, w jaki sposób typy są zadeklarowane, używane i zarządzane w środowisku uruchomieniowym w celu obsługi integracji wielu języków.|

## <a name="see-also"></a>Zobacz także

- [Wersje i zależności](../framework/migration-guide/versions-and-dependencies.md)
