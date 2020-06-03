---
title: Ustaw słowo kluczowe — odwołanie w C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: cdd84c824cc4dc93f4433f07e9978d22cba3f245
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795069"
---
# <a name="set-c-reference"></a><span data-ttu-id="28e64-102">set (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="28e64-102">set (C# Reference)</span></span>

<span data-ttu-id="28e64-103">`set`Słowo kluczowe definiuje metodę *dostępu* we właściwości lub indeksatora, która przypisuje wartość do właściwości lub elementu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="28e64-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="28e64-104">Aby uzyskać więcej informacji i przykładów, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zaimplementowane właściwości](../../programming-guide/classes-and-structs/auto-implemented-properties.md), i [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="28e64-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="28e64-105">W poniższym przykładzie zdefiniowano `get` `set` metodę dostępu a i dla właściwości o nazwie `Seconds` .</span><span class="sxs-lookup"><span data-stu-id="28e64-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="28e64-106">Używa pola prywatnego o nazwie `_seconds` do wstecz wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="28e64-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="28e64-107">Często `set` metoda dostępu składa się z pojedynczej instrukcji, która przypisuje wartość, tak jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="28e64-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="28e64-108">Począwszy od języka C# 7,0, można zaimplementować `set` metodę dostępu jako element członkowski będący w postaci wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="28e64-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="28e64-109">W poniższym przykładzie zaimplementowane są `get` i metody `set` dostępu jako elementy członkowskie, które są członkami wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="28e64-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="28e64-110">W przypadku prostych przypadków, w których właściwości `get` i metody `set` dostępu nie wykonują innej operacji niż ustawienie lub pobranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi kompilatora języka C# dla właściwości, które są implementowane.</span><span class="sxs-lookup"><span data-stu-id="28e64-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="28e64-111">Poniższy przykład implementuje `Hours` jako właściwość, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="28e64-111">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="28e64-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="28e64-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="28e64-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28e64-113">See also</span></span>

- [<span data-ttu-id="28e64-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="28e64-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="28e64-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="28e64-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="28e64-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="28e64-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="28e64-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="28e64-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
