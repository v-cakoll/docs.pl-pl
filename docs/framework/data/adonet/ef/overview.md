---
title: Omówienie programu Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: b68db4f139330ccc1da5057498a37a08d00ba266
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738507"
---
# <a name="entity-framework-overview"></a>Przegląd Entity Framework

Entity Framework to zestaw technologii ADO.NET, które obsługują opracowywanie aplikacji zorientowanych na dane. Architektzy i deweloperzy aplikacji zorientowanych na dane są niezbędni do osiągnięcia dwóch bardzo różnych celów. Muszą one modelować jednostki, relacje i logikę problemów firmy, które są przez nie rozwiązywane, a także muszą współdziałać z wyszukiwarkami danych używanymi do przechowywania i pobierania danych. Dane mogą obejmować wiele systemów magazynowania, z których każda jest z własnymi protokołami. nawet aplikacje, które współpracują z pojedynczym systemem magazynu, muszą zrównoważyć wymagania systemu magazynu przed wymaganiami pisania wydajnego i obsługiwanego kodu aplikacji.

Entity Framework pozwala deweloperom na współpracę z danymi w postaci obiektów i właściwości specyficznych dla domeny, takich jak klienci i adresy klientów, bez konieczności zapoznania się z podstawowymi bazami danych i kolumnami, w których te dane są zapis. Dzięki Entity Framework deweloperzy mogą korzystać z wyższego poziomu abstrakcji, gdy zajmują się danymi, i mogą tworzyć i konserwować aplikacje zorientowane na dane przy użyciu mniejszego kodu niż w tradycyjnych aplikacjach. Ponieważ Entity Framework jest składnikiem .NET Framework, Entity Framework aplikacje można uruchamiać na dowolnym komputerze, na którym zainstalowano .NET Framework od wersji 3,5 SP1.

## <a name="give-life-to-models"></a>Zapewnij życie dla modeli
 Od dawna dba i wspólne podejście projektowe podczas kompilowania aplikacji lub usługi jest podziałem aplikacji lub usługi na trzy części: model domeny, model logiczny i model fizyczny. Model domeny definiuje jednostki i relacje w systemie, który jest modelem. Model logiczny dla relacyjnej bazy danych normalizuje jednostki i relacje w tabelach z ograniczeniami klucza obcego. Model fizyczny dotyczy możliwości określonego aparatu danych przez określenie szczegółów magazynu, takich jak partycjonowanie i indeksowanie.

 Model fizyczny jest rafinowany przez administratorów bazy danych w celu zwiększenia wydajności, ale programiści piszący kod aplikacji przede wszystkim zawężają się do pracy z modelem logicznym, pisząc zapytania SQL i wywołując procedury składowane. Modele domen są zwykle używane jako narzędzie do przechwytywania i komunikowania się z wymaganiami aplikacji, często tak jak w przypadku diagramów obojętnych, które są wyświetlane i omówione w wczesnych etapach projektu, a następnie porzucone. Wiele zespołów programistycznych pomija Tworzenie modelu koncepcyjnego i rozpoczyna się od określenia tabel, kolumn i kluczy w relacyjnej bazie danych.

 Entity Framework umożliwia tworzenie modeli przez umożliwienie deweloperom wykonywania zapytań o jednostki i relacje w modelu domeny (nazywany modelem *koncepcyjnym* w Entity Framework), a jednocześnie polega na Entity Framework przetłumaczeniu tych operacji na źródło danych — określone polecenia. Spowoduje to zwolnienie aplikacji z zakodowanych zależności w konkretnym źródle danych.

 Podczas pracy z Code First model koncepcyjny jest mapowany na model magazynu w kodzie. Entity Framework może wywnioskować model koncepcyjny w oparciu o typy obiektów i dodatkowe konfiguracje, które definiujesz. Metadane mapowania są generowane w czasie wykonywania na podstawie kombinacji sposobu definiowania typów domen i dodatkowych informacji konfiguracyjnych dostarczanych w kodzie. Entity Framework generuje bazę danych zgodnie z wymaganiami na podstawie metadanych. Aby uzyskać więcej informacji, zobacz [Tworzenie i mapowanie modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkID=235382).

 Podczas pracy z narzędziami Entity Data Model, model koncepcyjny, model magazynu i mapowania między nimi są wyrażane w schematach opartych na języku XML i zdefiniowane w plikach, które mają odpowiednie rozszerzenia nazw:

