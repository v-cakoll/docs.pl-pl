---
title: set (odwołanie w C#)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b095520326c439601caa8fefa458dda75ba603e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="set-c-reference"></a><span data-ttu-id="d24b2-102">set (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d24b2-102">set (C# Reference)</span></span>
<span data-ttu-id="d24b2-103">`set` Definiuje — słowo kluczowe *akcesor* metody we właściwości lub indeksatora, która przypisuje wartość do właściwości lub indeksatora elementu.</span><span class="sxs-lookup"><span data-stu-id="d24b2-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="d24b2-104">Aby uzyskać dodatkowe informacje i przykłady, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [właściwości Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), i [indeksatory](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d24b2-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="d24b2-105">W poniższym przykładzie zdefiniowano zarówno `get` i `set` dostępu dla właściwości o nazwie `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="d24b2-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="d24b2-106">Używa prywatnego pole o nazwie `_seconds` kopii wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d24b2-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="d24b2-107">Często `set` dostępu składa się z jednej instrukcji, która nie zwraca wartości, tak jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d24b2-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="d24b2-108">Począwszy od wersji 7.0 C#, można zaimplementować `set` akcesor jako element członkowski zabudowanych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d24b2-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="d24b2-109">Poniższy przykład implementuje zarówno `get` i `set` metody dostępu jako członków zabudowanych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d24b2-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="d24b2-110">Proste przypadki, w którym właściwość `get` i `set` metod dostępu do wykonywania żadnych innych operacji niż ustawienie lub odczytywania wartości pola zapasowy prywatnej, można skorzystać z obsługi kompilatora C# dla właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d24b2-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="d24b2-111">Poniższy przykład implementuje `Hours` jako właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d24b2-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="d24b2-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d24b2-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d24b2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d24b2-113">See Also</span></span>  
 [<span data-ttu-id="d24b2-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d24b2-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d24b2-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d24b2-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d24b2-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d24b2-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d24b2-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d24b2-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
