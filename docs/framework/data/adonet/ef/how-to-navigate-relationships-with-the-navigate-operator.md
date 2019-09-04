---
title: 'Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: c8c23e00112859ffa9949d268c3263f73d3a714f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251432"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="1e39c-102">Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania</span><span class="sxs-lookup"><span data-stu-id="1e39c-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="1e39c-103">W tym temacie pokazano, jak wykonać polecenie względem modelu koncepcyjnego za pomocą <xref:System.Data.EntityClient.EntityCommand> obiektu i jak <xref:System.Data.Metadata.Edm.RefType> pobrać wyniki przy użyciu <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="1e39c-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="1e39c-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="1e39c-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="1e39c-105">Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e39c-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="1e39c-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="1e39c-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="1e39c-107">Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="1e39c-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="1e39c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e39c-108">Example</span></span>  
 <span data-ttu-id="1e39c-109">Poniższy przykład pokazuje, jak nawigować w [!INCLUDE[esql](../../../../../includes/esql-md.md)] relacji za pomocą operatora [nawigacji](./language-reference/navigate-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="1e39c-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](./language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="1e39c-110">`Navigate` Operator przyjmuje następujące parametry: wystąpienie jednostki, typ relacji, koniec relacji i początek relacji...</span><span class="sxs-lookup"><span data-stu-id="1e39c-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="1e39c-111">Opcjonalnie można przekazać tylko wystąpienie jednostki i typ relacji do `Navigate` operatora.</span><span class="sxs-lookup"><span data-stu-id="1e39c-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="1e39c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e39c-112">See also</span></span>

- [<span data-ttu-id="1e39c-113">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="1e39c-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="1e39c-114">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="1e39c-114">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
