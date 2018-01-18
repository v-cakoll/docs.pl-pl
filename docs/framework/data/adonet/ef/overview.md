---
title: "Omówienie struktury jednostek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d8d47b578d60d2c53aaa4b1f47e86430d3495ed1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="entity-framework-overview"></a>Omówienie struktury jednostek
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] To zestaw technologii w ADO.NET, która obsługuje programowanie zorientowane na dane aplikacji. Dla architektów i deweloperów aplikacje zorientowane na dane zmagały z koniecznością osiągnięcia dwóch celów bardzo różnią się. Muszą one modelu jednostki, relacje i logiki problemy biznesowe, które są one rozwiązywania i muszą one również współpracować z aparaty danych używany do przechowywania i pobierania danych. Dane mogą obejmować wiele systemów magazynowania, każdy z protokołami; nawet aplikacji, które działają w systemie pojedynczy magazyn musi równoważenie wymagania systemu magazynu względem wymagań pisania kodu wydajne i łatwy w obsłudze aplikacji.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia deweloperom pracy z danymi w postaci obiektów specyficznego dla domeny i właściwości, takich jak klienci i adresy klientów bez konieczności zajmować się tych tabelach bazy danych i przechowywania danych tej kolumny . Z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], deweloperzy mogą pracować na wyższym poziomie abstrakcji, gdy ich postępowania z danymi i można tworzyć i obsługiwać aplikacje zorientowane na danych z mniejsza ilość kodu niż w tradycyjne aplikacje. Ponieważ [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] wchodzi w skład [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacje mogą działać na dowolnym komputerze, na którym [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem SP1 jest zainstalowana.  
  
 Poniższe sekcje w tym temacie zawierają więcej szczegółów o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   [Nadanie życia do modeli](#LifeToModels)  
  
-   [Mapowania obiektów danych](#MappingObjectsToData)  
  
-   [Uzyskiwanie dostępu i zmienianie danych dotyczących jednostki](#AccessingData)  
  
-   [Dostawcy danych](#DataProviders)  
  
-   [Narzędzi modelu danych jednostki](#Tools)  
  
-   [Dowiedzieć się więcej](#LearnMore)  
  
<a name="LifeToModels"></a>   
## <a name="giving-life-to-models"></a>Nadanie życia do modeli  
 Na etapie projektowania dawna i wspólne podczas tworzenia aplikacji lub usługi jest podział aplikacji lub usługi na trzy części: modelu domeny logicznej modelu i modelu fizycznego. Model domeny definiuje jednostki i relacje w systemie, które są w modelu. Modelu logicznego relacyjnej bazy danych normalizuje jednostki i relacje do tabel z ograniczeń klucza obcego. Modelu fizycznego dotyczy możliwości aparatu danych przez określenie magazynu szczegóły, takie jak partycjonowania i indeksowania.  
  
 Modelu fizycznego jest wprowadzono ulepszenia przez administratorów bazy danych, aby zwiększyć wydajność, ale programistów głównie pisanie kodu aplikacji ograniczają się do pracy z modelu logicznego Pisanie zapytań SQL i wywoływanie procedur składowanych. Modele domeny są zazwyczaj używane jako narzędzia do przechwytywania i wymagania dotyczące aplikacji, często jako pod kątem diagramy, na których są wyświetlane i opisanych na wczesnym etapie projektu i następnie porzucone komunikacji. Wiele zespołów deweloperów pominąć tworzenie modelu koncepcyjnego i rozpocząć, określając tabel, kolumn i klucze w relacyjnej bazie danych.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Powoduje życia modeli umożliwia deweloperom do zapytania jednostki i relacje w modelu domeny (o nazwie *koncepcyjnej* modelu w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) podczas polegania na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] tłumaczenie tych operacje na polecenia specyficzne dla źródła danych. Dzięki temu aplikacje z wpisaną na stałe zależności z określonego źródła danych.  
  
 Podczas pracy z Code First, modelu koncepcyjnego jest mapowana na modelu magazynu w kodzie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Można wywnioskować na podstawie typów obiektów i dodatkowe konfiguracje, które należy zdefiniować modelu koncepcyjnego. Metadane mapowania jest generowane w czasie wykonywania, oparty na kombinacji sposób definiowania typów domeny, a dodatkowe informacje o konfiguracji podane w kodzie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]generuje bazy danych zgodnie z potrzebami, na podstawie metadanych. Aby uzyskać więcej informacji, zobacz [tworzenia i mapowania modelu koncepcyjnego](http://go.microsoft.com/fwlink/?LinkID=235382).  
  
 Podczas pracy z narzędzi modelu danych jednostki, model koncepcyjny modelu magazynu i mapowania między nimi są wyrażone w schematów opartych na języku XML i zdefiniowane w plikach, które mają odpowiednie rozszerzenia nazw:  
  
-   Schematu koncepcyjnego definition language (CSDL) definiuje modelu koncepcyjnego. Plik CSDL jest [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]w implementacji [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md). Rozszerzenie pliku jest .csdl.  
  
-   Język definicji schematu magazynu (SSDL) definiuje modelu magazynu, który jest również nazywany modelu logicznego. Rozszerzenie pliku jest ssdl.  
  
-   Specyfikacja języka mapowania (MSL) definiuje mapowania między magazynem a modelach koncepcyjnych. Rozszerzenie pliku jest .msl.  
  
 Mapowania i modelu magazynu, można zmienić w razie potrzeby bez konieczności wprowadzania zmian w modelu koncepcyjnym, klas danych lub kod aplikacji. Ponieważ Magazyn modeli są właściwe dla dostawcy, możesz pracować z spójny model koncepcyjny między różnymi źródłami danych.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa tych modelu i mapowania plików do tworzenia, odczytu, aktualizacji i usuwania operacji względem jednostki i relacje w modelu koncepcyjnym równoważne operacje wykonywane w źródle danych. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nawet obsługuje mapowania jednostki w modelu koncepcyjnym procedur przechowywanych w źródle danych. Aby uzyskać więcej informacji, zobacz [CSDL, SSDL, MSL specyfikacji i](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).  
  
<a name="MappingObjectsToData"></a>   
## <a name="mapping-objects-to-data"></a>Mapowania obiektów danych  
 Programowanie zorientowane obiektowo stanowi wyzwanie interakcji z systemów magazynowania danych. Dopasuj organizacji klasy odzwierciedla często organizacji tabel relacyjnych baz danych, nie jest idealne. Wiele tabel znormalizowane często odpowiada jednej klasy i relacje między klasami są często reprezentowane inaczej, niż są przedstawiane relacje między tabelami. Na przykład, aby reprezentować klienta zamówienia sprzedaży `Order` użyć właściwości, która zawiera odwołanie do wystąpienia klasy `Customer` klasy, podczas gdy `Order` wiersz tabeli w bazie danych zawiera kolumny klucza obcego (lub zestaw kolumn) z wartością, która odpowiada wartości klucza podstawowego w `Customer` tabeli. A `Customer` klasa może mieć właściwość o nazwie `Orders` zawierający kolekcję wystąpień `Order` klasy, gdy `Customer` tabeli w bazie danych nie ma kolumny można porównywać. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zapewnia deweloperom elastyczność do reprezentowania relacji w ten sposób, lub do dokładniejsze modelowania relacji reprezentowane w bazie danych.  
  
 W istniejących rozwiązaniach próbowano rozbieżność tego, często nazywane "impedancji niezgodność", tylko mapowania zorientowane obiektowo klas i właściwości relacyjne tabel i kolumn. Zamiast przyjmowania to tradycyjne podejście, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mapuje relacyjne tabel, kolumn i ograniczeń klucza obcego w modelach logicznych do jednostki i relacje w modelach koncepcyjnych. Umożliwia to większą elastyczność zarówno w celu zdefiniowania obiektów i optymalizowanie modelu logicznego. [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Narzędzia wygenerowane klasy extensible danych oparte na modelu koncepcyjnego. Te klasy są częściowej klasy, które można rozszerzyć z dodatkowych elementów członkowskich, które dodaje dewelopera. Domyślnie klasy, które są generowane dla określonego modelu koncepcyjnego pochodzić od klasy podstawowe, które udostępniają usługi dla materializowania jednostek jako obiekty i śledzenia i zapisywania zmian. Deweloperzy mogą używać tych klas do pracy z jednostki i relacje jako obiekty powiązane przez skojarzenia. Deweloperzy mogą również dostosowywać klas, które są generowane dla modelu koncepcyjnego. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
<a name="AccessingData"></a>   
## <a name="accessing-and-changing-entity-data"></a>Uzyskiwanie dostępu i zmienianie danych dotyczących jednostki  
 Więcej niż tylko innego rozwiązania mapowania relacyjnego obiektu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] jest zasadniczo o zezwalaniu na aplikacje dostępu i zmiany danych, który jest reprezentowany jako jednostki i relacje w modelu koncepcyjnym. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa informacji w modelu i mapowania plików do przekształcania obiektu zapytań dotyczących typów jednostek reprezentowanych w modelu koncepcyjnym do kwerend specyficzne dla źródła danych. Wyniki zapytania są zmaterializowany na obiekty który [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zarządza. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Oferuje następujące sposoby wykonywania zapytań modelu koncepcyjnego i zwracać obiekty:  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Zapewnia obsługę język Language-Integrated zapytania (LINQ) do wykonywania zapytań typy jednostek, które są zdefiniowane w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialekt niezależne od magazynu programu SQL Server, które współpracuje bezpośrednio z jednostek w modelu koncepcyjnym i obsługującym [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] pojęcia. [!INCLUDE[esql](../../../../../includes/esql-md.md)]jest używany zarówno w kwerendach obiektu i zapytań, które są wykonywane przy użyciu dostawcy EntityClient. Aby uzyskać więcej informacji, zobacz [omówienie SQL jednostki](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje EntityClient dostawcy danych. Ten dostawca zarządza połączeniami przekłada zapytania jednostki na zapytania dotyczące źródła danych i zwraca czytnika danych, która [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] używa do zmaterializowania danych jednostki w obiektach. Gdy materialization obiektu nie jest wymagana, dostawca EntityClient można także jak standard [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy danych, umożliwiając aplikacjom wykonywanie [!INCLUDE[esql](../../../../../includes/esql-md.md)] wysyła kwerendy i korzystać z czytnika zwracanych danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Na poniższym diagramie przedstawiono [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] architektury do uzyskiwania dostępu do danych:  
  
 ![Diagram architektury programu Entity Framework](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")  
  
 [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Narzędzia można wygenerować klasy pochodzącej od `System.Data.Objects.ObjectContext` lub `System.Data.Entity.DbContext` reprezentujący kontenera jednostek w modelu koncepcyjnym. Ten kontekst obiektu zawiera obiekty do śledzenia zmian i zarządzania tożsamościami, współbieżności i relacje. Ta klasa udostępnia również `SaveChanges` metody zapisującej wstawiania, aktualizacji i usuwa ze źródłem danych. Jak zapytania zmiany te są wykonywane zarówno przez polecenia są generowane automatycznie przez system lub procedur składowanych, które są określone przez dewelopera.  
  
<a name="DataProviders"></a>   
## <a name="data-providers"></a>Dostawcy danych  
 `EntityClient` Dostawca rozszerza [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] modelu dostawcy, uzyskując dostęp do danych pod względem koncepcyjnym jednostki i relacje. Wykonywania zapytania, które używają [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)]udostępnia podstawowy język zapytań umożliwiający tworzenie `EntityClient` do komunikowania się z bazą danych. Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera zaktualizowane dostawcy danych SqlClient obsługuje drzew poleceń w postaci kanonicznej. Aby uzyskać więcej informacji, zobacz [SqlClient Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).  
  
<a name="Tools"></a>   
## <a name="entity-data-model-tools"></a>Narzędzi modelu danych jednostki  
 Razem z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] środowiska uruchomieniowego, [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] obejmuje mapowanie i modelowanie narzędzi. Aby uzyskać więcej informacji, zobacz [modelowania i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).  
  
<a name="LearnMore"></a>   
## <a name="learning-more"></a>Dowiedzieć się więcej  
 Poniższe tematy umożliwiają Dowiedz się więcej o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
 [Wprowadzenie](../../../../../docs/framework/data/adonet/ef/getting-started.md)  
 Podaj informacje o tym, jak do uruchomienia i działanie szybko przy użyciu [szybkiego startu](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675), który wskazuje, jak utworzyć prostą [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.  
  
 [Terminologia programu Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)  
 Definiuje wiele warunków, które zostaną wprowadzone w modelu Entity Data Model i [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i które są używane w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji.  
  
 [Zasoby programu Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md)  
 Zawiera linki do tematy dotyczące pojęć i linki do tematów zewnętrznych i zasoby do budowy [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Program Entity Framework na platformie ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)
