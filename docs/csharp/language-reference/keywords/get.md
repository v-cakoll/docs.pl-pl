---
title: get (odwołanie w C#)
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 182f7164ad929232c185903a3dbf024a2e5d22a7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131315"
---
# <a name="get-c-reference"></a><span data-ttu-id="a2381-102">get (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a2381-102">get (C# Reference)</span></span>

<span data-ttu-id="a2381-103">`get` — Słowo kluczowe definiuje *akcesor* metoda we właściwości lub indeksatora, który zwraca wartość właściwości lub elementu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="a2381-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="a2381-104">Aby uzyskać więcej informacji, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="a2381-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="a2381-105">W poniższym przykładzie zdefiniowano zarówno `get` i `set` akcesora dla właściwości o nazwie `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="a2381-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="a2381-106">Używa prywatnego pola o nazwie `_seconds` kopii wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2381-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="a2381-107">Często `get` dostępu składa się z pojedynczej instrukcji, która nie zwraca wartości, tak jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a2381-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="a2381-108">Począwszy od języka C# 7.0, można zaimplementować `get` dostępu jako element członkowski wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="a2381-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="a2381-109">Poniższy przykład implementuje interfejsy `get` i `set` dostępu jako elementy członkowskie z wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="a2381-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="a2381-110">Dla prostych sytuacjach, w których właściwość `get` i `set` Akcesory wykonać żadna inna operacja niż ustawienie lub odczytywania wartości pola prywatnego zapasowy, możesz korzystać z zalet Obsługa właściwości zaimplementowane automatycznie w kompilatorze języka C#.</span><span class="sxs-lookup"><span data-stu-id="a2381-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="a2381-111">Poniższy przykład implementuje `Hours` jako automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2381-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a2381-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a2381-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a2381-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2381-113">See Also</span></span>

- [<span data-ttu-id="a2381-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a2381-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a2381-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a2381-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a2381-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a2381-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="a2381-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a2381-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
