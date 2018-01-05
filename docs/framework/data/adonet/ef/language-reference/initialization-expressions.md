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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f04d487f032bb8a5f36f3bd7d77ee3e7be480e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-expressions"></a><span data-ttu-id="33d4b-102">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="33d4b-102">Initialization Expressions</span></span>
<span data-ttu-id="33d4b-103">Wyrażenia inicjowania inicjuje nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="33d4b-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="33d4b-104">Większość wyrażenia inicjowania są obsługiwane, tym większości nowych 3.0 C# i Visual Basic 9.0 inicjowania wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="33d4b-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="33d4b-105">Następujące typy mogą zainicjowany i zwrócony przez LINQ do jednostek kwerendy:</span><span class="sxs-lookup"><span data-stu-id="33d4b-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="33d4b-106">Kolekcja zero lub więcej obiektów typów jednostek lub dla projekcji typów złożonych, które są zdefiniowane w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="33d4b-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="33d4b-107">Typy CLR obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33d4b-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="33d4b-108">Kolekcje wbudowane.</span><span class="sxs-lookup"><span data-stu-id="33d4b-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="33d4b-109">Typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="33d4b-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="33d4b-110">Inicjowanie typu anonimowego pokazano w poniższym przykładzie w składni wyrażeń zapytania:</span><span class="sxs-lookup"><span data-stu-id="33d4b-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="33d4b-111">W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono inicjowania typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="33d4b-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="33d4b-112">Obsługiwane jest również inicjowania klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33d4b-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="33d4b-113">Wzorzec inicjowania 3.0 C# i Visual Basic 9.0 jest obsługiwana i przyjęto założenie, że właściwość pobierającej i ustawiającej są symetryczne.</span><span class="sxs-lookup"><span data-stu-id="33d4b-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="33d4b-114">W poniższym przykładzie w składni wyrażeń zapytania przedstawiono niestandardowej klasy inicjowany w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="33d4b-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="33d4b-115">W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono niestandardowej klasy inicjowany w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="33d4b-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="33d4b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33d4b-116">See Also</span></span>  
 [<span data-ttu-id="33d4b-117">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="33d4b-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
