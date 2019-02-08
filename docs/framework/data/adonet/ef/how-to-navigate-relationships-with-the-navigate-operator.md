---
title: 'Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: 04114a0dd855d6543b238111d745eb386d4d2988
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826515"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="53aa7-102">Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania</span><span class="sxs-lookup"><span data-stu-id="53aa7-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="53aa7-103">W tym temacie pokazano, jak uruchamiać polecenia względem modelu koncepcyjnego przy użyciu <xref:System.Data.EntityClient.EntityCommand> obiektu oraz jak pobierać <xref:System.Data.Metadata.Edm.RefType> wyniki za pomocą <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="53aa7-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="53aa7-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="53aa7-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="53aa7-105">Dodaj [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53aa7-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="53aa7-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="53aa7-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="53aa7-107">Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="53aa7-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="53aa7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="53aa7-108">Example</span></span>  
 <span data-ttu-id="53aa7-109">Poniższy przykład pokazuje, jak nawigowanie po relacjach w [!INCLUDE[esql](../../../../../includes/esql-md.md)] przy użyciu [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="53aa7-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="53aa7-110">`Navigate` Operator przyjmuje następujące parametry: wystąpienie jednostki, typ relacji, relacji, początkiem i końcem relacji.</span><span class="sxs-lookup"><span data-stu-id="53aa7-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="53aa7-111">Opcjonalnie możesz przekazać tylko wystąpienie jednostki oraz typ relacji do `Navigate` operatora.</span><span class="sxs-lookup"><span data-stu-id="53aa7-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="53aa7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53aa7-112">See also</span></span>
- [<span data-ttu-id="53aa7-113">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="53aa7-113">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="53aa7-114">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="53aa7-114">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
