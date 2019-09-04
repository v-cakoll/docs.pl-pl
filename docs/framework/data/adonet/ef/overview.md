---
title: Omówienie programu Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 0934afa96a88b48d8af2d613e83ba793e2f75e71
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248603"
---
# <a name="entity-framework-overview"></a>Przegląd Entity Framework

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] To zestaw technologii w ADO.NET, który obsługuje opracowywanie aplikacji zorientowanych na dane. Architektzy i deweloperzy aplikacji zorientowanych na dane są niezbędni do osiągnięcia dwóch bardzo różnych celów. Muszą one modelować jednostki, relacje i logikę problemów firmy, które są przez nie rozwiązywane, a także muszą współdziałać z wyszukiwarkami danych używanymi do przechowywania i pobierania danych. Dane mogą obejmować wiele systemów magazynowania, z których każda jest z własnymi protokołami. nawet aplikacje, które współpracują z pojedynczym systemem magazynu, muszą zrównoważyć wymagania systemu magazynu przed wymaganiami pisania wydajnego i obsługiwanego kodu aplikacji.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia deweloperom współdziałanie z danymi w postaci obiektów i właściwości specyficznych dla domeny, takich jak klienci i adresy klientów, bez konieczności zapoznania się z podstawowymi tabelami baz danych i kolumnami, w których są przechowywane te dane . [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]Deweloperzy mogą korzystać z wyższego poziomu abstrakcji, gdy zajmują się danymi, i mogą tworzyć i obsługiwać aplikacje zorientowane na dane przy użyciu mniejszego kodu niż w tradycyjnych aplikacjach. Ponieważ jest to składnik .NET Framework, aplikacje można uruchamiać [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] na dowolnym komputerze, na którym jest zainstalowany .NET Framework rozpoczynający się od wersji 3,5 programu SP1. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]

## <a name="give-life-to-models"></a>Zapewnij życie dla modeli
 Od dawna dba i wspólne podejście projektowe podczas kompilowania aplikacji lub usługi jest podziałem aplikacji lub usługi na trzy części: model domeny, model logiczny i model fizyczny. Model domeny definiuje jednostki i relacje w systemie, który jest modelem. Model logiczny dla relacyjnej bazy danych normalizuje jednostki i relacje w tabelach z ograniczeniami klucza obcego. Model fizyczny dotyczy możliwości określonego aparatu danych przez określenie szczegółów magazynu, takich jak partycjonowanie i indeksowanie.

 Model fizyczny jest rafinowany przez administratorów bazy danych w celu zwiększenia wydajności, ale programiści piszący kod aplikacji przede wszystkim zawężają się do pracy z modelem logicznym, pisząc zapytania SQL i wywołując procedury składowane. Modele domen są zwykle używane jako narzędzie do przechwytywania i komunikowania się z wymaganiami aplikacji, często tak jak w przypadku diagramów obojętnych, które są wyświetlane i omówione w wczesnych etapach projektu, a następnie porzucone. Wiele zespołów programistycznych pomija Tworzenie modelu koncepcyjnego i rozpoczyna się od określenia tabel, kolumn i kluczy w relacyjnej bazie danych.

 Daje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] to możliwość tworzenia modeli przez umożliwienie deweloperom wykonywania zapytań o jednostki i relacje w modelu domeny (nazywany modelem *koncepcyjnym* w), [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]podczas gdy [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] polega na tym, aby przetłumaczyć te operacje na źródło danych — określone polecenia. Spowoduje to zwolnienie aplikacji z zakodowanych zależności w konkretnym źródle danych.

 Podczas pracy z Code First model koncepcyjny jest mapowany na model magazynu w kodzie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Można wywnioskować model koncepcyjny w oparciu o typy obiektów i dodatkowe konfiguracje, które definiujesz. Metadane mapowania są generowane w czasie wykonywania na podstawie kombinacji sposobu definiowania typów domen i dodatkowych informacji konfiguracyjnych dostarczanych w kodzie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]generuje bazę danych zgodnie z wymaganiami na podstawie metadanych. Aby uzyskać więcej informacji, zobacz [Tworzenie i mapowanie modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkID=235382).

 Podczas pracy z narzędziami Entity Data Model, model koncepcyjny, model magazynu i mapowania między nimi są wyrażane w schematach opartych na języku XML i zdefiniowane w plikach, które mają odpowiednie rozszerzenia nazw:

