---
title: Omówienie usługi Common Language Runtime (CLR) — .NET Framework
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
author: rpetrusha
ms.author: ronpet
ms.custom: updateeachrelease
ms.openlocfilehash: a1e1fd2b7843299fdd8fbd62dbfba6c62a7be50f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645009"
---
# <a name="common-language-runtime-clr-overview"></a>Omówienie usługi Common Language Runtime (CLR)

.NET Framework zapewnia środowisko czasu wykonywania o nazwie środowisko uruchomieniowe języka wspólnego, która uruchamia kod i dostarcza usług, które ułatwiają proces programowania łatwiejsze.

Kompilatory i narzędzia ujawniać funkcjonalność wykonywalnych języka wspólnego i umożliwiają pisanie kodu w tej korzyści z tego środowiska wykonania kodu zarządzanego. Kod opracowany przy użyciu kompilatora języka przeznaczonego dla środowiska wykonawczego jest nazywany kodem zarządzanym; firma korzysta z zalet funkcji takich jak integracja wielu języków, wielu języków, obsługa wyjątków, zwiększone zabezpieczenia, przechowywanie wersji i wdrażania Obsługa, uproszczony model interakcji ze składnikami oraz usługi debugowania i profilowania.

> [!NOTE]
> Kompilatory i narzędzia mają możliwość generowania danych wyjściowych, który może wykorzystywać środowisko uruchomieniowe języka wspólnego, ponieważ system typów, format metadanych i środowiska wykonawczego (wirtualny system wykonywania) są definiowane przez publiczny standard ECMA języka wspólnego Specyfikacja infrastruktury. Aby uzyskać więcej informacji, zobacz [ECMA C# i wspólnych specyfikacji infrastruktury języka](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Aby włączyć środowisko wykonawcze zapewniające usługi kodu zarządzanego, Kompilatory języka muszą emitować metadane opisujące typy, członków i odwołania w kodzie. Metadane są przechowywane z kodem; Każdy obciążana wspólnego języka środowiska uruchomieniowego przenośny plik wykonywalny (PE) zawiera metadane. Aby zlokalizować i ładowania klas, układania wystąpień w pamięci, rozwiązywania wywołań metod, generowania kodu macierzystego, wymuszania zabezpieczeń i granic kontekstowych środowiska wykonawczego Ustaw środowisko wykonawcze używa metadanych.

Środowisko wykonawcze automatycznie obsługuje układ obiektu i zarządza odwołaniami do obiektów, zwalniając je, gdy są one już używane. Obiekty, których okresy istnienia są zarządzane w ten sposób są nazywane zarządzanymi danymi. Wyrzucanie elementów bezużytecznych eliminuje przecieki pamięci, a także niektóre inne typowe błędy programowania. Jeśli Twój kod jest zarządzany, można użyć danych zarządzanych, niezarządzanych danych lub zarządzanych i niezarządzanych danych w aplikacji .NET Framework. Ponieważ Kompilatory języka dostarczają własne typy, takie jak typy pierwotne, użytkownik może nie zawsze wiedzieć (lub trzeba znać) czy zarządzania danymi.

Środowisko uruchomieniowe języka wspólnego ułatwia projektowanie składników i aplikacji, w których obiekty są uruchamiane w różnych językach. Obiekty napisane w różnych językach mogą komunikować się ze sobą, a ich zachowania mogą być ściśle zintegrowane. Na przykład można zdefiniować klasę i następnie użyć innego języka do wyprowadzenia klasy z oryginalnej klasy lub do wywołania metody wobec klasy oryginalnej. Wystąpienie klasy można również przekazać do metody, klasy w innym języku. Ta integracja wielu języków jest możliwe, ponieważ Kompilatory języka i narzędzia, które są przeznaczone dla środowiska uruchomieniowego Użyj wspólny system typów zdefiniowanych przez środowisko uruchomieniowe programu i stosują zasady wykonywania Definiowanie nowych typów, a także do tworzenia, za pomocą, przechowywanie, i powiązanie z typami.

Jako część dla swoich metadanych wszystkie składniki zarządzane posiadają informacje dotyczące składników i zasobów, które zostały zbudowane. Środowisko wykonawcze używa tych informacji, aby upewnić się, że składnik lub aplikacja posiadała określone wersje wszystkiego, czego potrzebuje, co sprawia, że z powodu niewypełnienia zależności jest prawdopodobieństwo złamania kodu. Rejestracja informacje i dane dotyczące stanu nie jest już są przechowywane w rejestrze, w którym może być trudne do ustanawiania i obsługa. Zamiast tego informacje dotyczące typów, które należy zdefiniować (i ich zależności) są przechowywane z kodem jako metadane, co znacznie zmniejsza komplikację zadań replikacji i usuwania składników.

Narzędzia i Kompilatory języka ujawniać funkcjonalność środowiska wykonawczego w sposoby, które mają być przydatne i intuicyjne dla deweloperów. Oznacza to, że niektóre funkcje środowiska uruchomieniowego, może być bardziej zauważalne w jednym środowisku niż w innej. Sposób pracy w środowisku wykonawczym zależy od tego, których kompilatorów języka lub narzędzi używasz. Na przykład jeśli jesteś deweloperem języka Visual Basic, można zauważyć, że plików wykonywalnych języka wspólnego, języka Visual Basic ma więcej funkcji zorientowanych obiektowo niż przed. Środowisko wykonawcze zapewnia następujące korzyści:

- Usprawnienia wydajności.

- Możliwość łatwego używania składników zaprojektowanych w innych językach.

- Typy rozszerzalne dostarczone przez bibliotekę klas.

- Funkcje językowe, takie jak dziedziczenie, interfejsy i przeciążanie dla programowania obiektowego.

- Obsługa jawnie wolnych wątków, która umożliwia tworzenie aplikacji wielowątkowych i skalowalnych.

- Obsługa wyjątków strukturalnych.

- Obsługa atrybutów niestandardowych.

- Wyrzucanie elementów bezużytecznych.

- Użyj obiektów delegowanych zamiast wskaźników funkcji zwiększone bezpieczeństwo typu i zabezpieczeń. Aby uzyskać więcej informacji na temat obiektów delegowanych, zobacz [Wspólny System typów](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Wersje środowiska CLR

Numer wersji systemu .NET Framework nie musi koniecznie odpowiadać numerowi wersji CLR, którą zawiera. W poniższej tabeli przedstawiono, jak skorelowane są numery dwóch wersji:

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
|4.8|4|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Proces zarządzanego wykonania](managed-execution-process.md)|W tym artykule opisano kroki wymagane do zalet środowiska uruchomieniowego języka wspólnego.|
|[Automatyczne zarządzanie pamięcią](automatic-memory-management.md)|W tym artykule opisano, jak moduł odśmiecania pamięci przydziela i zwalnia pamięć.|
|[Omówienie programu .NET Framework](../framework/get-started/overview.md)|W tym artykule opisano kluczowe pojęcia .NET Framework, takich jak wspólny system typów, współdziałanie między językami, wykonania kodu zarządzanego, domeny aplikacji i zestawy.|
|[System typu wspólnego](./base-types/common-type-system.md)|W tym artykule opisano, jak typy są deklarowane, używane i zarządzane w środowisku uruchomieniowym w odniesieniu do integracji wielu języków.|

## <a name="see-also"></a>Zobacz także

- [Wersje i zależności](../framework/migration-guide/versions-and-dependencies.md)
