---
title: 'Instrukcje: Wykonywanie zapytania, które zwraca wyniki RefType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: 1a7b5433ac514d22433dfb0bbf572a60854c1037
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251473"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a>Instrukcje: Wykonywanie zapytania, które zwraca wyniki RefType
W tym temacie pokazano, jak wykonać polecenie względem modelu koncepcyjnego za pomocą <xref:System.Data.EntityClient.EntityCommand> obiektu i jak <xref:System.Data.Metadata.Edm.RefType> pobrać wyniki przy użyciu <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1. Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje zapytanie zwracające <xref:System.Data.Metadata.Edm.RefType> wyniki. W przypadku przekazania następującego zapytania jako argumentu do `ExecuteRefTypeQuery` funkcji funkcja zwraca odwołanie do jednostki:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 W przypadku przekazania sparametryzowanych zapytań, takich jak następujące, Dodaj <xref:System.Data.EntityClient.EntityParameter> obiekty <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> do właściwości <xref:System.Data.EntityClient.EntityCommand> obiektu.  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](./language-reference/entity-sql-reference.md)
- [Dostawca EntityClient dla programu Entity Framework](entityclient-provider-for-the-entity-framework.md)
