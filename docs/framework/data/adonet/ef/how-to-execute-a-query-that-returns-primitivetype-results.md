---
title: 'Instrukcje: Wykonywanie zapytania, które zwraca wyniki PrimitiveType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: 4805a9f959096b87e2ed3e35b02fbd8c04d45fbc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251484"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a>Instrukcje: Wykonywanie zapytania, które zwraca wyniki PrimitiveType
W tym temacie pokazano <xref:System.Data.EntityClient.EntityCommand>, jak wykonać polecenie względem modelu koncepcyjnego za pomocą i jak <xref:System.Data.Metadata.Edm.PrimitiveType> pobrać wyniki przy użyciu <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1. Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje zapytanie zwracające <xref:System.Data.Metadata.Edm.PrimitiveType> wynik. Jeśli następujące zapytanie zostanie przekazane jako argument do `ExecutePrimitiveTypeQuery` funkcji, funkcja wyświetla średnią cenę `Products`listy:  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 W <xref:System.Data.EntityClient.EntityParameter> przypadkuprzekazania<xref:System.Data.EntityClient.EntityCommand.Parameters%2A> sparametryzowanych zapytań, takich jak następujące, obiekty do właściwości obiektu.<xref:System.Data.EntityClient.EntityCommand>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](./language-reference/entity-sql-reference.md)
- [Dostawca EntityClient dla programu Entity Framework](entityclient-provider-for-the-entity-framework.md)