- Język definicji schematu koncepcyjnego (CSDL) definiuje model koncepcyjny. CSDL jest implementacją Entity Framework [Entity Data Model](../entity-data-model.md). Rozszerzenie pliku jest. csdl.

- Język definicji schematu magazynu (SSDL) definiuje model magazynu, który jest również nazywany modelem logicznym. Rozszerzenie pliku to. SSDL.

- Język Specyfikacja mapowania (MSL) definiuje mapowania między modelami magazynu i koncepcyjnymi. Rozszerzenie pliku to. MSL.

Model magazynu i mapowania mogą ulegać zmianom w razie potrzeby bez konieczności wprowadzania zmian w modelu koncepcyjnym, klasach danych lub kodzie aplikacji. Ponieważ modele magazynu są specyficzne dla dostawcy, można korzystać ze spójnego modelu koncepcyjnego w różnych źródłach danych.

Entity Framework używa tego modelu i mapowania plików do tworzenia, odczytywania, aktualizowania i usuwania operacji względem jednostek i relacji w modelu koncepcyjnym do równoważnych operacji w źródle danych. Entity Framework nawet obsługuje mapowanie jednostek w modelu koncepcyjnym na procedury składowane w źródle danych. Aby uzyskać więcej informacji, zobacz [specyfikacje CSDL, SSDL i MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).

## <a name="map-objects-to-data"></a>Mapowanie obiektów na dane
 Programowanie zorientowane obiektowo stanowi wyzwanie dla współpracy z systemami magazynowania danych. Chociaż organizacja klas często odzwierciedla organizację tabel relacyjnych baz danych, dopasowanie nie jest idealne. Wiele znormalizowanych tabel często odpowiada pojedynczej klasie, a relacje między klasami są często reprezentowane inaczej niż reprezentowane są relacje między tabelami. Na przykład, aby reprezentować klienta dla zamówienia sprzedaży, Klasa `Order` może używać właściwości, która zawiera odwołanie do wystąpienia klasy `Customer`, natomiast wiersz tabeli `Order` w bazie danych zawiera kolumnę klucza obcego (lub zestaw kolumn) o wartości, która odnosi się do wartości klucza podstawowego w tabeli `Customer`. Klasa `Customer` może mieć właściwość o nazwie `Orders`, która zawiera kolekcję wystąpień klasy `Order`, podczas gdy tabela `Customer` w bazie danych nie ma porównywalnej kolumny. Entity Framework zapewnia deweloperom elastyczność umożliwiającą reprezentowanie relacji w ten sposób lub bardziej ścisłe relacje między modelami, które są reprezentowane w bazie danych.

 Istniejące rozwiązania podjęły próbę mostkowania tej przerwy, która jest często nazywana "niezgodnością", tylko mapując klasy zorientowane obiektowo i właściwości na relacyjne tabele i kolumny. Zamiast korzystać z tego tradycyjnego podejścia, Entity Framework mapuje tabele relacyjne, kolumny i ograniczenia klucza obcego w modelach logicznych na jednostki i relacje w modelu koncepcyjnym. Zapewnia to większą elastyczność zarówno w definiowaniu obiektów, jak i optymalizowaniu modelu logicznego. Narzędzia Entity Data Model generują rozszerzalne klasy danych na podstawie modelu koncepcyjnego. Klasy te są klasami częściowymi, które można rozszerzyć z dodatkowymi elementami członkowskimi dodawanymi przez dewelopera. Domyślnie klasy, które są generowane dla określonego modelu koncepcyjnego, pochodzą z klas podstawowych, które udostępniają usługi dla jednostek materializacji jako obiekty i do śledzenia i zapisywania zmian. Deweloperzy mogą używać tych klas do pracy z jednostkami i relacjami jako obiektami związanymi ze skojarzeniami. Deweloperzy mogą również dostosować klasy, które są generowane dla modelu koncepcyjnego. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Dostęp i zmiana danych jednostki

