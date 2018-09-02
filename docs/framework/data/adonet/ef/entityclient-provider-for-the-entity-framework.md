---
title: Dostawca EntityClient dla programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 1bafdc250c7edc009352d668e8ee7962a86fe8bf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395094"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Dostawca EntityClient dla programu Entity Framework
Dostawca EntityClient jest dostawcy danych używanych przez aplikacje platformy Entity Framework na dostęp do danych opisanych w modelu koncepcyjnym. Aby uzyskać informacje o modelach koncepcyjnych, zobacz [modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). Dostawca EntityClient używa innego dostawcy danych .NET Framework, dostępu do źródła danych. Na przykład dostawca EntityClient używa dostawcy danych .NET Framework dla programu SQL Server (SqlClient) podczas uzyskiwania dostępu do bazy danych programu SQL Server. Aby uzyskać informacje o dostawcy SqlClient, zobacz [SqlClient programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). Dostawca EntityClient jest zaimplementowana w <xref:System.Data.EntityClient> przestrzeni nazw.  
  
## <a name="managing-connections"></a>Zarządzanie połączeniami  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Opartą na specyficznych dla magazynowania [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy danych, zapewniając <xref:System.Data.EntityClient.EntityConnection> źródłowy dostawca danych i relacyjnej bazy danych. Do konstruowania <xref:System.Data.EntityClient.EntityConnection> obiektu musi odwoływać się do zestawu metadanych, który zawiera niezbędne modeli i mapowanie, a także dane specyficzne dla magazynu dostawcy nazwę i parametry połączenia. Po <xref:System.Data.EntityClient.EntityConnection> jest w miejscu, jednostek jest możliwy za pośrednictwem klas wygenerowanych na podstawie modelu koncepcyjnego.  
  
 Można określić parametry połączenia w pliku app.config.  
  
 <xref:System.Data.EntityClient> Obejmuje również <xref:System.Data.EntityClient.EntityConnectionStringBuilder> klasy. Ta klasa umożliwia deweloperom programowo utworzyć parametry połączenia poprawnych składniowo, analizy i Odbuduj istniejących parametrów połączenia, przy użyciu właściwości i metod klasy. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Tworzenie zapytań  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Język jest dialekt niezależny od magazynu SQL, który współpracuje bezpośrednio ze schematami koncepcyjnymi encji i obsługuje model Entity Data Model pojęć, takich jak dziedziczenie i relacje. <xref:System.Data.EntityClient.EntityCommand> Klasa jest używana do wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] polecenia względem modelu jednostki. Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiektów, można określić nazwę procedury składowanej lub tekst zapytania. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Pracuje z dostawcami magazynu danych do translacji ogólny [!INCLUDE[esql](../../../../../includes/esql-md.md)] do zapytań specyficznych dla magazynowania. Aby uzyskać więcej informacji na temat pisania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytań, zobacz [jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 Poniższy przykład tworzy <xref:System.Data.EntityClient.EntityCommand> obiektu i przypisuje [!INCLUDE[esql](../../../../../includes/esql-md.md)] tekst do zapytania jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości. To [!INCLUDE[esql](../../../../../includes/esql-md.md)] produktów uporządkowane według ceny z modelu koncepcyjnego liczba żądań zapytań. Poniższy kod nie ma informacji o modelu przechowywania ogóle.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"``SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>Wykonywanie zapytań  
 Po wykonaniu zapytania jest analizowany i przekształcone w drzewie poleceń w postaci kanonicznej. Wszystkie kolejne przetwarzanie jest realizowane na drzewo poleceń. Drzewo poleceń jest oznacza, że komunikacji między <xref:System.Data.EntityClient> i podstawowych [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] dostawcy danych, takich jak <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> Przedstawia wyniki wykonania <xref:System.Data.EntityClient.EntityCommand> względem modelu koncepcyjnego. Do wykonania polecenia, które zwraca <xref:System.Data.EntityClient.EntityDataReader>, wywołaj <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> Implementuje <xref:System.Data.IExtendedDataRecord> do opisania rozbudowane ze strukturą wyników.  
  
## <a name="managing-transactions"></a>Zarządzanie transakcjami  
 W ramach jednostki, istnieją dwa sposoby, aby móc używać transakcji: automatyczne i jawne. Użyj automatycznego transakcji <xref:System.Transactions> przestrzeni nazw i jawnego transakcji używają <xref:System.Data.EntityClient.EntityTransaction> klasy.  
  
 Aby zaktualizować dane, która jest dostępna za pośrednictwem modelu koncepcyjnego; zobacz [porady: Zarządzanie transakcji platformy Entity Framework](https://msdn.microsoft.com/library/4a55eb7f-f826-4a48-9df1-aebe2352ebef).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki RefType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca typy złożone](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej jednostki przy użyciu EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej procedury składowanej przy użyciu EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Instrukcje: Wykonywanie zapytania polimorficznego](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzania połączeniami i transakcji](https://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [Program Entity Framework na platformie ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dokumentacja języka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
