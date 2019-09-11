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
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="32552-102">Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="32552-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="32552-103">Pokazano, jak wykonać polecenie względem modelu koncepcyjnego za pomocą <xref:System.Data.EntityClient.EntityCommand> obiektu i jak pobrać zagnieżdżone wyniki kolekcji przy <xref:System.Data.EntityClient.EntityDataReader>użyciu.</span><span class="sxs-lookup"><span data-stu-id="32552-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="32552-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="32552-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="32552-105">Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt tak, aby korzystał z Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="32552-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="32552-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="32552-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="32552-107">Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="32552-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="32552-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="32552-108">Example</span></span>  
 <span data-ttu-id="32552-109">*Kolekcja zagnieżdżona* to kolekcja znajdująca się w innej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="32552-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="32552-110">Poniższy kod pobiera kolekcję `Contacts` i zagnieżdżone `SalesOrderHeaders` kolekcje, które są skojarzone z każdym z nich `Contact`.</span><span class="sxs-lookup"><span data-stu-id="32552-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="32552-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32552-111">See also</span></span>

- [<span data-ttu-id="32552-112">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="32552-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
