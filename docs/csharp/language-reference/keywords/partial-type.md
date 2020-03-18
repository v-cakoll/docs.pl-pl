---
title: typ częściowy — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715208"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="09f3f-102">typ częściowy (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="09f3f-102">partial type (C# Reference)</span></span>

<span data-ttu-id="09f3f-103">Definicje typów częściowych umożliwiają podzielenie definicji klasy, struktury lub interfejsu na wiele plików.</span><span class="sxs-lookup"><span data-stu-id="09f3f-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="09f3f-104">W *File1.cs:*</span><span class="sxs-lookup"><span data-stu-id="09f3f-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="09f3f-105">W *File2.cs* deklaracja:</span><span class="sxs-lookup"><span data-stu-id="09f3f-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="09f3f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09f3f-106">Remarks</span></span>

<span data-ttu-id="09f3f-107">Dzielenie typu klasy, struktury lub interfejsu na kilka plików może być przydatne podczas pracy z dużymi projektami lub z automatycznie generowanym kodem, takim jak ten dostarczony przez [Projektanta formularzy systemu Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="09f3f-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="09f3f-108">Typ częściowy może zawierać [metodę częściową](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="09f3f-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="09f3f-109">Aby uzyskać więcej informacji, zobacz [Klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="09f3f-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="09f3f-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="09f3f-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="09f3f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09f3f-111">See also</span></span>

- [<span data-ttu-id="09f3f-112">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="09f3f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="09f3f-113">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="09f3f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="09f3f-114">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="09f3f-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="09f3f-115">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="09f3f-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
