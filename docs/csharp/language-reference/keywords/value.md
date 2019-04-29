---
title: kontekstowe słowo kluczowe wartości - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ee80888a57e999fa44e891dd6e0d64caa698009c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660362"
---
# <a name="value-c-reference"></a><span data-ttu-id="9a07f-102">value (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9a07f-102">value (C# Reference)</span></span>

<span data-ttu-id="9a07f-103">Kontekstowe słowo kluczowe `value` jest używany w metodzie dostępu set w deklaracji właściwości zwykłych.</span><span class="sxs-lookup"><span data-stu-id="9a07f-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="9a07f-104">Jest on podobny do parametru wejściowego metody.</span><span class="sxs-lookup"><span data-stu-id="9a07f-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="9a07f-105">Wyraz `value` odwołuje się do wartości, które podejmuje próbę przypisania do właściwości kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="9a07f-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="9a07f-106">W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name` , który używa `value` parametru, aby przypisać nowy ciąg do pola pomocniczego `name`.</span><span class="sxs-lookup"><span data-stu-id="9a07f-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="9a07f-107">Z punktu widzenia kodu klienta operacji jest zapisywany jako przypisanie proste.</span><span class="sxs-lookup"><span data-stu-id="9a07f-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="9a07f-108">Aby uzyskać więcej informacji na temat użytkowania `value`, zobacz [właściwości](../../programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="9a07f-108">For more information about the use of `value`, see [Properties](../../programming-guide/classes-and-structs/properties.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9a07f-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9a07f-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9a07f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a07f-110">See also</span></span>

- [<span data-ttu-id="9a07f-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9a07f-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9a07f-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9a07f-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9a07f-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9a07f-113">C# Keywords</span></span>](index.md)