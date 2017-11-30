---
title: Architektura ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 227bef975a54676ceda5f922ed02f98c27fc8759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="adonet-architecture"></a>Architektura ADO.NET
Przetwarzanie danych ma tradycyjnie zależał przede wszystkim od modelu opartego na połączeniach, dwuwarstwowa. Ponieważ przetwarzanie danych używa coraz wielowarstwowych architekturach, programistów przełączenie się do odłączonego rozwiązanie zapewniające lepszą skalowalność dla swoich aplikacji.  
  
## <a name="adonet-components"></a>Składniki ADO.NET  
 Dwa główne składniki [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] do uzyskiwania dostępu do danych i operowanie nimi są [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych i <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>Dostawcy danych .NET framework  
 Dostawcy danych .NET Framework są składnikami, które zostały jawnie zaprojektowane do manipulowania danymi i szybkie, tylko do przodu, tylko do odczytu dostęp do danych. `Connection` Obiektu udostępnia połączenie ze źródłem danych. `Command` Obiektu umożliwia dostęp do bazy danych poleceń, aby zwrócić dane, modyfikować danych, uruchamiania procedur składowanych i wysłać lub pobrać informacji o parametrach. `DataReader` Zawiera wysoko wydajnych strumienia danych ze źródła danych. Na koniec `DataAdapter` zapewnia mostka między `DataSet` obiekt i źródła danych. `DataAdapter` Używa `Command` obiekty do wykonania polecenia SQL w źródle danych do obu obciążenia `DataSet` z danymi i uzgodnienia zmian wprowadzonych w danych w `DataSet` do źródła danych. Aby uzyskać więcej informacji, zobacz [dostawcy danych .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) i [pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Zestaw danych  
 ADO.NET `DataSet` jawnie zaprojektowano pod kątem dostępu do danych niezależnie od dowolnego źródła danych. W związku z tym mogą być używane w wielu i źródłami danych różnych, używany z danych XML lub używane do zarządzania dane lokalne aplikacji. `DataSet` Zawiera co najmniej jedną kolekcję <xref:System.Data.DataTable> obiektów składające się z wierszy i kolumn danych, a także klucz podstawowy obcego klucza, ograniczenia i relacji informacje o danych w `DataTable` obiektów. Aby uzyskać więcej informacji, zobacz [zestawów danych, DataTables i DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Na poniższym diagramie przedstawiono związek między [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych i `DataSet`.  
  
 ![Grafika ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Architektura ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Wybranie elementu DataReader lub zestaw danych  
 Jeśli zdecydujesz, czy aplikacja powinna używać `DataReader` (zobacz [pobierania danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) lub `DataSet` (zobacz [zestawów danych, DataTables i DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), należy wziąć pod uwagę rodzaj Funkcja wymaganych przez aplikację. Użyj `DataSet` wykonać następujące czynności:  
  
-   Dzięki czemu można manipulować go w pamięci podręcznej danych lokalnie w aplikacji. Jeśli wymagane jest tylko do odczytu wyników zapytania, `DataReader` jest lepszym rozwiązaniem.  
  
-   Zdalne danych między warstwami lub usługi XML sieci Web.  
  
-   Współdziałanie z danymi dynamicznie takich jak powiązanie z formantem formularzy systemu Windows lub łączenie i powiązane dane z wielu źródeł.  
  
-   Przetwarzają dużą ilością danych bez konieczności otwarte połączenie ze źródłem danych, dzięki czemu połączenie ma być używane przez innych klientów.  
  
 Jeśli nie jest wymagane funkcje udostępniane przez `DataSet`, może poprawić wydajność aplikacji przy użyciu `DataReader` do zwrócenia danych w sposób tylko do przodu, tylko do odczytu. Mimo że `DataAdapter` używa `DataReader` do wypełnienia zawartość `DataSet` (zobacz [wypełnianie zestawu danych z element DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), za pomocą `DataReader`, może zwiększyć wydajność, ponieważ spowoduje zapisanie pamięci może być zużyte przez `DataSet`i uniknąć przetwarzania, które jest wymagane, aby utworzyć i wypełnić zawartość `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 LINQ do DataSet zapewnia możliwość wykonywania kwerend i kontrolę nad danymi w obiekcie zestawu danych w pamięci podręcznej typów kompilacji. Umożliwia pisanie zapytań w jednym z języka programowania .NET Framework, takich jak C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [LINQ do DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 LINQ do SQL obsługuje zapytania względem modelu obiektów zamapowanego struktur danych relacyjnej bazy danych bez użycia pośredniego modelu koncepcyjnego. Każda tabela jest reprezentowany przez klasę oddzielne ściśle sprzężenia w modelu obiektu schematu relacyjnej bazy danych. LINQ do SQL tłumaczy zapytania o języku zintegrowanym w modelu obiektów języka Transact-SQL i wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, LINQ do SQL tłumaczy wyniki do obiektów. Aby uzyskać więcej informacji, zobacz [LINQ do SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework umożliwia deweloperom tworzenie aplikacji dostęp do danych przez Programowanie w odniesieniu do modelu koncepcyjnego aplikacji, zamiast programowanie bezpośrednio ze schematem relacyjnego magazynu. Celem jest, aby zmniejszyć ilość kodu i konserwacja wymagane przez aplikacje zorientowane na danych. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>Usługi danych WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Służy do wdrażania usług danych w sieci Web lub intranet. Dane mają strukturę jako jednostki i relacje zgodnie ze specyfikacją modelu danych jednostki. Adresowane przez standardowego protokołu HTTP jest wdrożony w tym modelu danych. Aby uzyskać więcej informacji, zobacz [4.5 usługi danych WCF](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML i ADO.NET  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]wykorzystuje możliwości XML w celu zapewnienia odłączonego dostępu do danych. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]została zaprojektowana ręcznie dostępnych z klasami XML w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; oba są składnikami architektury pojedynczego.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]i klasy XML w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zbieżne w `DataSet` obiektu. `DataSet` Można wypełniać za pomocą danych z źródła XML pliku lub strumienia XML. `DataSet` Mogą być zapisywane jako World Wide Web konsorcjum W3C XML zgodnego ze obejmuje schematem XML schematu definition language (XSD) Schema, niezależnie od tego źródła danych w `DataSet`. Ze względu na format serializacji natywnej `DataSet` XML, jest doskonałym średni przenoszenie danych między warstwami, co `DataSet` optymalny wybór dla kontekstu danych i schematu usług zdalnych do i z usługi XML sieci Web. Aby uzyskać więcej informacji, zobacz [dokumenty XML i dane](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET — omówienie](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
