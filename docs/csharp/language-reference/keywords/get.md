---
title: get- C# Reference
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 783814a575e95fc9deb5c9cdef235a5636f5f529
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602146"
---
# <a name="get-c-reference"></a><span data-ttu-id="af9b1-102">get (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="af9b1-102">get (C# Reference)</span></span>

<span data-ttu-id="af9b1-103">Słowo kluczowe definiuje metodę dostępu we właściwości lub indeksatora, która zwraca wartość właściwości lub element indeksatora. `get`</span><span class="sxs-lookup"><span data-stu-id="af9b1-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="af9b1-104">Aby uzyskać więcej informacji, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zaimplementowane właściwości](../../programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="af9b1-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="af9b1-105">W poniższym przykładzie zdefiniowano `get` `set` metodę dostępu a i dla właściwości o nazwie `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="af9b1-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="af9b1-106">Używa pola prywatnego o nazwie `_seconds` do wstecz wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="af9b1-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="af9b1-107">`get` Często metoda dostępu składa się z pojedynczej instrukcji, która zwraca wartość, tak jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="af9b1-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="af9b1-108">Począwszy od C# 7,0, można zaimplementować `get` metodę dostępu jako element członkowski w postaci wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="af9b1-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="af9b1-109">W poniższym przykładzie zaimplementowane są `get` `set` i Akcesory jako elementy członkowskie z wyrażeniami.</span><span class="sxs-lookup"><span data-stu-id="af9b1-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="af9b1-110">W przypadku prostych przypadków, w których właściwości `get` i `set` metody dostępu nie wykonują żadnej innej operacji niż ustawienie lub pobranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi C# kompilatora w celu zaimplementowania. aœciwoœci.</span><span class="sxs-lookup"><span data-stu-id="af9b1-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="af9b1-111">Poniższy przykład implementuje `Hours` jako właściwość, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="af9b1-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="af9b1-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="af9b1-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af9b1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af9b1-113">See also</span></span>

- [<span data-ttu-id="af9b1-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="af9b1-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="af9b1-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="af9b1-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="af9b1-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="af9b1-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="af9b1-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="af9b1-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
