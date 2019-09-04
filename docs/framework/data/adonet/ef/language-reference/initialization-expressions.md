---
title: Wyrażenia inicjowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 109be8ef2bf41326fcab5896ecdc359859683345
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250684"
---
# <a name="initialization-expressions"></a><span data-ttu-id="fca23-102">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="fca23-102">Initialization Expressions</span></span>
<span data-ttu-id="fca23-103">Wyrażenie inicjowania inicjuje nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="fca23-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="fca23-104">Obsługiwane są większość wyrażeń inicjujących, w tym C# większość nowych wyrażeń inicjacji 3,0 i Visual Basic 9,0.</span><span class="sxs-lookup"><span data-stu-id="fca23-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="fca23-105">Następujące typy można zainicjować i zwrócić przez zapytanie LINQ to Entities:</span><span class="sxs-lookup"><span data-stu-id="fca23-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="fca23-106">Kolekcja obiektów jednostek typu "zero" lub "rzutowanie typów złożonych", które są zdefiniowane w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="fca23-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="fca23-107">Typy CLR obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fca23-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="fca23-108">Kolekcje wbudowane.</span><span class="sxs-lookup"><span data-stu-id="fca23-108">Inline collections.</span></span>  
  
- <span data-ttu-id="fca23-109">Typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="fca23-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="fca23-110">Inicjalizacja typu anonimowego jest pokazana w poniższym przykładzie w składni wyrażenia zapytania:</span><span class="sxs-lookup"><span data-stu-id="fca23-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="fca23-111">W poniższym przykładzie w składni zapytania opartej na metodzie są wyświetlane anonimowe inicjalizacje typu:</span><span class="sxs-lookup"><span data-stu-id="fca23-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="fca23-112">Inicjowanie klasy zdefiniowanej przez użytkownika również jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fca23-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="fca23-113">Wzorzec C# inicjalizacji 3,0 i Visual Basic 9,0 jest obsługiwany i zakłada, że metody pobierającej i ustawiającej właściwości są symetryczne.</span><span class="sxs-lookup"><span data-stu-id="fca23-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="fca23-114">Poniższy przykład w składni wyrażenia zapytania pokazuje klasę niestandardową, która jest inicjowana w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="fca23-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="fca23-115">Poniższy przykład w składni zapytania opartej na metodzie przedstawia klasę niestandardową, która jest inicjowana w zapytaniu:</span><span class="sxs-lookup"><span data-stu-id="fca23-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="fca23-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fca23-116">See also</span></span>

- [<span data-ttu-id="fca23-117">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="fca23-117">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
