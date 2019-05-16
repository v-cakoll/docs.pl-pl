---
title: Typ częściowej — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 5dba3759d8d0046f2a491e1d3408acb54bd0343d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633372"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="eba48-102">typu częściowego (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="eba48-102">partial type (C# Reference)</span></span>

<span data-ttu-id="eba48-103">Definicje typu częściowego umożliwiają definicji klasy, struktury lub interfejsu ma być podzielony na wiele plików.</span><span class="sxs-lookup"><span data-stu-id="eba48-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="eba48-104">W *File1.cs*:</span><span class="sxs-lookup"><span data-stu-id="eba48-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="eba48-105">W *File2.cs* deklaracji:</span><span class="sxs-lookup"><span data-stu-id="eba48-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="eba48-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eba48-106">Remarks</span></span>

<span data-ttu-id="eba48-107">Podział klasy, struktury lub interfejsu typ za pośrednictwem kilku plików może być przydatny podczas pracy z dużymi projektami lub z automatycznie wygenerowanego kodu, takim jak udostępniany przez [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="eba48-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="eba48-108">Może zawierać typu częściowego [metody częściowej](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="eba48-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="eba48-109">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="eba48-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eba48-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eba48-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eba48-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eba48-111">See also</span></span>

- [<span data-ttu-id="eba48-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eba48-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eba48-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="eba48-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eba48-114">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="eba48-114">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="eba48-115">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="eba48-115">Introduction to Generics</span></span>](../../programming-guide/generics/introduction-to-generics.md)
