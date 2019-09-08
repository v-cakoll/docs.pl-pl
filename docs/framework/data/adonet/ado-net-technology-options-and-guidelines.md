---
title: Opcje technologii ADO.NET i wskazówki
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: d0f363d5eb102edf965c9c6068873fce0721d288
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785774"
---
# <a name="adonet-technology-options-and-guidelines"></a>Opcje technologii ADO.NET i wskazówki
Platforma danych ADO.NET to strategia wielu wersji, która pozwala zmniejszyć ilość kodowania i konserwacji, które są wymagane dla deweloperów, umożliwiając im programowanie modeli danych jednostki koncepcyjnej. Ta platforma zawiera Entity Framework ADO.NET i powiązane technologie.  
  
## <a name="entity-framework"></a>Entity Framework  
 ADO.NET Entity Framework jest zaprojektowana tak, aby umożliwić deweloperom tworzenie aplikacji do uzyskiwania dostępu do danych przez programowanie względem koncepcyjnego modelu aplikacji zamiast programowania bezpośrednio względem relacyjnego schematu magazynu. Celem jest zmniejszenie ilości kodu i konserwacji wymaganych przez aplikacje zorientowane na dane. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](./ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Entity Data Model (EDM)  
 Entity Data Model (EDM) to specyfikacja projektowania, która definiuje dane aplikacji jako zestawy jednostek i relacji. Dane w tym modelu obsługują mapowanie relacyjne obiektów i programowalność danych między granicami aplikacji.  
  
### <a name="object-services"></a>Usługi obiektów  
 Usługi obiektów umożliwiają programistom współdziałanie z modelem koncepcyjnym przez zestaw klas środowiska uruchomieniowego języka wspólnego (CLR). Te klasy mogą być generowane automatycznie na podstawie modelu koncepcyjnego lub mogą być opracowane niezależnie, aby odzwierciedlały strukturę modelu koncepcyjnego. Usługi obiektów zapewniają również obsługę infrastruktury dla Entity Framework, w tym usług takich jak zarządzanie stanami, śledzenie zmian, rozpoznawanie tożsamości, ładowanie i nawigowanie po relacjach, propagowanie zmian obiektów do modyfikacji bazy danych. i obsługa tworzenia zapytań dla Entity SQL. Aby uzyskać więcej informacji, zobacz temat [usługi obiektów — omówienie (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
### <a name="linq-to-entities"></a>LINQ do Jednostek  
 LINQ to Entities to implementacja programu Query-Integrated Language (LINQ), która umożliwia deweloperom tworzenie kwerend o jednoznacznie określonym typie względem kontekstu obiektu Entity Framework przy użyciu wyrażeń LINQ i operatorów zapytań standardowych LINQ. LINQ to Entities pozwala deweloperom na współdziałanie z modelem koncepcyjnym z bardzo elastycznym mapowaniem relacyjnym obiektów w Microsoft SQL Server i bazach danych innych firm. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](./ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Entity SQL  
 Entity SQL jest językiem zapytań opartym na tekście zaprojektowanym do współdziałania z Entity Data Model. Entity SQL jest dialektem SQL, który zawiera konstrukcje do wykonywania zapytań w warunkach modelowania wyższego poziomu, takich jak dziedziczenie, typy złożone i jawne relacje. Deweloperzy mogą również używać Entity SQL bezpośrednio z usługami obiektów. Aby uzyskać więcej informacji, zobacz [Entity SQL Language](./ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 EntityClient jest nowym dostawcą danych .NET Framework używanym do współdziałania z Entity Data Model. EntityClient następuje wzorzec dostawcy danych .NET Framework, który uwidacznia <xref:System.Data.EntityClient.EntityConnection> i <xref:System.Data.EntityClient.EntityCommand> obiekty, które zwracają <xref:System.Data.EntityClient.EntityDataReader>. EntityClient współpracuje z językiem Entity SQL, zapewniając elastyczne mapowanie dla dostawców danych specyficznych dla magazynu. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
### <a name="entity-data-model-tools"></a>Narzędzia modelu danych jednostki  
 Entity Framework zawiera narzędzia wiersza polecenia, kreatorów i projektantów, które ułatwiają tworzenie aplikacji modelu EDM. Formant EntityDataSource obsługuje scenariusze powiązań danych na podstawie modelu EDM. Powierzchnia programowania kontrolki EntityDataSource jest podobna do innych formantów źródła danych w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzia ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 LINQ to SQL to implementacja relacyjnego mapowania obiektów (lub/M), która umożliwia modelowanie SQL Serverj bazy danych przy użyciu klas .NET Framework. LINQ to SQL umożliwia wykonywanie zapytań dotyczących bazy danych za pomocą LINQ, a także aktualizowanie, wstawianie i usuwanie danych z tego programu. LINQ to SQL obsługuje transakcje, widoki i procedury składowane, zapewniając łatwy sposób integrowania sprawdzania poprawności danych i reguł logiki biznesowej z modelem danych. Można użyć Object Relational Designer (Projektant O/R) do modelowania klas jednostek i skojarzeń opartych na obiektach w bazie danych. Aby uzyskać więcej informacji, zobacz [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>Usługi danych WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]wdraża usługi danych w sieci Web lub w intranecie. Dane są uporządkowane jako jednostki i relacje zgodnie ze specyfikacjami Entity Data Model. Dane wdrożone w tym modelu są adresowane przy użyciu standardowego protokołu HTTP. Aby uzyskać więcej informacji, zobacz [4.5 usług danych WCF](../wcf/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](ado-net-overview.md)
- [Nowości w programie ADO.NET](whats-new.md)
