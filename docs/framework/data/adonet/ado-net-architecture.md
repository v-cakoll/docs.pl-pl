---
title: Architektura ADO.NET
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 4c2299951202794112ea66c1f20025777c68e356
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870318"
---
# <a name="adonet-architecture"></a>Architektura ADO.NET
Przetwarzanie danych tradycyjnie opierało się głównie na modelu opartego na połączeniach, dwuwarstwowy. Jak przetwarzanie danych coraz większym stopniu korzysta z architektury wielowarstwowej, programistów przełączenie się do odłączonego podejście, aby zapewnić lepszą skalowalność dla swoich aplikacji.  
  
## <a name="adonet-components"></a>Składniki ADO.NET  
 Dwa główne składniki [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] do uzyskiwania dostępu do danych i manipulowania nimi są [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych i <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>Dostawcy danych .NET framework  
 Dostawcy danych .NET Framework są składnikami, które zostały jawnie zaprojektowane do manipulowania danymi i szybkie tylko do przodu, tylko do odczytu dostępu do danych. `Connection` Obiektu zapewnia łączność ze źródłem danych. `Command` Obiekt umożliwia dostęp do bazy danych poleceń, aby zwrócić dane, modyfikowania danych, uruchamianie procedur składowanych i wysyłać lub odbierać informacje o parametrach. `DataReader` Zapewnia strumienia o wysokiej wydajności, dane ze źródła danych. Na koniec `DataAdapter` zapewnia połączenie między `DataSet` obiektu i źródła danych. `DataAdapter` Używa `Command` obiektów do wykonywania poleceń SQL w źródle danych, zarówno obciążenie `DataSet` z danymi i uzgadniają zmiany, które zostały wprowadzone do danych w `DataSet` wstecz do źródła danych. Aby uzyskać więcej informacji, zobacz [dostawcy danych .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) i [pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Zestaw danych  
 ADO.NET `DataSet` jawnie zaprojektowano pod kątem dostępu do danych niezależnie od dowolnego źródła danych. W rezultacie mogą być używane z wieloma i danych różnych źródeł, używany z danymi XML lub używany do zarządzania danymi lokalne dla aplikacji. `DataSet` Zawiera co najmniej jedną kolekcję <xref:System.Data.DataTable> obiektów składający się z wierszy i kolumn danych, a także klucz podstawowy obcego klucza, ograniczenia i relacji informacje o danych w `DataTable` obiektów. Aby uzyskać więcej informacji, zobacz [DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Na poniższym diagramie przedstawiono relację między [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych i `DataSet`.  
  
 ![Grafika ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Architektura ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Wybieranie elementu DataReader lub zestawu danych  
 Gdy zdecydujesz, czy aplikacja powinna używać `DataReader` (zobacz [podczas pobierania danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) lub `DataSet` (zobacz [DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), należy wziąć pod uwagę typ Funkcja wymaganych przez aplikację. Użyj `DataSet` wykonać następujące czynności:  
  
-   Dzięki czemu można przekształcać je w pamięci podręcznej dane lokalnie w aplikacji. Jeśli wymagane jest tylko do odczytu wyników zapytania, `DataReader` jest lepszym rozwiązaniem.  
  
-   Zdalne danych między warstwami lub usługi sieci Web XML.  
  
-   Wchodzić w interakcje z danymi dynamicznie takich jak powiązanie z kontrolką formularzy Windows lub łącząc i powiązane dane z wielu źródeł.  
  
-   Należy przeprowadzić rozległe przetwarzanie danych bez konieczności otwarte połączenie źródła danych, co zwalnia połączenia, który będzie używany przez innych klientów.  
  
 Jeśli nie jest wymagane funkcje udostępniane przez `DataSet`, może poprawić wydajność aplikacji przy użyciu `DataReader` zwrócić dane w sposób tylko do przodu, tylko do odczytu. Mimo że `DataAdapter` używa `DataReader` do wypełnienia zawartość `DataSet` (zobacz [wypełnianie zestawu danych z elementu DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), za pomocą `DataReader`, może zwiększyć wydajność, ponieważ zapisze pamięci może być używane przez `DataSet`i uniknąć przetwarzania, który jest wymagany, aby utworzyć i wypełnić zawartość `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 Program LINQ to DataSet oferuje możliwości zapytań i typów w czasie kompilacji sprawdzania przez dane buforowane w obiekt DataSet. Umożliwia pisanie zapytań w jednym języku programowania .NET Framework, takich jak C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 LINQ do SQL obsługuje zapytania względem modelu obiektów, mapowanego do struktur danych relacyjnej bazy danych bez użycia pośrednie modelu koncepcyjnego. Każda tabela jest reprezentowany przez osobnej klasy sprzęganiu model obiektu schematu relacyjnej bazy danych. LINQ do SQL tłumaczy zapytania o języku zintegrowanym w modelu obiektów na instrukcji języka Transact-SQL i wysyła je do bazy danych do wykonania. Po powrocie z bazy danych wyników programu LINQ to SQL tłumaczy wyniki do obiektów. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>Program Entity Framework na platformie ADO.NET  
 ADO.NET Entity Framework zaprojektowana w celu umożliwienia deweloperom tworzyć aplikacje dostępu do danych przez Programowanie w oparciu o model koncepcyjny aplikacji zamiast programowania bezpośrednio w odniesieniu do schematu magazyn relacyjny. Celem jest zmniejszenie ilości kodu i konserwacji jest wymagana dla aplikacji zorientowanych na dane. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>Usługi danych WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Służy do wdrażania usług danych w Internecie lub intranecie. Dane mają strukturę jako jednostek i relacji zgodnie ze specyfikacją modelu Entity Data Model. Adresowane przez standardowego protokołu HTTP jest wdrożony w tym modelu danych. Aby uzyskać więcej informacji, zobacz [4.5 usług danych WCF](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML i ADO.NET  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] korzysta z mocy XML w celu zapewnienia odłączonego dostępu do danych. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] została zaprojektowana ręcznie — dostępnych z klasami XML [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; obie są składniki architektury jednego.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] i klasy XML w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zbiegają się w `DataSet` obiektu. `DataSet` Można wypełnić danymi ze źródła XML, czy jest pliku lub strumienia XML. `DataSet` Może być zapisana jako World Wide Web Consortium (W3C) XML zgodne, który zawiera jego schematu XML definicji język (XSD) schematu, niezależnie od źródła danych w `DataSet`. Ze względu na format serializacji natywnej `DataSet` język XML, jest to doskonałe medium do przenoszenia danych między warstwami, dzięki czemu `DataSet` optymalnym wyborem dla kontekstu danych i schematu usług zdalnych do i z usługi sieci Web XML. Aby uzyskać więcej informacji, zobacz [dokumenty i dane XML](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
