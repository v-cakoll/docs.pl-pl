---
title: 'Instrukcje: Wykonywanie zapytania SQL sparametryzowanej jednostki przy użyciu EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: a9b4069004cc48fa05efa29b4467aa1dca47fb29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610100"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="5cdf0-102">Instrukcje: Wykonywanie zapytania SQL sparametryzowanej jednostki przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="5cdf0-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="5cdf0-103">W tym temacie przedstawiono sposób wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] kwerendę, która ma następujące parametry przy użyciu <xref:System.Data.EntityClient.EntityCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cdf0-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="5cdf0-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="5cdf0-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="5cdf0-105">Dodaj [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cdf0-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="5cdf0-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="5cdf0-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="5cdf0-107">Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="5cdf0-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="5cdf0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cdf0-108">Example</span></span>  
 <span data-ttu-id="5cdf0-109">Poniższy przykład pokazuje, jak utworzyć ciąg zapytania z dwoma parametrami.</span><span class="sxs-lookup"><span data-stu-id="5cdf0-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="5cdf0-110">Następnie tworzy <xref:System.Data.EntityClient.EntityCommand>, dodaje dwa parametry <xref:System.Data.EntityClient.EntityParameter> kolekcję, która <xref:System.Data.EntityClient.EntityCommand>i iteruje po kolekcji `Contact` elementów.</span><span class="sxs-lookup"><span data-stu-id="5cdf0-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="5cdf0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cdf0-111">See also</span></span>
- [<span data-ttu-id="5cdf0-112">Instrukcje: Wykonaj zapytanie parametryczne</span><span class="sxs-lookup"><span data-stu-id="5cdf0-112">How to: Execute a Parameterized Query</span></span>](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)
- [<span data-ttu-id="5cdf0-113">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="5cdf0-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
