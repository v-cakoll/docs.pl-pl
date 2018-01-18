---
title: Dostawca EntityClient Entity Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eaccace7a333903e236107a72dbc17e19dc8d48a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Dostawca EntityClient Entity Framework
Dostawca EntityClient jest dostawcą danych używane przez aplikacje programu Entity Framework dostępu do danych opisanego w modelu koncepcyjnym. Aby uzyskać informacje o modelach koncepcyjnych, zobacz [modelowania i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). Dostawca EntityClient używa inni dostawcy danych .NET Framework do dostępu do źródła danych. Na przykład EntityClient używa dostawcy danych programu .NET Framework dla programu SQL Server (SqlClient) podczas uzyskiwania dostępu do bazy danych programu SQL Server. Informacje o dostawcy SqlClient znajdują się w temacie [SqlClient Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). Dostawca EntityClient jest zaimplementowana w <xref:System.Data.EntityClient> przestrzeni nazw.  
  
## <a name="managing-connections"></a>Zarządzanie połączeniami  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kompilacje ponad pamięci masowej [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy danych, zapewniając <xref:System.Data.EntityClient.EntityConnection> źródłowy dostawca danych i relacyjnej bazy danych. Aby utworzyć <xref:System.Data.EntityClient.EntityConnection> obiektu, trzeba odwoływać zestawu metadanych, które zawiera niezbędne modeli i mapowania, a także ciąg połączenia i nazwę dostawcy magazynu danych. Po <xref:System.Data.EntityClient.EntityConnection> jest na miejscu, jednostek jest możliwy za pośrednictwem klasy wygenerowane na podstawie modelu koncepcyjnego.  
  
 Można określić parametry połączenia w pliku app.config.  
  
 <xref:System.Data.EntityClient> Obejmuje również <xref:System.Data.EntityClient.EntityConnectionStringBuilder> klasy. Ta klasa umożliwia deweloperom programowe tworzenie ciągów połączenia poprawna składniowo i przeanalizować i skompiluj ponownie istniejących parametrów połączenia, przy użyciu właściwości i metody klasy. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Tworzenie zapytań  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Język jest dialekt niezależne od magazynu programu SQL Server, które współpracuje bezpośrednio z Schematy koncepcyjne jednostki i obsługuje modelu Entity Data Model pojęcia, takie jak dziedziczenia i relacje. <xref:System.Data.EntityClient.EntityCommand> Klasa jest używana do wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] polecenia w odniesieniu do modelu jednostki. Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiekty, można określić nazwę procedury składowanej lub tekst zapytania. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Współpracuje z dostawców magazynu danych do tłumaczenia ogólnego [!INCLUDE[esql](../../../../../includes/esql-md.md)] do specyficznych dla magazynu zapytań. Aby uzyskać więcej informacji na temat pisania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytań, zobacz [języka SQL jednostki](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 Poniższy przykład tworzy <xref:System.Data.EntityClient.EntityCommand> obiektów i przypisuje [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania tekst do jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości. To [!INCLUDE[esql](../../../../../includes/esql-md.md)] produktów uporządkowanych według cennika z modelu koncepcyjnego liczba żądań zapytań. Następujący kod nie ma informacji o modelu magazynu w ogóle.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"``SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>Wykonywanie zapytań  
 Po wykonaniu zapytania jest przeanalizować i przekonwertować na drzewa poleceń w postaci kanonicznej. Wszystkie kolejne przetwarzanie jest realizowane na drzewo poleceń. Drzewo poleceń jest sposób komunikacji między <xref:System.Data.EntityClient> i podstawowych [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] dostawcy danych, takich jak <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> Przedstawia wyniki wykonania <xref:System.Data.EntityClient.EntityCommand> względem modelu koncepcyjnego. Do wykonania polecenia, która zwraca <xref:System.Data.EntityClient.EntityDataReader>, wywołaj <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> Implementuje <xref:System.Data.IExtendedDataRecord> do opisywania sformatowanego strukturę wyników.  
  
## <a name="managing-transactions"></a>Zarządzanie transakcji  
 W ramach jednostki, istnieją dwa sposoby używania transakcji: jawne i automatyczne. Użyj automatycznego transakcji <xref:System.Transactions> przestrzeni nazw i jawnych transakcji używają <xref:System.Data.EntityClient.EntityTransaction> klasy.  
  
 Aby zaktualizować dane widoczne poprzez model koncepcyjny; zobacz [porady: Zarządzanie transakcji w ramach jednostki](http://msdn.microsoft.com/en-us/4a55eb7f-f826-4a48-9df1-aebe2352ebef).  
  
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
 [Zarządzanie połączeniami i transakcji](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [Program Entity Framework na platformie ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dokumentacja języka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
