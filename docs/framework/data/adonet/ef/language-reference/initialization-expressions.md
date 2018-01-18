---
title: "Wyrażenia inicjowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3fc3b4b2fdbec6c527f6240460a263f40e683177
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="initialization-expressions"></a><span data-ttu-id="6a6d3-102">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="6a6d3-102">Initialization Expressions</span></span>
<span data-ttu-id="6a6d3-103">Wyrażenia inicjowania inicjuje nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="6a6d3-104">Większość wyrażenia inicjowania są obsługiwane, tym większości nowych 3.0 C# i Visual Basic 9.0 inicjowania wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="6a6d3-105">Następujące typy mogą zainicjowany i zwrócony przez LINQ do jednostek kwerendy:</span><span class="sxs-lookup"><span data-stu-id="6a6d3-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="6a6d3-106">Kolekcja zero lub więcej obiektów typów jednostek lub dla projekcji typów złożonych, które są zdefiniowane w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="6a6d3-107">Typy CLR obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a6d3-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="6a6d3-108">Kolekcje wbudowane.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="6a6d3-109">Typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="6a6d3-110">Inicjowanie typu anonimowego pokazano w poniższym przykładzie w składni wyrażeń zapytania:</span><span class="sxs-lookup"><span data-stu-id="6a6d3-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="6a6d3-111">W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono inicjowania typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="6a6d3-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="6a6d3-112">Obsługiwane jest również inicjowania klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="6a6d3-113">Wzorzec inicjowania 3.0 C# i Visual Basic 9.0 jest obsługiwana i przyjęto założenie, że właściwość pobierającej i ustawiającej są symetryczne.</span><span class="sxs-lookup"><span data-stu-id="6a6d3-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="6a6d3-114">W poniższym przykładzie w składni wyrażeń zapytania przedstawiono niestandardowej klasy inicjowany w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="6a6d3-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="6a6d3-115">W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono niestandardowej klasy inicjowany w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="6a6d3-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="6a6d3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a6d3-116">See Also</span></span>  
 [<span data-ttu-id="6a6d3-117">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="6a6d3-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
