---
title: Środowisko uruchomieniowe języka wspólnego (CLR)
ms.custom: updateeachrelease
ms.date: 04/16/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7887c1142b721249526a318257149e419affd967
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="common-language-runtime-clr-overview"></a>Typowe Omówienie środowiska uruchomieniowego języka wspólnego (CLR)

.NET Framework zapewnia środowisko czasu wykonywania o nazwie środowisko uruchomieniowe języka wspólnego, która uruchamia kod i udostępnia usługi, które ułatwia proces tworzenia.

Kompilatory narzędzia udostępniać funkcje środowisko uruchomieniowe języka wspólnego firmy i umożliwiają napisać kod tego korzyści z tym zarządzanego środowiska wykonawczego. Kod, który opracowywania kompilatora języka, przeznaczonego dla środowiska uruchomieniowego jest nazywany kod zarządzany; korzysta z funkcji takich jak integracja wielu języków, obsługa wielu języków wyjątków, zwiększone zabezpieczenia, przechowywanie wersji i wdrożenia obsługuje, uproszczony model interakcja składników i debugowanie i profilowania usług.

> [!NOTE]
> Kompilatory i narzędzia są możliwe do generowania danych wyjściowych, który może wykorzystać środowisko uruchomieniowe języka wspólnego, ponieważ system typów, format metadanych i środowiska uruchomieniowego (systemu wirtualnego wykonywania) są definiowane przez publiczny standard języka wspólnego ECMA Specyfikacja infrastruktury. Aby uzyskać więcej informacji, zobacz [ECMA C# i wspólnych specyfikacji infrastruktury języka](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Aby włączyć środowisko uruchomieniowe do świadczenia usług do kodu zarządzanego, Kompilatory języka musi wysyłać metadanych, które opisują typy elementów członkowskich i odwołań w kodzie. Metadane są przechowywane z kodem; co obciążana wspólnego języka środowiska uruchomieniowego przenośnego (PE) pliku wykonywalnego zawiera metadanych. Środowisko uruchomieniowe używa metadanych do zlokalizować i załadować klasy, układ wystąpień w pamięci, rozwiązać wywołania metody, wygenerować kodu natywnego, wymuszanie zabezpieczeń i określają granice kontekstu środowiska wykonawczego.

Środowisko uruchomieniowe obsługuje układ obiektu i automatycznie zarządza odwołania do obiektów, zwalniając je, gdy są one już używane. Obiekty, których okresy istnienia są zarządzane w ten sposób są nazywane danych zarządzanych. Wyrzucanie elementów bezużytecznych eliminuje przecieki pamięci, a także innych typowych błędów programowania. Jeśli kod jest zarządzana, można użyć danych zarządzanych niezarządzanych danych i dane zarządzane i niezarządzane w aplikacji .NET Framework. Ponieważ Kompilatory języka Podaj własnych typów, takich jak typy pierwotne, użytkownik może nie zawsze wiedzieć (lub trzeba znać) czy zarządzania danymi.

Środowisko uruchomieniowe języka wspólnego ułatwia składniki projektu i aplikacji, w których obiekty interakcji w językach. Obiekty napisane w różnych językach może komunikować się ze sobą i ich zachowania mogą być ściśle zintegrowane. Na przykład można zdefiniować klasę, a następnie użyć innego języka wyprowadzenia klasy z oryginalnej klasy lub wywołanie metody w klasie oryginalnego. Wystąpienie klasy można również przekazać do metody klasy napisane w różnych językach. Integracja między językami jest możliwa, ponieważ Kompilatory języka i narzędzia, których miejscem docelowym jest środowisko uruchomieniowe przy użyciu wspólny system typów zdefiniowanych w czasie wykonywania, a zasady środowiska uruchomieniowego do definiowania nowych typów, a także do tworzenia, za pomocą, przechowywanie, postępuj zgodnie z ich i powiązanie z typów.

W ramach ich metadanych wszystkie składniki zarządzane przenoszenia informacji na temat składników i zasoby, które zostały one utworzono przy użyciu. Środowisko uruchomieniowe używa tych informacji, aby upewnić się, że Twoje składnik lub pojedyncza aplikacja ma określony wersje wszystkich elementów, które są niezbędne, dzięki czemu mniej prawdopodobne podziału z powodu niektóre unmet zależności kodu. Danych informacji i stanu rejestracji nie są przechowywane w rejestrze, gdzie mogą być trudne do ustalenia i obsługa. Zamiast tego informacji na temat typów, które należy zdefiniować (oraz ich zależności) znajduje się kod jak metadanych, co znacznie mniej skomplikowanych zadań składnika replikacji i usuwania.

Kompilatory języka i narzędzia ujawniać funkcjonalność aparatu plików wykonywalnych w sposób, w którym mają być przydatne i intuicyjne dla deweloperów. Oznacza to, że niektóre funkcje środowiska uruchomieniowego może być bardziej zauważalne w jednym środowisku niż w innym. Jak wystąpić środowiska uruchomieniowego zależy od tego, które Kompilatory języka lub narzędzia można użyć. Na przykład jeśli jesteś deweloperem Visual Basic, można zauważyć z wykonywalnych języka wspólnego języka Visual Basic ma więcej zorientowane obiektowo funkcji niż przed. Środowisko uruchomieniowe zapewnia następujące korzyści:

- Ulepszenia wydajności.

- Możliwość używania łatwo składniki opracowane w innych językach.

- Typy Extensible pochodzącymi z biblioteki klas.

- Funkcje języka dziedziczenia, interfejsów i przeciążanie programowanie zorientowane obiektowo.

- Obsługa jawne wolnych wątków umożliwiający tworzenie aplikacji wielowątkowych i skalowalności.

- Obsługa wyjątków strukturalnych.

- Obsługa niestandardowych atrybutów.

- Wyrzucanie elementów bezużytecznych.

- Na użytek delegatów zamiast wskaźników funkcji typu zwiększenie bezpieczeństwa i zabezpieczeń. Aby uzyskać więcej informacji na temat delegatów, zobacz [Wspólny System typów](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Wersji środowiska CLR

Numer wersji platformy .NET niekoniecznie nie odpowiada numer wersji środowiska CLR zawiera. W poniższej tabeli przedstawiono, jak skorelowania numery dwóch wersji.

|Wersja programu .NET Framework|Zawiera wersję środowiska CLR|
|----------------------------|--------------------------|
|1.0|1.0|
|1.1|1.1|
|2.0|2.0|
|3.0|2.0|
|3.5|2.0|
|4|4|
|4.5 (w tym 4.5.1 i 4.5.2)|4|
|4.6 (w tym 4.6.1 i 4.6.2)|4|
|4.7 (w tym 4.7.1 i 4.7.2)|4|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Proces zarządzanego wykonania](managed-execution-process.md)|W tym artykule opisano kroki wymagane do wykorzystać środowisko uruchomieniowe języka wspólnego.|
|[Automatyczne zarządzanie pamięcią](automatic-memory-management.md)|W tym artykule opisano, jak moduł garbage collector przydziela i zwalnia pamięć.|
|[Omówienie programu .NET Framework](../framework/get-started/overview.md)|W tym artykule opisano podstawowe pojęcia .NET Framework, takich jak wspólny system typów, współdziałanie między językami, wykonania kodu zarządzanego, domeny aplikacji i zestawów.|
|[System typu wspólnego](./base-types/common-type-system.md)|Opisuje sposób typy są zadeklarowane, używane i zarządzane w środowisku wykonawczym wesprzeć integracja wielu języków.|

## <a name="see-also"></a>Zobacz także

[Wersje i zależności](../framework/migration-guide/versions-and-dependencies.md)
