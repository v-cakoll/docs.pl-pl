---
title: 'Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 87bd7124d476ef39553db3ceaca206e44db8e5e9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854621"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a>Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone
Pokazano, jak wykonać polecenie względem modelu koncepcyjnego za pomocą <xref:System.Data.EntityClient.EntityCommand> obiektu i jak pobrać zagnieżdżone wyniki kolekcji przy <xref:System.Data.EntityClient.EntityDataReader>użyciu.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1. Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt tak, aby korzystał z Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Przykład  
 *Kolekcja zagnieżdżona* to kolekcja znajdująca się w innej kolekcji. Poniższy kod pobiera kolekcję `Contacts` i zagnieżdżone `SalesOrderHeaders` kolekcje, które są skojarzone z każdym z nich `Contact`.  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a>Zobacz także

- [Dostawca EntityClient dla programu Entity Framework](entityclient-provider-for-the-entity-framework.md)
