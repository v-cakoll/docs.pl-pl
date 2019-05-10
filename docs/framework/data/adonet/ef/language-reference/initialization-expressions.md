---
title: Wyrażenia inicjowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 78bafcad0a0f34c74ea58f107621ad145c1b405b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631530"
---
# <a name="initialization-expressions"></a><span data-ttu-id="7ec6d-102">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="7ec6d-102">Initialization Expressions</span></span>
<span data-ttu-id="7ec6d-103">Wyrażenia inicjowania inicjuje nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="7ec6d-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="7ec6d-104">Większość wyrażenia inicjowania są obsługiwane, w tym najbardziej nowe C# 3.0 i wyrażenia inicjowania 9.0 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ec6d-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="7ec6d-105">Następujące typy można zainicjowany i zwrócony przez LINQ zapytanie jednostki:</span><span class="sxs-lookup"><span data-stu-id="7ec6d-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="7ec6d-106">Kolekcja zero lub więcej obiektów typów jednostek lub projekcji złożonych typów, które są zdefiniowane w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="7ec6d-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="7ec6d-107">Typy CLR obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ec6d-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="7ec6d-108">Kolekcje wbudowane.</span><span class="sxs-lookup"><span data-stu-id="7ec6d-108">Inline collections.</span></span>  
  
- <span data-ttu-id="7ec6d-109">Typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="7ec6d-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="7ec6d-110">Inicjalizacja typu anonimowego pokazano w poniższym przykładzie w składni wyrażenia zapytania:</span><span class="sxs-lookup"><span data-stu-id="7ec6d-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="7ec6d-111">Poniższy przykład przy użyciu składni zapytania oparte na metodzie pokazuje inicjowania typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="7ec6d-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="7ec6d-112">Obsługiwane jest również inicjowanie klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7ec6d-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="7ec6d-113">C# 3.0 i Visual Basic 9.0 wzorzec inicjowania jest obsługiwana i przyjęto założenie, że pobierającej i ustawiającej są symetryczne.</span><span class="sxs-lookup"><span data-stu-id="7ec6d-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="7ec6d-114">W składni wyrażenia zapytania poniższy kod przedstawia klasę niestandardową, która jest inicjowany w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="7ec6d-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="7ec6d-115">Poniższy przykład przy użyciu składni zapytania oparte na metodzie pokazuje klasę niestandardową, która jest inicjowany w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="7ec6d-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7ec6d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ec6d-116">See also</span></span>

- [<span data-ttu-id="7ec6d-117">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7ec6d-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
