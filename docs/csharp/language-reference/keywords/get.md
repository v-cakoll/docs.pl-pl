---
title: get (odwołanie w C#)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3cdf639065ee5bf0cb9e920061557991c0a4b921
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="get-c-reference"></a><span data-ttu-id="d48f0-102">get (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d48f0-102">get (C# Reference)</span></span>

<span data-ttu-id="d48f0-103">`get` Definiuje — słowo kluczowe *akcesor* metody we właściwości lub indeksatora, który zwraca wartość właściwości lub indeksatora elementu.</span><span class="sxs-lookup"><span data-stu-id="d48f0-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="d48f0-104">Aby uzyskać więcej informacji, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [właściwości Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d48f0-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="d48f0-105">W poniższym przykładzie zdefiniowano zarówno `get` i `set` dostępu dla właściwości o nazwie `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="d48f0-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="d48f0-106">Używa prywatnego pole o nazwie `_seconds` kopii wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d48f0-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="d48f0-107">Często `get` dostępu składa się z jednej instrukcji, która nie zwraca wartości, tak jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d48f0-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="d48f0-108">Począwszy od wersji 7.0 C#, można zaimplementować `get` akcesor jako element członkowski zabudowanych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d48f0-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="d48f0-109">Poniższy przykład implementuje zarówno `get` i `set` akcesor jako członków zabudowanych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d48f0-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="d48f0-110">Proste przypadki, w którym właściwość `get` i `set` metod dostępu do wykonywania żadnych innych operacji niż ustawienie lub odczytywania wartości pola zapasowy prywatnej, można skorzystać z obsługi kompilatora C# dla właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d48f0-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="d48f0-111">Poniższy przykład implementuje `Hours` jako właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d48f0-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d48f0-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d48f0-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d48f0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d48f0-113">See Also</span></span>  
 [<span data-ttu-id="d48f0-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d48f0-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d48f0-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d48f0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 <span data-ttu-id="d48f0-116">[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md) [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="d48f0-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>