Więcej niż tylko inne rozwiązanie do mapowania relacyjnego obiektów Entity Framework ma podstawowe znaczenie dla włączania aplikacji do uzyskiwania dostępu do danych, które są reprezentowane jako jednostki i relacje w modelu koncepcyjnym. Entity Framework używa informacji w modelu i mapowania plików do tłumaczenia zapytań obiektów na typy jednostek reprezentowane w modelu koncepcyjnym do zapytań specyficznych dla źródła danych. Wyniki zapytania są istotne dla obiektów zarządzanych przez Entity Framework. Entity Framework zapewnia następujące sposoby wykonywania zapytań względem modelu koncepcyjnego i zwracania obiektów:

- LINQ to Entities. Zapewnia obsługę zapytań opartych na języku (LINQ) do wykonywania zapytań o typy jednostek, które są zdefiniowane w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](./language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]., Dialekt niezależny od magazynu SQL, który działa bezpośrednio z jednostkami w modelu koncepcyjnym i obsługuje koncepcje Entity Data Model. [!INCLUDE[esql](../../../../../includes/esql-md.md)] jest używany zarówno z kwerendami obiektów, jak i kwerendami, które są wykonywane przy użyciu dostawcy EntityClient. Aby uzyskać więcej informacji, zobacz [Entity SQL przegląd](./language-reference/entity-sql-overview.md).

Entity Framework obejmuje dostawcę danych EntityClient. Ten dostawca zarządza połączeniami, tłumaczy zapytania jednostek na zapytania specyficzne dla źródła danych i zwraca czytnik danych, którego Entity Framework używa do zmaterializowania danych jednostki w obiektach. Gdy obiekt materializację nie jest wymagany, Dostawca EntityClient może być również używany jako standardowy dostawca danych ADO.NET przez umożliwienie aplikacjom wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytań i używania zwróconego czytnika danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).

Na poniższym diagramie przedstawiono architekturę Entity Framework do uzyskiwania dostępu do danych:

![Diagram architektury Entity Framework](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Narzędzia Entity Data Model mogą generować klasę pochodną `System.Data.Objects.ObjectContext` lub `System.Data.Entity.DbContext` reprezentującą kontener jednostek w modelu koncepcyjnym. Ten kontekst obiektu udostępnia funkcje śledzenia zmian oraz zarządzania tożsamościami, współbieżnością i relacjami. Ta klasa udostępnia również metodę `SaveChanges`, która zapisuje operacje wstawiania, aktualizacji i usuwania do źródła danych. Podobnie jak w przypadku zapytań, te zmiany są wykonywane przez polecenia automatycznie generowane przez system lub przez procedury składowane, które są określone przez dewelopera.

## <a name="data-providers"></a>Dostawcy danych

Dostawca `EntityClient` rozszerza model dostawcy ADO.NET, uzyskując dostęp do danych pod względem jednostek koncepcyjnych i relacji. Wykonuje zapytania, które używają [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] udostępnia podstawowy język zapytań, który umożliwia `EntityClient` komunikacji z bazą danych. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).

Entity Framework obejmuje zaktualizowany Dostawca danych SqlClient obsługujący drzewa poleceń w postaci kanonicznej. Aby uzyskać więcej informacji, zobacz [SqlClient dla Entity Framework](sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Narzędzia modelu Entity Data Model

Wraz z Entity Framework środowiska uruchomieniowego program Visual Studio zawiera narzędzia do mapowania i modelowania. Aby uzyskać więcej informacji, zobacz [modelowanie i mapowanie](modeling-and-mapping.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby dowiedzieć się więcej na temat Entity Framework, zobacz:

[Wprowadzenie](getting-started.md) — zawiera informacje o tym, jak szybko rozpocząć pracę, korzystając z [przewodnika Szybki Start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)), który pokazuje, jak utworzyć prostą Entity Framework aplikację.

[Terminologia Entity Framework](terminology.md) — definiuje wiele warunków wprowadzonych przez Entity Data Model i Entity Framework i które są używane w dokumentacji programu Entity Framework.

[Zasoby Entity Framework](resources.md) — zawiera linki do tematów koncepcyjnych i linki do zewnętrznych tematów i zasobów służących do kompilowania aplikacji Entity Framework.

## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](index.md)
