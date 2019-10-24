---
title: kontekstowe słowo kluczowe C# wartości — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 34b192d17bd96b6b893c9f14f0d4a77274a32f78
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771740"
---
# <a name="value-c-reference"></a><span data-ttu-id="2e83f-102">value (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2e83f-102">value (C# Reference)</span></span>

<span data-ttu-id="2e83f-103">Kontekstowe słowo kluczowe `value` jest używane w metodzie dostępu `set` w deklaracjach [Właściwości](../../programming-guide/classes-and-structs/properties.md) i [indeksatora](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="2e83f-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="2e83f-104">Jest podobny do parametru wejściowego metody.</span><span class="sxs-lookup"><span data-stu-id="2e83f-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="2e83f-105">Słowo `value` odwołuje się do wartości, którą kod klienta próbuje przypisać do właściwości lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="2e83f-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="2e83f-106">W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name`, która używa parametru `value` do przypisywania nowego ciągu do pola zapasowego `name`.</span><span class="sxs-lookup"><span data-stu-id="2e83f-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="2e83f-107">Z punktu widzenia kodu klienta operacja jest zapisywana jako proste przypisanie.</span><span class="sxs-lookup"><span data-stu-id="2e83f-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="2e83f-108">Aby uzyskać więcej informacji, zobacz artykuły [Properties](../../programming-guide/classes-and-structs/properties.md) i [Indexeres](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="2e83f-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2e83f-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2e83f-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2e83f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e83f-110">See also</span></span>

- [<span data-ttu-id="2e83f-111">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="2e83f-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2e83f-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2e83f-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2e83f-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2e83f-113">C# Keywords</span></span>](index.md)
