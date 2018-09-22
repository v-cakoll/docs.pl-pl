---
title: Omówienie programu Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 35eb3b1503c8754752662aef0c5101251d60d49c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584009"
---
# <a name="entity-framework-overview"></a>Omówienie programu Entity Framework

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] To zestaw technologii ADO.NET, które obsługują tworzenie aplikacji zorientowanych na dane. Z potrzebami osiągnięcia dwa cele zbytnio zmagały architektów i deweloperów aplikacji zorientowanych na dane. Modelują one muszą jednostek, relacje i logiki problemy biznesowe, które są ich rozwiązywania, a także muszą współpracować z aparatów danych, używane do przechowywania i pobierania danych. Dane mogą obejmować wiele systemów pamięci masowej, każdy z protokołami; nawet aplikacjach, które działają w systemie pojedynczy magazyn muszą równoważyć wymagania systemu magazynu pod kątem wymagań pisania kodu wydajne i łatwy w obsłudze aplikacji.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia deweloperom pracę z danymi w postaci obiektów specyficznych dla domeny i właściwości, takich jak klienci i adresy klientów bez konieczności zajmowania się w tych tabelach bazy danych i kolumnami, gdzie te dane są przechowywane . Za pomocą [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], deweloperzy mogą pracować na wyższym poziomie abstrakcji, gdy zajmują się danymi i mogą tworzyć i utrzymywać zorientowane na dane aplikacji przy użyciu mniejszej ilości kodu niż w tradycyjnej aplikacji. Ponieważ [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] jest składnikiem [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacje mogą działać na dowolnym komputerze, na którym [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem SP1 jest zainstalowana.

## <a name="give-life-to-models"></a>Ożywić modeli
 Na etapie projektowania od i typowe podczas tworzenia aplikacji lub usługi jest podział aplikacji lub usługi na trzy części: modelu domeny, modelu logicznego i modelu fizycznego. Model domeny definiuje jednostek i relacji w systemie, który jest w modelu. Logiczny model relacyjnej bazy danych normalizuje jednostki i relacje do tabel za pomocą ograniczeń klucza obcego. Modelu fizycznego eliminuje możliwości silnika określone dane, określając szczegóły magazynu, takich jak partycjonowanie i indeksowania.

 Modelu fizycznego jest udoskonalane przez administratorów baz danych, aby zwiększyć wydajność, ale programistom pisanie kodu aplikacji przede wszystkim ograniczają się do pracy z modelu logicznego przez pisanie zapytań SQL i wywoływanie procedur składowanych. Modeli domeny są zazwyczaj używane jako narzędzie do przechwytywania i komunikowania się z wymaganiami aplikacji, często jako to diagramy, które są wyświetlane i opisem na wczesnym etapie projektu, a następnie odrzucone. Wiele zespołów programistycznych pominąć tworzenie modelu koncepcyjnego i Rozpocznij, określając tabel, kolumn i klucze w relacyjnej bazie danych.

 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zapewnia życia z modelami umożliwia deweloperom wykonywanie zapytań dotyczących jednostek i relacji w modelu domeny (o nazwie *koncepcyjny* modelu w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) polegając jednocześnie na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] do translacji te operacje na polecenia specyficzne dla źródła danych. Dzięki temu aplikacje od ustalonych zależności z określonego źródła danych.

 Podczas pracy z Code First, model koncepcyjny jest zamapowana na model magazynu w kodzie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Może wywnioskować na podstawie typów obiektów i dodatkowe konfiguracje, które definiujesz modelu koncepcyjnego. Metadane mapowanie jest generowany w czasie wykonywania, które są oparte na kombinacji sposób definiowania swoje typy domen i informacje dodatkowe czynności konfiguracyjne, które należy podać w kodzie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] generuje bazy danych zgodnie z potrzebami, na podstawie metadanych. Aby uzyskać więcej informacji, zobacz [tworzenia i mapowania modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkID=235382).

 Podczas pracy z narzędziami modelu danych jednostki, modelu koncepcyjnego, model magazynu i mapowania między nimi są wyrażone w schematach opartych na języku XML i zdefiniowane w plikach, które mają odpowiednie rozszerzenia nazw:

