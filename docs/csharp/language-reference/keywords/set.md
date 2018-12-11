---
title: set — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 3020badc8b7873d7feb0b8133d3a181e1c051cbd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243741"
---
# <a name="set-c-reference"></a><span data-ttu-id="58e8e-102">set (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="58e8e-102">set (C# Reference)</span></span>

<span data-ttu-id="58e8e-103">`set` — Słowo kluczowe definiuje *akcesor* metoda we właściwości lub indeksatora, który przypisuje wartość do właściwości lub elementu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="58e8e-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="58e8e-104">Aby uzyskać więcej informacji i przykładów, zobacz [właściwości](../../programming-guide/classes-and-structs/properties.md), [implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), i [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="58e8e-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="58e8e-105">W poniższym przykładzie zdefiniowano zarówno `get` i `set` akcesora dla właściwości o nazwie `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="58e8e-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="58e8e-106">Używa prywatnego pola o nazwie `_seconds` kopii wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="58e8e-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="58e8e-107">Często `set` dostępu składa się z pojedynczej instrukcji, która nie zwraca wartości, tak jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="58e8e-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="58e8e-108">Począwszy od języka C# 7.0, można zaimplementować `set` dostępu jako element członkowski wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="58e8e-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="58e8e-109">Poniższy przykład implementuje interfejsy `get` i `set` metod dostępu jako elementy członkowskie z wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="58e8e-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="58e8e-110">Dla prostych sytuacjach, w których właściwość `get` i `set` Akcesory wykonać żadna inna operacja niż ustawienie lub odczytywania wartości pola prywatnego zapasowy, możesz korzystać z zalet Obsługa właściwości zaimplementowane automatycznie w kompilatorze języka C#.</span><span class="sxs-lookup"><span data-stu-id="58e8e-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="58e8e-111">Poniższy przykład implementuje `Hours` jako automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="58e8e-111">The following example implements `Hours` as an auto-implemented property.</span></span> 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="58e8e-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="58e8e-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="58e8e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58e8e-113">See also</span></span>

- [<span data-ttu-id="58e8e-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="58e8e-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="58e8e-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="58e8e-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="58e8e-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="58e8e-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="58e8e-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="58e8e-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)