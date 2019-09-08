---
title: Architektura ADO.NET
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 50b8aaf6b07494c44423cf454f667f3bcdce32c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787009"
---
# <a name="adonet-architecture"></a>Architektura ADO.NET
Przetwarzanie danych tradycyjnie opiera się głównie na modelu dwuwarstwowym opartym na połączeniu. Ponieważ przetwarzanie danych w coraz większym stopniu używa architektur wielowarstwowych, programiści przełączają się do rozłączonej metody w celu zapewnienia lepszej skalowalności aplikacji.  
  
## <a name="adonet-components"></a>Składniki ADO.NET  
 Dwa główne składniki ADO.NET do uzyskiwania dostępu do danych i manipulowania nimi są dostawcami danych .NET Framework i <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>Dostawcy danych .NET Framework  
 Dostawcy danych .NET Framework są składnikami, które zostały jawnie zaprojektowane w celu manipulowania danymi i szybkiego, tylko do odczytu do danych. `Connection` Obiekt zapewnia łączność ze źródłem danych. `Command` Obiekt umożliwia dostęp do poleceń bazy danych, aby zwracać dane, modyfikować dane, uruchamiać procedury składowane i wysyłać lub pobierać informacje o parametrach. `DataReader` Zapewnia wysoką wydajność strumienia danych ze źródła danych. Na `DataAdapter` koniec udostępnia mostek `DataSet` między obiektem a źródłem danych. Używa obiektów do wykonywania poleceń SQL w `DataSet` źródle danych w celu załadowania danych z danymi i uzgodnienia zmian wprowadzonych w `DataSet` danych z powrotem ze źródłem danych. `Command` `DataAdapter` Aby uzyskać więcej informacji, zobacz [.NET Framework dostawców danych](data-providers.md) oraz [pobieranie i modyfikowanie danych w programie ADO.NET](retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Zestaw danych  
 ADO.NET `DataSet` został jawnie zaprojektowany na potrzeby dostępu do danych niezależnie od źródła danych. W związku z tym może być używany z wieloma i różnymi źródłami danych, używanymi z danymi XML lub używanymi do zarządzania danymi lokalnymi w aplikacji. Zawiera kolekcję co najmniej jednego <xref:System.Data.DataTable> obiektu składającego się z wierszy i kolumn danych, a także klucz podstawowy, klucz obcy, ograniczenie i informacje `DataTable` o relacji dotyczące danych w obiektach. `DataSet` Aby uzyskać więcej informacji, zobacz [zestawy danych, DataTables i DataViews](./dataset-datatable-dataview/index.md).  
  
 Na poniższym diagramie przedstawiono relację między dostawcą danych .NET Framework a `DataSet`.  
  
 ![Grafika ADO.NET](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Architektura ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Wybieranie elementu DataReader lub zestawu danych  
 W przypadku podjęcia decyzji o tym, czy aplikacja `DataReader` powinna korzystać z (zobacz [pobieranie danych przy użyciu elementu DataReader](retrieving-data-using-a-datareader.md)), czy `DataSet` (zobacz [zestawy DataSet, DataTables i DataViews](./dataset-datatable-dataview/index.md)), należy wziąć pod uwagę typ funkcjonalności wymaganej przez aplikację. Użyj, `DataSet` aby wykonać następujące czynności:  
  
- Buforuj dane lokalnie w aplikacji, aby umożliwić manipulowanie nimi. Jeśli musisz tylko odczytać wyniki zapytania, `DataReader` jest to lepszy wybór.  
  
- Zdalne dane między warstwami lub z usługi sieci Web XML.  
  
- Pracuj z danymi dynamicznymi, takimi jak powiązanie z kontrolką Windows Forms lub łączenie i odnoszące się do danych z wielu źródeł.  
  
- Wykonaj rozległe przetwarzanie danych bez konieczności otwierania połączenia ze źródłem danych, które zwalnia połączenie, które będzie używane przez innych klientów.  
  
 Jeśli nie są wymagane funkcje zapewniane `DataSet`przez program, można zwiększyć wydajność aplikacji przy `DataReader` użyciu funkcji, aby zwrócić dane tylko do odczytu. `DataReader`Chociaż program `DataAdapter` `DataReader` używa do`DataSet` wypełniania zawartości (zobacz [wypełnianie zestawu danych z elementu DataAdapter](populating-a-dataset-from-a-dataadapter.md)) przy użyciu, można zwiększyć wydajność, ponieważ spowoduje to oszczędność pamięci, która będzie używana przez i należy unikać przetwarzania wymaganego do utworzenia i wypełnienia zawartości `DataSet`. `DataSet`  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 LINQ to DataSet zapewnia możliwości zapytań i sprawdzanie typów w czasie kompilacji dla danych w pamięci podręcznej w obiekcie DataSet. Umożliwia pisanie zapytań w jednym z .NET Framework języku deweloperskim, takich jak C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 LINQ to SQL obsługuje zapytania względem modelu obiektów, który jest mapowany do struktur danych relacyjnej bazy danych bez użycia pośredniego modelu koncepcyjnego. Każda tabela jest reprezentowana przez oddzielną klasę, ściśle sprzęgając model obiektów do schematu relacyjnej bazy danych. LINQ to SQL tłumaczy zapytania zintegrowane z językiem w modelu obiektów na Transact-SQL i wysyła je do bazy danych w celu wykonania. Gdy baza danych zwróci wyniki, LINQ to SQL przetłumaczy wyniki z powrotem na obiekty. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>Program Entity Framework na platformie ADO.NET  
 ADO.NET Entity Framework jest zaprojektowana tak, aby umożliwić deweloperom tworzenie aplikacji do uzyskiwania dostępu do danych przez programowanie względem koncepcyjnego modelu aplikacji zamiast programowania bezpośrednio względem relacyjnego schematu magazynu. Celem jest zmniejszenie ilości kodu i konserwacji wymaganych przez aplikacje zorientowane na dane. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](./ef/index.md).  
  
## <a name="wcf-data-services"></a>Usługi danych WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]służy do wdrażania usług danych w sieci Web lub intranecie. Dane są uporządkowane jako jednostki i relacje zgodnie ze specyfikacjami Entity Data Model. Dane wdrożone w tym modelu są adresowane przy użyciu standardowego protokołu HTTP. Aby uzyskać więcej informacji, zobacz [4.5 usług danych WCF](../wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML i ADO.NET  
 ADO.NET wykorzystuje moc XML w celu zapewnienia nieprzerwanego dostępu do danych. ADO.NET została zaprojektowana z użyciem klas XML w .NET Framework; Oba są składnikami pojedynczej architektury.  
  
 ADO.NET i klasy XML w .NET Framework są zbieżne w `DataSet` obiekcie. `DataSet` Można wypełnić danymi ze źródła XML, niezależnie od tego, czy jest to plik, czy strumień XML. Może być zapisany jako plik XML zgodny ze standardem World Wide Web Consortium (W3C), który obejmuje schemat jako schemat języka definicji schematu XML (XSD), niezależnie od źródła danych `DataSet`w. `DataSet` Ze względu na natywny format `DataSet` serializacji pliku XML, jest to doskonałe rozwiązanie do przemieszczania danych między warstwami, `DataSet` co zapewnia optymalny wybór dla danych zdalnych i kontekstu schematu do i z usługi sieci Web XML. Aby uzyskać więcej informacji, zobacz [dokumenty XML i dane](../../../standard/data/xml/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](ado-net-overview.md)
