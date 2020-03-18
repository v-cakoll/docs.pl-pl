---
title: set — słowo kluczowe — odwołanie do języka C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0b293709abe64a0a82d8575f6793a07ca6c9533b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173500"
---
# <a name="set-c-reference"></a><span data-ttu-id="da489-102">set (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="da489-102">set (C# Reference)</span></span>

<span data-ttu-id="da489-103">Słowo `set` kluczowe definiuje metodę *akcesora* we właściwości lub indeksatora, który przypisuje wartość do właściwości lub elementu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="da489-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="da489-104">Aby uzyskać więcej informacji i przykładów, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [Właściwości autoimplementowane](../../programming-guide/classes-and-structs/auto-implemented-properties.md)i [Indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="da489-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="da489-105">W poniższym przykładzie `get` zdefiniowano zarówno a, jak `set` i akcesor dla właściwości o nazwie `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="da489-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="da489-106">Używa pola prywatnego `_seconds` o nazwie do tyłu wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="da489-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="da489-107">Często `set` akcesor składa się z pojedynczej instrukcji, która przypisuje wartość, jak to miało miejsce w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="da489-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="da489-108">Począwszy od języka C# 7.0, można zaimplementować `set` akcesor jako element członkowski zabudowany wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="da489-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="da489-109">Poniższy przykład implementuje `get` zarówno `set` akcesorów jako elementy członkowskie zabudowane wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="da489-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="da489-110">W prostych przypadkach, w `get` których `set` właściwość i akcesory wykonać nie inną operację niż ustawienie lub pobieranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi kompilatora C# dla właściwości auto implementowane.</span><span class="sxs-lookup"><span data-stu-id="da489-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="da489-111">Poniższy przykład implementuje `Hours` jako właściwości auto-implemented.</span><span class="sxs-lookup"><span data-stu-id="da489-111">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="da489-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="da489-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="da489-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da489-113">See also</span></span>

- [<span data-ttu-id="da489-114">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="da489-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="da489-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="da489-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="da489-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="da489-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="da489-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="da489-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
