---
title: Dostawca EntityClient dla programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 70cc5a9aaa22cc563c910f9d250ad4565e34a135
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251601"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Dostawca EntityClient dla programu Entity Framework
Dostawca EntityClient jest dostawcą danych używanym przez aplikacje Entity Framework do uzyskiwania dostępu do danych opisanych w modelu koncepcyjnym. Aby uzyskać informacje o modelach koncepcyjnych, zobacz [modelowanie i mapowanie](modeling-and-mapping.md). EntityClient używa innych dostawców danych .NET Framework, aby uzyskać dostęp do źródła danych. Na przykład EntityClient używa Dostawca danych .NET Framework dla SQL Server (SqlClient) podczas uzyskiwania dostępu do bazy danych SQL Server. Aby uzyskać informacje na temat dostawcy SqlClient, zobacz temat [SqlClient dla Entity Framework](sqlclient-for-the-entity-framework.md). Dostawca EntityClient jest zaimplementowany w <xref:System.Data.EntityClient> przestrzeni nazw.  
  
## <a name="managing-connections"></a>Zarządzanie połączeniami  
 Kompilacje na podstawie ADO.NET dostawców danych specyficznych dla magazynu przez <xref:System.Data.EntityClient.EntityConnection> udostępnienie dostawcy danych i relacyjnej bazy danych. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Aby skonstruować <xref:System.Data.EntityClient.EntityConnection> obiekt, należy odwołać się do zestawu metadanych zawierającego wymagane modele i mapowania, a także nazwę dostawcy danych specyficzną dla magazynu i parametry połączenia. Po zakończeniu <xref:System.Data.EntityClient.EntityConnection> będzie można uzyskać dostęp do jednostek za pośrednictwem klas generowanych na podstawie modelu koncepcyjnego.  
  
 Możesz określić parametry połączenia w pliku App. config.  
  
 <xref:System.Data.EntityClient> Zawiera<xref:System.Data.EntityClient.EntityConnectionStringBuilder> również klasę. Ta klasa umożliwia deweloperom Programistyczne tworzenie składni parametrów połączenia oraz analizowanie i ponowne kompilowanie istniejących parametrów połączenia przy użyciu właściwości i metod klasy. Aby uzyskać więcej informacji, zobacz [jak: Kompiluj parametry](how-to-build-an-entityconnection-connection-string.md)połączenia usługi EntityConnection.  
  
## <a name="creating-queries"></a>Tworzenie zapytań  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Język to niezależny od magazynu dialekt SQL, który działa bezpośrednio ze schematami jednostek koncepcyjnych i obsługuje Entity Data Model pojęć, takich jak dziedziczenie i relacje. Klasa jest używana do [!INCLUDE[esql](../../../../../includes/esql-md.md)] wykonywania polecenia względem modelu jednostki. <xref:System.Data.EntityClient.EntityCommand> Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiektów można określić nazwę procedury składowanej lub tekst zapytania. Współpracuje z dostawcami danych specyficznymi dla magazynu w celu [!INCLUDE[esql](../../../../../includes/esql-md.md)] przetłumaczenia ogólnego na zapytania specyficzne dla magazynu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Aby uzyskać więcej informacji na [!INCLUDE[esql](../../../../../includes/esql-md.md)] temat pisania zapytań, zobacz [Entity SQL Language](./language-reference/entity-sql-language.md).  
  
 Poniższy przykład tworzy <xref:System.Data.EntityClient.EntityCommand> obiekt i [!INCLUDE[esql](../../../../../includes/esql-md.md)] przypisuje tekst zapytania do jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości. To [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytanie żąda produktów uporządkowanych według ceny listy z modelu koncepcyjnego. Poniższy kod nie zawiera żadnych informacji o modelu magazynu.  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>Wykonywanie zapytań  
 Gdy zapytanie jest wykonywane, jest analizowane i konwertowane do drzewa poleceń w postaci kanonicznej. Wszystkie kolejne operacje przetwarzania są wykonywane w drzewie poleceń. Drzewo poleceń jest sposobem komunikacji między <xref:System.Data.EntityClient> programem a podstawowym dostawcą danych .NET Framework, <xref:System.Data.SqlClient>na przykład.  
  
 <xref:System.Data.EntityClient.EntityDataReader> Prezentuje wyniki<xref:System.Data.EntityClient.EntityCommand> wykonywania względem modelu koncepcyjnego. Aby wykonać polecenie <xref:System.Data.EntityClient.EntityDataReader>, które zwraca wywołanie <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> Implementuje<xref:System.Data.IExtendedDataRecord> , aby opisać bogate wyniki strukturalne.  
  
## <a name="managing-transactions"></a>Zarządzanie transakcjami  
 W Entity Framework istnieją dwa sposoby używania transakcji: automatyczne i jawne. Transakcje automatyczne używają <xref:System.Transactions> przestrzeni nazw, a transakcje jawne <xref:System.Data.EntityClient.EntityTransaction> używają klasy.  
  
 Aby zaktualizować dane, które są udostępniane za pomocą modelu koncepcyjnego [, zobacz How to: Zarządzanie transakcjami w](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100))Entity Framework.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie parametrów połączenia usługi EntityConnection](how-to-build-an-entityconnection-connection-string.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki typu pierwotnego](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające wyniki StructuralType](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające wyniki RefType](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające typy złożone](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające kolekcje zagnieżdżone](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Instrukcje: Wykonywanie zapytania Entity SQL sparametryzowanego przy użyciu EntityCommand](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Instrukcje: Wykonaj sparametryzowane procedury składowane za pomocą EntityCommand](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Instrukcje: Wykonywanie zapytania polimorficznego](how-to-execute-a-polymorphic-query.md)  
  
 [Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigacji](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Program Entity Framework na platformie ADO.NET](index.md)
- [Dokumentacja języka](./language-reference/index.md)
