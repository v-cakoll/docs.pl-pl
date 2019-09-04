---
title: 'Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej jednostki przy użyciu EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: addda1a18ab325971b823d0131338a7bb824ad5c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251532"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="ddeea-102">Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej jednostki przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="ddeea-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="ddeea-103">W tym temacie pokazano, jak wykonać [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytanie, które zawiera parametry za <xref:System.Data.EntityClient.EntityCommand> pomocą obiektu.</span><span class="sxs-lookup"><span data-stu-id="ddeea-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ddeea-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="ddeea-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="ddeea-105">Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddeea-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="ddeea-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ddeea-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="ddeea-107">Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="ddeea-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="ddeea-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddeea-108">Example</span></span>  
 <span data-ttu-id="ddeea-109">Poniższy przykład pokazuje, jak utworzyć ciąg zapytania z dwoma parametrami.</span><span class="sxs-lookup"><span data-stu-id="ddeea-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="ddeea-110">Następnie tworzy <xref:System.Data.EntityClient.EntityCommand>, dodaje dwa parametry <xref:System.Data.EntityClient.EntityParameter> do kolekcji <xref:System.Data.EntityClient.EntityCommand>i wykonuje iterację kolekcji `Contact` elementów.</span><span class="sxs-lookup"><span data-stu-id="ddeea-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="ddeea-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddeea-111">See also</span></span>

- <span data-ttu-id="ddeea-112">[Instrukcje: Wykonaj zapytanie parametryczne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ddeea-112">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="ddeea-113">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="ddeea-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
