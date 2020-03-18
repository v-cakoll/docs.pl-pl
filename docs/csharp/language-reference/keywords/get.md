---
title: get - C# Odwołanie
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 61d8c02aaf13f43ff8ea17c1e868ea9fd52893c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173630"
---
# <a name="get-c-reference"></a><span data-ttu-id="f9d97-102">get (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f9d97-102">get (C# Reference)</span></span>

<span data-ttu-id="f9d97-103">Słowo `get` kluczowe definiuje metodę *akcesora* we właściwości lub indeksatora, który zwraca wartość właściwości lub elementu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="f9d97-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="f9d97-104">Aby uzyskać więcej informacji, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [Właściwości autoimplementowane](../../programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9d97-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="f9d97-105">W poniższym przykładzie `get` zdefiniowano zarówno a, jak `set` i akcesor dla właściwości o nazwie `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="f9d97-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="f9d97-106">Używa pola prywatnego `_seconds` o nazwie do tyłu wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9d97-106">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="f9d97-107">Często `get` akcesor składa się z pojedynczej instrukcji, która zwraca wartość, jak to miało miejsce w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9d97-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="f9d97-108">Począwszy od języka C# 7.0, można zaimplementować `get` akcesor jako element członkowski zabudowany wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="f9d97-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="f9d97-109">Poniższy przykład implementuje `get` zarówno `set` akcesor jako elementy członkowskie zabudowane wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="f9d97-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="f9d97-110">W prostych przypadkach, w `get` których `set` właściwość i akcesory wykonać nie inną operację niż ustawienie lub pobieranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi kompilatora C# dla właściwości auto implementowane.</span><span class="sxs-lookup"><span data-stu-id="f9d97-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="f9d97-111">Poniższy przykład implementuje `Hours` jako właściwości auto-implemented.</span><span class="sxs-lookup"><span data-stu-id="f9d97-111">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f9d97-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f9d97-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9d97-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9d97-113">See also</span></span>

- [<span data-ttu-id="f9d97-114">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="f9d97-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f9d97-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f9d97-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f9d97-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f9d97-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="f9d97-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f9d97-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
