---
title: wartość kontekstowe słowo kluczowe - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712900"
---
# <a name="value-c-reference"></a><span data-ttu-id="4197d-102">value (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4197d-102">value (C# Reference)</span></span>

<span data-ttu-id="4197d-103">Kontekstowe słowo `value` kluczowe jest `set` używane w akcesor w [deklaracji właściwości](../../programming-guide/classes-and-structs/properties.md) i [indeksatora.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="4197d-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="4197d-104">Jest on podobny do parametru wejściowego metody.</span><span class="sxs-lookup"><span data-stu-id="4197d-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="4197d-105">Słowo `value` odwołuje się do wartości, którą kod klienta próbuje przypisać do właściwości lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="4197d-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="4197d-106">W poniższym `MyDerivedClass` przykładzie ma `Name` właściwość o `value` nazwie, która używa parametru, `name`aby przypisać nowy ciąg do pola zapasowego .</span><span class="sxs-lookup"><span data-stu-id="4197d-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="4197d-107">Z punktu widzenia kodu klienta operacja jest zapisywana jako proste przypisanie.</span><span class="sxs-lookup"><span data-stu-id="4197d-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="4197d-108">Aby uzyskać więcej informacji, zobacz [właściwości](../../programming-guide/classes-and-structs/properties.md) i [indeksatorzy artykułów.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="4197d-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4197d-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4197d-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4197d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4197d-110">See also</span></span>

- [<span data-ttu-id="4197d-111">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="4197d-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4197d-112">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="4197d-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4197d-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4197d-113">C# Keywords</span></span>](index.md)
