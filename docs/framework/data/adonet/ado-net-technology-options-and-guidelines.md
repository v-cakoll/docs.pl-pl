---
title: Opcje technologii ADO.NET i wskazówki
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: 106fdbc121c3b1c15aaced5e0314e0651387cede
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="adonet-technology-options-and-guidelines"></a>Opcje technologii ADO.NET i wskazówki
Platforma danych ADO.NET to strategii wielu wersji, aby zmniejszyć ilość kodowania i konserwacji wymagane dla deweloperów, należy włączyć je do programowania dla modeli danych jednostki koncepcyjnego. Ta platforma obejmuje ADO.NET Entity Framework i technologii pokrewnych.  
  
## <a name="entity-framework"></a>Entity Framework  
 ADO.NET Entity Framework umożliwia deweloperom tworzenie aplikacji dostęp do danych przez Programowanie w odniesieniu do modelu koncepcyjnego aplikacji, zamiast programowanie bezpośrednio ze schematem relacyjnego magazynu. Celem jest, aby zmniejszyć ilość kodu i konserwacja wymagane przez aplikacje zorientowane na danych. Aby uzyskać więcej informacji, zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Entity Data Model (EDM)  
 Modelu danych jednostki (EDM) jest specyfikację projektu, który definiuje dane aplikacji jako zestawy jednostki i relacje. Dane w tym modelu obsługuje mapowania obiektów relacyjnych i programowania danych poza granicami aplikacji.  
  
### <a name="object-services"></a>Obiekt usługi  
 Obiekt usługi umożliwia deweloperom interakcję z modelu koncepcyjnego za pomocą zestawu wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) klasy. Te klasy mogą być automatycznie generowane przez model koncepcyjny lub mogą być opracowane niezależnie w celu odzwierciedlenia struktury modelu koncepcyjnego. Obiekt usługi również zapewnia obsługę infrastruktury dla programu Entity Framework, takich jak usługi takie jak zarządzanie stanem, śledzenie rozpoznawania tożsamości zmian ładowanie i nawigowanie po relacjach, propagowanie zmian obiektu do modyfikacji bazy danych i obsługę SQL jednostki tworzenia zapytania. Aby uzyskać więcej informacji, zobacz [obiektu usługi — omówienie (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
### <a name="linq-to-entities"></a>LINQ do Jednostek  
 Składnik LINQ to Entities jest implementacja zapytanie o języku zintegrowanym (LINQ), który umożliwia deweloperom tworzenie jednoznacznie zapytań dotyczących kontekst Entity Framework za pomocą wyrażenia LINQ i LINQ standardowych operatorów zapytań. Składnik LINQ to Entities umożliwia deweloperom pracy projektowej modelu koncepcyjnego z bardzo elastyczne mapowania obiektów relacyjnych przez program Microsoft SQL Server i baz danych innych firm. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Entity SQL  
 Jednostka SQL jest język zapytań tekst przeznaczony do współdziałania z modelu danych jednostki. Jednostka SQL jest dialekt SQL, którego zawiera konstrukcje zapytań pod względem wyższego poziomu modelowania, takich jak dziedziczenia, typy złożone i jawnej relacji. Deweloperzy mogą również używać SQL jednostki bezpośrednio z usługami obiektu. Aby uzyskać więcej informacji, zobacz [języka SQL jednostki](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 Dostawca EntityClient jest używana do interakcji z modelu Entity Data Model nowego dostawcy danych .NET Framework. Dostawca EntityClient zgodny ze wzorcem dostawcy danych .NET Framework, ujawnienia <xref:System.Data.EntityClient.EntityConnection> i <xref:System.Data.EntityClient.EntityCommand> obiekty, które zwraca <xref:System.Data.EntityClient.EntityDataReader>. Dostawca EntityClient współpracuje z języka SQL jednostki, zapewniając elastyczne mapowania do dostawcy magazynu danych. Aby uzyskać więcej informacji, zobacz [EntityClient i SQL jednostki](http://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
### <a name="entity-data-model-tools"></a>Narzędzi modelu danych jednostki  
 Entity Framework oferuje narzędzia wiersza polecenia, kreatorów i projektantów w celu ułatwienia tworzenia EDM aplikacji. Sterowanie obiektu EntityDataSource obsługuje scenariusze wiązania danych oparte na modelu EDM. Programowania powierzchni obiektu EntityDataSource formantu jest podobny do innych kontrolki źródła danych w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzi modelu danych jednostki ADO.NET](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 LINQ do SQL jest mapowania relacyjnego obiektu (lub / M) implementację, która umożliwia modelu bazy danych programu SQL Server przy użyciu klasy .NET Framework. LINQ do SQL umożliwia zapytanie bazy danych za pomocą LINQ, jak również zaktualizować, Wstaw i usuwanie danych z go. LINQ do SQL obsługuje transakcje, widoków i procedur składowanych, zapewniając łatwy sposób na zintegrowanie sprawdzanie poprawności danych i reguł logiki biznesowej do modelu danych. Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) służy do modelowania klas jednostek i skojarzenia, które są oparte na obiektach w bazie danych. Aby uzyskać więcej informacji, zobacz [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>Usługi danych WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] wdraża usług danych w sieci Web lub w sieci intranet. Dane mają strukturę jako jednostki i relacje zgodnie ze specyfikacją modelu danych jednostki. Adresowane przez standardowego protokołu HTTP jest wdrożony w tym modelu danych. Aby uzyskać więcej informacji, zobacz [4.5 usługi danych WCF](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Nowości w programie ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
