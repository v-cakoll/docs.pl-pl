---
title: Omówienie programu Common Language Runtime (CLR) — .NET Framework
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
ms.openlocfilehash: 6f9ad8aafc37039b55ae3bf6eb743e07ad8e2235
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74884413"
---
# <a name="common-language-runtime-clr-overview"></a>Omówienie czasu wykonywania języka wspólnego (CLR)

Program .NET Framework zapewnia środowisko wykonywania o nazwie środowiska uruchomieniowego języka wspólnego, który uruchamia kod i zapewnia usługi, które ułatwiają proces tworzenia.

Kompilatory i narzędzia uwidaczniają funkcjonalność środowiska uruchomieniowego języka wspólnego i umożliwiają pisanie kodu, który korzysta z tego środowiska zarządzanego wykonywania. Kod, który można opracować za pomocą kompilatora języka, który jest przeznaczony dla czasu wykonywania jest nazywany kodem zarządzanym; korzysta z funkcji, takich jak integracja między językami, obsługa wyjątków między językami, zwiększone zabezpieczenia, obsługa wersji i wdrażania, uproszczony model interakcji ze składnikami oraz usługi debugowania i profilowania.

> [!NOTE]
> Kompilatory i narzędzia są w stanie wygenerować dane wyjściowe, które środowisko uruchomieniowe języka wspólnego może zużywać, ponieważ system typów, format metadanych i środowiska wykonawczego (system wykonywania wirtualnego) są zdefiniowane przez standard publiczny, wspólny język ECMA Specyfikacja infrastruktury. Aby uzyskać więcej informacji, zobacz [ECMA C# i Specyfikacje infrastruktury języka wspólnego](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Aby włączyć czas uruchomieniowy do świadczenia usług do kodu zarządzanego, kompilatory języka musi emitować metadane, które opisuje typy, elementy członkowskie i odwołania w kodzie. Metadane są przechowywane z kodem; każdy wczytywalny plik przenośnego pliku wykonywalnego (PE) w czasie wykonywania języka wspólnego zawiera metadane. W czasie wykonywania używa metadanych do lokalizowania i ładowania klas, rozłożyć wystąpienia w pamięci, rozpoznać wywołania metody, wygenerować kod macierzysty, wymusić zabezpieczenia i ustawić granice kontekstu w czasie wykonywania.

Czas wykonywania automatycznie obsługuje układ obiektu i zarządza odwołania do obiektów, zwalniając je, gdy nie są już używane. Obiekty, których okresy istnienia są zarządzane w ten sposób są nazywane danymi zarządzanymi. Wyrzucanie elementów bezużytecznych eliminuje przecieki pamięci, a także niektóre inne typowe błędy programowania. Jeśli kod jest zarządzany, można użyć danych zarządzanych, danych niezarządzanych lub zarówno zarządzanych, jak i niezarządzanych danych w aplikacji .NET Framework. Ponieważ kompilatory języka podać własne typy, takie jak typy pierwotne, nie zawsze wiadomo (lub trzeba wiedzieć), czy dane są zarządzane.

Czas wykonywania języka wspólnego ułatwia projektowanie składników i aplikacji, których obiekty współdziałają między językami. Obiekty napisane w różnych językach mogą komunikować się ze sobą, a ich zachowania mogą być ściśle zintegrowane. Na przykład można zdefiniować klasę, a następnie użyć innego języka, aby wyprowadzić klasę z oryginalnej klasy lub wywołać metodę w oryginalnej klasie. Można również przekazać wystąpienie klasy do metody klasy napisane w innym języku. Ta integracja między językami jest możliwe, ponieważ kompilatory języka i narzędzia, które są przeznaczone dla czasu wykonywania użyć wspólnego systemu typów zdefiniowane przez czas wykonywania i są zgodne z regułami wykonywania do definiowania nowych typów, a także do tworzenia, używania, utrwalania i powiązania z typami.

W ramach swoich metadanych wszystkie zarządzane składniki przenoszą informacje o składnikach i zasobach, przeciwko którym zostały zbudowane. Czas wykonywania używa tych informacji, aby upewnić się, że składnik lub aplikacja ma określone wersje wszystkiego, czego potrzebuje, co sprawia, że kod mniej prawdopodobne, aby przerwać z powodu niektórych niezaspokojone zależności. Informacje rejestracyjne i dane o stanie nie są już przechowywane w rejestrze, w którym mogą być trudne do ustalenia i utrzymania. Zamiast tego informacje o typach, które definiujesz (i ich zależności) są przechowywane z kodem jako metadane, dzięki czemu zadania replikacji składników i usuwania znacznie mniej skomplikowane.

Kompilatory języka i narzędzia uwidaczniają funkcjonalność środowisko uruchomieniowego w sposób, który ma być przydatny i intuicyjny dla deweloperów. Oznacza to, że niektóre funkcje środowiska uruchomieniowego mogą być bardziej zauważalne w jednym środowisku niż w innym. Sposób działania środowiska uruchomieniowego zależy od tego, którego kompilatora języka lub narzędzi używasz. Na przykład jeśli jesteś programistą języka Visual Basic, można zauważyć, że w czasie wykonywania języka wspólnego języka języka języka ma więcej obiektów obiektów niż wcześniej. Czas wykonywania zapewnia następujące korzyści:

- Usprawnienia wydajności.

- Możliwość łatwego korzystania ze składników opracowanych w innych językach.

- Typy rozszerzalne dostarczane przez bibliotekę klas.

- Funkcje języka, takie jak dziedziczenie, interfejsy i przeciążenia dla programowania obiektowego.

- Obsługa jawnego wolnego wątkowania, które umożliwia tworzenie wielowątkowych, skalowalnych aplikacji.

- Obsługa ustrukturyzowanej obsługi wyjątków.

- Obsługa atrybutów niestandardowych.

- Wyrzucanie elementów bezużytecznych.

- Użyj delegatów zamiast wskaźników funkcji dla zwiększenia bezpieczeństwa typu i bezpieczeństwa. Aby uzyskać więcej informacji na temat delegatów, zobacz [System typowego typu](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Wersje CLR

Numer wersji .NET Framework nie musi odpowiadać numer wersji clr zawiera. Aby uzyskać listę wersji programu .NET Framework i odpowiadających im wersji clr, zobacz [.NET Framework wersje i zależności](../framework/migration-guide/versions-and-dependencies.md). Wersje .NET Core mają jedną wersję produktu, oznacza to, że nie ma osobnej wersji CLR. Aby uzyskać listę wersji programu .NET Core, zobacz [Pobieranie programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Proces zarządzanego wykonania](managed-execution-process.md)|Opisuje kroki wymagane do korzystania ze wspólnego języka wykonywania.|
|[Automatyczne zarządzanie pamięcią](automatic-memory-management.md)|Opisuje, jak moduł zbierający elementy bezużyteczne przydziela i zwalnia pamięć.|
|[Przegląd programu .NET Framework](../framework/get-started/overview.md)|W tym artykule opisano pojęcia key .NET Framework, takie jak wspólny system typów, współdziałanie między językami, wykonanie zarządzane, domeny aplikacji i zestawy.|
|[System typu wspólnego](./base-types/common-type-system.md)|Opisuje sposób, w jaki typy są deklarowane, używane i zarządzane w czasie wykonywania na rzecz integracji między językami.|
