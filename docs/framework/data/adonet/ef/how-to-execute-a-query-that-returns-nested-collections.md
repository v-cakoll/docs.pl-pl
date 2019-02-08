---
title: 'Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 466187bf340d8cc2088615ae942131658399d65f
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827100"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="0b812-102">Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="0b812-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="0b812-103">To pokazuje, jak uruchamiać polecenia względem modelu koncepcyjnego przy użyciu <xref:System.Data.EntityClient.EntityCommand> obiektu oraz jak pobierać wyniki zagnieżdżoną kolekcję przy użyciu <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="0b812-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="0b812-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="0b812-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="0b812-105">Dodaj [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b812-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0b812-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0b812-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="0b812-107">Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="0b812-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="0b812-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b812-108">Example</span></span>  
 <span data-ttu-id="0b812-109">A *zagnieżdżone kolekcji* jest kolekcją, która znajduje się wewnątrz innej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0b812-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="0b812-110">Poniższy kod pobiera kolekcję `Contacts` i kolekcje zagnieżdżone `SalesOrderHeaders` skojarzonych z każdym `Contact`.</span><span class="sxs-lookup"><span data-stu-id="0b812-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="0b812-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b812-111">See also</span></span>
- [<span data-ttu-id="0b812-112">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0b812-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
