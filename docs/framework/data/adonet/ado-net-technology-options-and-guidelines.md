---
title: Opcje technologii ADO.NET i wskazówki
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: 0d0e8f7bd779ce7a8290594887630dd192301fe1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700855"
---
# <a name="adonet-technology-options-and-guidelines"></a>Opcje technologii ADO.NET i wskazówki
Platforma danych ADO.NET jest strategia wielu wersji, aby zmniejszyć ilość kodowania i konserwacji wymagane dla deweloperów, należy włączyć je aby programować przy użyciu modeli danych koncepcyjnymi encji. Ta platforma obejmuje ADO.NET Entity Framework i powiązanych technologii.  
  
## <a name="entity-framework"></a>Entity Framework  
 ADO.NET Entity Framework zaprojektowana w celu umożliwienia deweloperom tworzyć aplikacje dostępu do danych przez Programowanie w oparciu o model koncepcyjny aplikacji zamiast programowania bezpośrednio w odniesieniu do schematu magazyn relacyjny. Celem jest zmniejszenie ilości kodu i konserwacji jest wymagana dla aplikacji zorientowanych na dane. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Entity Data Model (EDM)  
 Entity Data Model (EDM) jest specyfikację projektu, który definiuje dane aplikacji jako zestawów jednostek i relacji. Dane w tym modelu obsługuje mapowania obiektowo relacyjny i programowania danych granice aplikacji.  
  
### <a name="object-services"></a>Usługi obiektów  
 Usługi obiektów umożliwia programistom do interakcji z modelu koncepcyjnego za pomocą zestawu typowych klas środowiska uruchomieniowego (języka wspólnego CLR) języka. Te klasy może być automatycznie wygenerowany na podstawie modelu koncepcyjnego lub mogą być tworzone niezależnie odzwierciedlający strukturę modelu koncepcyjnego. Obiekt usługi obsługuje również infrastruktury dla programu Entity Framework, w tym usług, takich jak zarządzanie stanem, sprawdzaniu spójności, rozwiązanie tożsamości, ładowania i, nawigowanie po relacjach, propagowanie zmian obiektu do modyfikacji bazy danych a obsługa języka Entity SQL tworzenia zapytania. Aby uzyskać więcej informacji, zobacz [obiektu usługi — omówienie (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
### <a name="linq-to-entities"></a>LINQ do Jednostek  
 Składnik LINQ to Entities jest implementacja zapytanie o języku zintegrowanym (LINQ), który umożliwia deweloperom tworzenie silnie typizowane zapytania w odniesieniu do kontekstu obiektów programu Entity Framework za pomocą wyrażenia LINQ i LINQ standardowych operatorów zapytań. Składnik LINQ to Entities umożliwia deweloperom pracować z modelu koncepcyjnego za pomocą bardzo elastyczny mapowania obiektowo relacyjny programu Microsoft SQL Server i baz danych innych firm. Aby uzyskać więcej informacji, zobacz [składnik LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Entity SQL  
 Jednostka SQL jest język kwerendy oparte na tekście przeznaczone do interakcji z modelu Entity Data Model. Jednostka SQL jest dialekt SQL, który zawiera konstrukcje zapytań pod względem wyższego poziomu modelowania, takich jak dziedziczenie, złożonych typów i relacji jawnego. Deweloperzy mogą również używać jednostki SQL bezpośrednio z usługi obiektów. Aby uzyskać więcej informacji, zobacz [jednostki języka SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 Dostawca EntityClient jest używane do interakcji z modelu Entity Data Model nowego dostawcy danych .NET Framework. Dostawca EntityClient jest zgodny ze wzorcem dostawcy danych .NET Framework, ujawnienia <xref:System.Data.EntityClient.EntityConnection> i <xref:System.Data.EntityClient.EntityCommand> obiekty, które zwraca <xref:System.Data.EntityClient.EntityDataReader>. Dostawca EntityClient w programach języka Entity SQL, zapewniając elastyczne mapowania z dostawcami magazynu danych. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
### <a name="entity-data-model-tools"></a>Narzędzia modelu danych jednostki  
 Entity Framework udostępnia narzędzia wiersza polecenia, kreatory i projektanci w celu ułatwienia tworzenia EDM aplikacji. Sterowanie EntityDataSource obsługuje scenariusze powiązania danych w oparciu o EDM. Powierzchni programowania formantu EntityDataSource jest podobne do innych formantów źródła danych w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzia modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 LINQ do SQL jest relacyjne mapowanie obiektów (lub / M) wdrożenia, która pozwala na model bazy danych programu SQL Server przy użyciu klas .NET Framework. LINQ do SQL umożliwia wykonywanie zapytań bazy danych przy użyciu LINQ, jak również aktualizacji, wstawianie i usuwanie danych z niego. LINQ do SQL obsługuje transakcje, widoków i procedur składowanych, zapewniając łatwy sposób Zintegruj swój model danych sprawdzanie poprawności danych i reguł logiki biznesowej. Object Relational Designer (O/R Designer) służy do modelowania klas jednostek i skojarzenia, które są oparte na obiektach w bazie danych. Aby uzyskać więcej informacji, zobacz [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>Usługi danych WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Służy do wdrażania usług danych w Internecie lub intranecie. Dane mają strukturę jako jednostek i relacji zgodnie ze specyfikacją modelu Entity Data Model. Adresowane przez standardowego protokołu HTTP jest wdrożony w tym modelu danych. Aby uzyskać więcej informacji, zobacz [4.5 usług danych WCF](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Nowości w programie ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