- Język definicji schematu koncepcyjnego (CSDL) definiuje model koncepcyjny. CSDL jest [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]implementacją [Entity Data Model](../entity-data-model.md). Rozszerzenie pliku jest. csdl.

- Język definicji schematu magazynu (SSDL) definiuje model magazynu, który jest również nazywany modelem logicznym. Rozszerzenie pliku to. SSDL.

- Język Specyfikacja mapowania (MSL) definiuje mapowania między modelami magazynu i koncepcyjnymi. Rozszerzenie pliku to. MSL.

Model magazynu i mapowania mogą ulegać zmianom w razie potrzeby bez konieczności wprowadzania zmian w modelu koncepcyjnym, klasach danych lub kodzie aplikacji. Ponieważ modele magazynu są specyficzne dla dostawcy, można korzystać ze spójnego modelu koncepcyjnego w różnych źródłach danych.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa tego modelu i plików mapowania do tworzenia, odczytywania, aktualizowania i usuwania operacji względem jednostek i relacji w modelu koncepcyjnym do równoważnych operacji w źródle danych. Program [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje również jednostki mapowania w modelu koncepcyjnym do procedur składowanych w źródle danych. Aby uzyskać więcej informacji, zobacz [specyfikacje CSDL, SSDL i MSL](./language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Mapowanie obiektów na dane
 Programowanie zorientowane obiektowo stanowi wyzwanie dla współpracy z systemami magazynowania danych. Chociaż organizacja klas często odzwierciedla organizację tabel relacyjnych baz danych, dopasowanie nie jest idealne. Wiele znormalizowanych tabel często odpowiada pojedynczej klasie, a relacje między klasami są często reprezentowane inaczej niż reprezentowane są relacje między tabelami. Na przykład, aby reprezentować klienta dla zamówienia sprzedaży, `Order` Klasa może używać właściwości, która zawiera odwołanie do wystąpienia `Customer` klasy, natomiast `Order` wiersz tabeli w bazie danych zawiera kolumnę klucza obcego (lub zestaw kolumn) wartość, która odnosi się do wartości klucza podstawowego w `Customer` tabeli. Klasa może mieć właściwość o nazwie `Orders` , która zawiera `Order` kolekcję wystąpień klasy, podczas gdy `Customer` tabela w bazie danych nie ma porównywalnej kolumny. `Customer` [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zapewnia deweloperom elastyczność umożliwiającą reprezentowanie relacji w ten sposób lub bardziej ścisłe relacje między modelami, które są reprezentowane w bazie danych.

 Istniejące rozwiązania podjęły próbę mostkowania tej przerwy, która jest często nazywana "niezgodnością", tylko mapując klasy zorientowane obiektowo i właściwości na relacyjne tabele i kolumny. Zamiast korzystać z tego tradycyjnego podejścia, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Mapowanie tabel relacyjnych, kolumn i ograniczeń klucza obcego w modelach logicznych na jednostki i relacje w modelach koncepcyjnych. Zapewnia to większą elastyczność zarówno w definiowaniu obiektów, jak i optymalizowaniu modelu logicznego. Narzędzia Entity Data Model generują rozszerzalne klasy danych na podstawie modelu koncepcyjnego. Klasy te są klasami częściowymi, które można rozszerzyć z dodatkowymi elementami członkowskimi dodawanymi przez dewelopera. Domyślnie klasy, które są generowane dla określonego modelu koncepcyjnego, pochodzą z klas podstawowych, które udostępniają usługi dla jednostek materializacji jako obiekty i do śledzenia i zapisywania zmian. Deweloperzy mogą używać tych klas do pracy z jednostkami i relacjami jako obiektami związanymi ze skojarzeniami. Deweloperzy mogą również dostosować klasy, które są generowane dla modelu koncepcyjnego. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Dostęp i zmiana danych jednostki

Więcej niż tylko inne rozwiązanie do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mapowania relacyjnego obiektów, które ma podstawowe znaczenie dla włączania aplikacji do uzyskiwania dostępu do danych, które są reprezentowane jako jednostki i relacje w modelu koncepcyjnym. Program [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] używa informacji w modelu i mapowania plików do tłumaczenia zapytań obiektów na typy jednostek reprezentowane w modelu koncepcyjnym do zapytań specyficznych dla źródła danych. Wyniki zapytania są uwzględniane w obiektach zarządzanych przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] program. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zapewnia następujące sposoby wykonywania zapytań względem modelu koncepcyjnego i zwracania obiektów:

- LINQ to Entities. Zapewnia obsługę zapytań opartych na języku (LINQ) do wykonywania zapytań o typy jednostek, które są zdefiniowane w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](./language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialekt niezależny od magazynu SQL, który działa bezpośrednio z jednostkami w modelu koncepcyjnym i obsługuje koncepcje Entity Data Model. [!INCLUDE[esql](../../../../../includes/esql-md.md)]jest używany zarówno z kwerendami obiektów, jak i kwerendami, które są wykonywane przy użyciu dostawcy EntityClient. Aby uzyskać więcej informacji, zobacz [Entity SQL przegląd](./language-reference/entity-sql-overview.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera dostawcę danych EntityClient. Ten dostawca zarządza połączeniami, tłumaczy zapytania jednostek na zapytania specyficzne dla źródła danych i zwraca czytnik danych, którego [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] używa do zmaterializowania danych jednostki w obiektach. Gdy obiekt materializację nie jest wymagany, Dostawca EntityClient może być również używany jako standardowy dostawca danych ADO.NET przez umożliwienie aplikacjom wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytań i używania zwróconego czytnika danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).

Na poniższym diagramie przedstawiono [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] architekturę dostępu do danych:

![Diagram architektury Entity Framework](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Narzędzia Entity Data Model mogą generować klasę pochodną `System.Data.Objects.ObjectContext` lub `System.Data.Entity.DbContext` reprezentującą kontener jednostek w modelu koncepcyjnym. Ten kontekst obiektu udostępnia funkcje śledzenia zmian oraz zarządzania tożsamościami, współbieżnością i relacjami. Ta klasa udostępnia `SaveChanges` również metodę, która zapisuje operacje wstawiania, aktualizacji i usuwania do źródła danych. Podobnie jak w przypadku zapytań, te zmiany są wykonywane przez polecenia automatycznie generowane przez system lub przez procedury składowane, które są określone przez dewelopera.

## <a name="data-providers"></a>Dostawcy danych

`EntityClient` Dostawca rozszerza model dostawcy ADO.NET, uzyskując dostęp do danych pod względem jednostek koncepcyjnych i relacji. Wykonuje zapytania, które używają [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)]Program udostępnia podstawowy język zapytań umożliwiający `EntityClient` komunikację z bazą danych programu. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera zaktualizowaną dostawca danych SqlClient, która obsługuje drzewa poleceń w postaci kanonicznej. Aby uzyskać więcej informacji, zobacz [SqlClient dla Entity Framework](sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Narzędzia modelu Entity Data Model

Wraz z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] środowiskiem uruchomieniowym program Visual Studio zawiera narzędzia do mapowania i modelowania. Aby uzyskać więcej informacji, zobacz [modelowanie i mapowanie](modeling-and-mapping.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby dowiedzieć się więcej [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]na temat, zobacz:

[Wprowadzenie](getting-started.md) — zawiera informacje o tym, jak szybko rozpocząć pracę, korzystając z [przewodnika Szybki Start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)), który pokazuje, jak [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utworzyć prostą aplikację.

[Terminologia Entity Framework](terminology.md) — definiuje wiele warunków wprowadzonych przez Entity Data Model i [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i, które są używane w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji.

[Zasoby Entity Framework](resources.md) — zawiera linki do tematów koncepcyjnych i linki do zewnętrznych tematów i zasobów służących do kompilowania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.

## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](index.md)