-   Język definicji schematu koncepcyjnego (CSDL) definiuje modelu koncepcyjnego. Jest CSDL [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]przez implementację [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md). Rozszerzenie pliku jest .csdl.

-   Język definicji schematu Store (SSDL) definiuje modelu magazynu, który jest również nazywany modelu logicznego. Rozszerzenie pliku jest ssdl.

-   Mapowanie specification language (MSL) definiuje mapowania między magazynu i modeli koncepcyjnych. Rozszerzenie pliku jest MSL albo identyfikatorem.

Model magazynu i mapowania można zmienić zgodnie z potrzebami bez konieczności wprowadzania zmian w modelu koncepcyjnym, klas danych lub kod aplikacji. Ponieważ modeli magazynowania są właściwe dla dostawcy, spójny model koncepcyjny można pracować w różnych źródłach danych.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa tych modelu i mapowania plików do tworzenia, odczytu, aktualizowanie i usuwanie operacji wykonywanych względem jednostek i relacji w modelu koncepcyjnym równoważne operacji w źródle danych. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nawet obsługuje mapowania jednostki w modelu koncepcyjnym procedur przechowywanych w źródle danych. Aby uzyskać więcej informacji, zobacz [CSDL, SSDL i MSL specyfikacji](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Map — obiekty do danych
 Programowanie zorientowane obiektowo stanowi wyzwanie, interakcji z systemów magazynowania danych. Dopasuj organizacji klasy często odzwierciedla organizacji tabel relacyjnej bazy danych, nie jest doskonały. Wiele znormalizowanych tabel często odpowiadają jednej klasy i relacje między klasami są często reprezentowane inaczej, niż są przedstawiane relacje między tabelami. Na przykład do reprezentowania klientów dla zamówienia sprzedaży `Order` użyć właściwości, która zawiera odwołanie do wystąpienia klasy `Customer` klasy, podczas gdy `Order` wiersz tabeli w bazie danych, zawiera kolumny klucza obcego (lub zestaw kolumn) z wartością, która odnosi się do wartości klucza podstawowego w `Customer` tabeli. A `Customer` klasa może mieć właściwość o nazwie `Orders` zawierający kolekcję wystąpień `Order` klasy, podczas gdy `Customer` tabeli w bazie danych nie ma kolumny porównywalny. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Oferuje deweloperom elastyczność do reprezentowania relacji w ten sposób lub dokładniej modelowania relacji, ponieważ są one reprezentowane w bazie danych.

 Podjęto istniejących rozwiązań można wypełnić tę lukę, często nazywanej "niezgodności impedancji", tylko mapowania obiektowo klas i właściwości do relacyjnych tabel i kolumn. Zamiast tego tradycyjne podejście [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mapuje tabelach relacyjnych, kolumn i ograniczeń klucza obcego w modelach logicznych jednostek i relacji w modelach koncepcyjnych. Umożliwia to większą elastyczność zarówno w celu zdefiniowania obiektów i optymalizowanie modelu logicznego. [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Narzędzia Generowanie klas extensible danych opartych na modelu koncepcyjnego. Te klasy są klas częściowych, które mogą zostać rozszerzone o dodatkowe elementy członkowskie, które są dodawane przez dewelopera. Domyślnie klas, które są generowane dla konkretnego modelu koncepcyjnego pochodzi od klasy bazowe, które udostępniają usługi materializowanie jednostki jako obiekty oraz śledzenie i zapisywanie zmian. Deweloperzy mogą używać tych klas do pracy z jednostki i relacje jako obiekty powiązane przez skojarzenia. Deweloperzy będą mogli również dostosować klas, które są generowane dla modelu koncepcyjnego. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Dostęp i zmiany danych jednostki

Więcej niż kolejna rozwiązaniu mapowania obiektowo relacyjny [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] to zasadniczo dotyczące włączania aplikacji dostępu i zmiany danych, która jest reprezentowana jako jednostek i relacji w modelu koncepcyjnym. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa informacji w modelu i mapowania plików do translacji zapytań obiektu dla typów jednostek reprezentowanych w model koncepcyjny do zapytań specyficznych dla źródła danych. Wyniki zapytania są zmaterializowanego w obiektach, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zarządza. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Oferuje następujące sposoby wykonywania zapytań modelu koncepcyjnego i zwracać obiekty:

-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Wykonywanie zapytania dotyczącego typów jednostek, które są zdefiniowane w modelu koncepcyjnym zapewnia obsługę Language-Integrated Query (LINQ). Aby uzyskać więcej informacji, zobacz [składnik LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).

-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialekt niezależny od magazynu, programu SQL Server, który współpracuje bezpośrednio z jednostkami w modelu koncepcyjnym i obsługujący [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] pojęcia. [!INCLUDE[esql](../../../../../includes/esql-md.md)] jest używany zarówno za pomocą zapytań dotyczących obiektów i zapytania, które są wykonywane przy użyciu dostawca EntityClient. Aby uzyskać więcej informacji, zobacz [omówienie jednostki SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje EntityClient dostawcy danych. Ten dostawca zarządza połączeniami przekłada zapytania jednostki na kwerendach specyficznymi dla źródła danych i zwraca wartość czytnik danych [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] używa do zmaterializowania jednostki danych w obiektach. Gdy materializacja obiektu nie jest wymagane, dostawca EntityClient również mogą być używane jak standardowy [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy danych, dzięki czemu aplikacje mogą wykonać [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania i używanie czytnika zwracanych danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

Na poniższym diagramie przedstawiono [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] architektury do uzyskiwania dostępu do danych:

![Diagram architektury programu Entity Framework](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")

[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Narzędzia można wygenerować klasy pochodzącej od `System.Data.Objects.ObjectContext` lub `System.Data.Entity.DbContext` reprezentujący kontener jednostek w modelu koncepcyjnym. Ten kontekst udostępnia funkcje służące do śledzenia zmian i zarządzania tożsamościami, współbieżność i relacje. Ta klasa udostępnia również `SaveChanges` metody zapisującej operacji wstawiania, aktualizuje i usuwa ze źródłem danych. Jak zapytania zmiany te są albo wykonywane za pomocą poleceń automatycznie generowane przez system lub procedur składowanych, które są określone przez dewelopera.

## <a name="data-providers"></a>Dostawcy danych

`EntityClient` Dostawca rozszerza [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] modelu dostawców, uzyskując dostęp do danych pod względem koncepcyjny jednostek i relacji. Wykonuje zapytania, które używają [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] dostarcza podstawowy język zapytań, który umożliwia `EntityClient` do komunikowania się z bazą danych. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera zaktualizowany dostawca danych SqlClient obsługuje drzew poleceń w postaci kanonicznej. Aby uzyskać więcej informacji, zobacz [SqlClient programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Narzędzia modelu danych jednostki

Wraz z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] środowiska uruchomieniowego, Visual Studio zawiera mapowanie i narzędzia do modelowania. Aby uzyskać więcej informacji, zobacz [modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby dowiedzieć się więcej na temat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], zobacz:

[Wprowadzenie do](../../../../../docs/framework/data/adonet/ef/getting-started.md) — zawiera informacje dotyczące sposobów rozpocząć i uruchomiona szybko przy użyciu [Szybki Start](https://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675), który pokazuje, jak utworzyć prostą [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.

[Terminologia programu Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md) — definiuje wiele warunków, które są wprowadzone w modelu Entity Data Model i [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , które są używane w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji.

[Zasoby programu Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md) — zawiera łącza do tematów pojęciowych i linki do tematów zewnętrznych i zasoby do tworzenia [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.

## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)
