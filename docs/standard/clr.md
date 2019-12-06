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
ms.openlocfilehash: 6f9ad8aafc37039b55ae3bf6eb743e07ad8e2235
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884413"
---
# <a name="common-language-runtime-clr-overview"></a>Środowisko uruchomieniowe języka wspólnego (CLR) — Omówienie

Program .NET Framework zapewnia środowisko czasu wykonywania, nazywane środowiskiem uruchomieniowym języka wspólnego, które uruchamia kod i oferuje usługi, które ułatwiają proces programowania.

Kompilatory i narzędzia udostępniają funkcje środowiska uruchomieniowego języka wspólnego i umożliwiają pisanie kodu, który korzysta z tego środowiska wykonywania kodu zarządzanego. Kod opracowany przy użyciu kompilatora języka przeznaczonego dla środowiska wykonawczego jest nazywany kodem zarządzanym; korzysta on z funkcji takich jak integracja wielu języków, obsługa wyjątków w wielu językach, zwiększone zabezpieczenia, obsługa wersjonowania i wdrażania, uproszczony model interakcji ze składnikami oraz usługi debugowania i profilowania.

> [!NOTE]
> Kompilatory i narzędzia mają możliwość generowania danych wyjściowych, które może wykorzystywać środowisko uruchomieniowe języka wspólnego, ponieważ typ systemu, format metadanych i środowisko wykonawczego (wirtualny system wykonywania) są definiowane przez publiczny standard — specyfikację infrastruktury wspólnego języka ECMA. Aby uzyskać więcej informacji, [Zobacz C# specyfikacje ECMA i Common Language Infrastructure](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Aby włączyć środowisko wykonawcze zapewniające usługi kodu zarządzanego, kompilatory języka muszą emitować metadane opisujące typy, członków i odwołania w kodzie. Metadane są przechowywane z kodem; każdy nadający się do ładowania przenośny plik wykonywalny (PE) środowiska uruchomieniowego języka wspólnego zawiera metadane. Środowisko wykonawcze używa metadanych do lokalizowania i ładowania klas, układania wystąpień w pamięci, rozwiązywania wywołań metod, generowania kodu macierzystego, wymuszania zabezpieczeń i ustawiania granic kontekstowych środowiska wykonawczego.

Środowisko wykonawcze automatycznie obsługuje układ obiektu i zarządza odwołaniami do obiektów, zwalniając je, gdy nie są one już używane. Obiekty, których okresy istnienia są zarządzane w ten sposób, są nazywane zarządzanymi danymi. Wyrzucanie elementów bezużytecznych eliminuje przecieki pamięci, jak również inne typowe błędy programowania. Jeśli kod jest zarządzany, można użyć danych zarządzanych, niezarządzanych danych lub obu rodzajów danych w aplikacji środowiska .NET Framework. Ponieważ kompilatory języka dostarczają własne typy, takie jak typy elementów podstawowych, możesz nie zawsze wiedzieć (albo potrzebować wiedzieć), czy Twoje dane są zarządzane.

Środowisko uruchomieniowe języka wspólnego ułatwia projektowanie składników i aplikacji, których obiekty są uruchamiane w różnych językach. Obiekty napisane w różnych językach mogą komunikować się ze sobą, a ich zachowania mogą być ściśle zintegrowane. Na przykład można zdefiniować klasę i następnie użyć innego języka do utworzenia pochodnej klasy z oryginalnej klasy lub do wywołania metody wobec klasy oryginalnej. Wystąpienie klasy można również przekazać do metody klasy w innym języku. Integracja wielu języków jest możliwa, ponieważ programy kompilujące języki i narzędzia przeznaczone do czasu wykonania programu używają systemu typu wspólnego, określonego przez czas wykonania programu i stosują zasady wykonywania, aby zdefiniować nowe typy, a także tworzyć, używać, utrzymywać i wiązać z typami.

Jako część swoich metadanych wszystkie składniki zarządzane posiadają informacje dotyczące składników i zasobów, na bazie których zostały zbudowane. Środowisko wykonawcze używa tych informacji, aby składnik lub aplikacja posiadała określone wersje wszystkiego, czego potrzebuje, co sprawia, że prawdopodobieństwo złamania kodu z powodu niewypełnienia zależności jest mniejsze. Informacje dotyczące rejestracji i dane dotyczące stanu nie są już są przechowywane w rejestrze, która to lokalizacja sprawiała, że trudno było je utworzyć i nimi zarządzać. Zamiast tego informacje dotyczące definiowanych typów (i ich zależności) są przechowywane z kodem jako metadane, co znacznie zmniejsza komplikację zadań replikacji i usuwania składników.

Narzędzia i kompilatory języka udostępniają funkcjonalności środowiska wykonawczego w sposoby, które mają być przydatne i intuicyjne dla deweloperów. Oznacza to, że niektóre funkcje środowiska wykonawczego mogą być bardziej zauważalne w jednym środowisku niż w innym. Sposób pracy w środowisku wykonawczym zależy od tego, których kompilatorów języka lub narzędzi używasz. Na przykład jeśli jesteś deweloperem w środowisku programu Visual Basic, możesz zauważyć, że dzięki środowisku uruchomieniowemu języka wspólnego język Visual Basic ma więcej funkcji zorientowanych obiektowo niż wcześniej. Środowisko wykonawcze zapewnia następujące korzyści:

- Usprawnienia wydajności.

- Możliwość łatwego używania składników zaprojektowanych w innych językach.

- Typy rozszerzalne dostarczone przez bibliotekę klas.

- Funkcje języka, takie jak dziedziczenie, interfejsy i przeciążanie dla programowania obiektowego.

- Obsługa jawnie wolnych wątków, które umożliwiają tworzenie aplikacji wielowątkowych i skalowalnych.

- Obsługa wyjątków strukturalnych.

- Obsługa atrybutów niestandardowych.

- Wyrzucanie elementów bezużytecznych.

- Użyj obiektów delegowanych zamiast wskaźników funkcji, aby zwiększyć zabezpieczenia i ochronę typu. Aby uzyskać więcej informacji na temat delegatów, zobacz [Common Type System](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Wersje środowiska CLR

Numer wersji .NET Framework nie musi odpowiadać numerowi wersji środowiska CLR, który zawiera. Listę wersji .NET Framework i odpowiadających im wersji środowiska CLR można znaleźć w temacie [.NET Framework wersje i zależności](../framework/migration-guide/versions-and-dependencies.md). Wersje .NET Core mają jedną wersję produktu, czyli nie ma oddzielnej wersji środowiska CLR. Aby zapoznać się z listą wersji programu .NET Core, zobacz [pobieranie platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Proces zarządzanego wykonania](managed-execution-process.md)|W tym artykule opisano kroki wymagane do wykorzystania zalet środowiska uruchomieniowego języka wspólnego.|
|[Automatyczne zarządzanie pamięcią](automatic-memory-management.md)|Opisuje, jak program do wyrzucania elementów bezużytecznych przydziela i zwalnia pamięć.|
|[Przegląd .NET Framework](../framework/get-started/overview.md)|Zawiera opis podstawowych pojęć programu .NET Framework, takich jak wspólny system typów, współdziałanie wielu języków, wykonywanie kodu zarządzanego, domeny aplikacji i zestawy.|
|[System typu wspólnego](./base-types/common-type-system.md)|Opisuje, jak typy są deklarowane, używane i zarządzane w środowisku wykonawczym w celu obsługi integracji wielu języków.|
