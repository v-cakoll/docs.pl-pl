---
title: częściowe odwołanie do C# typu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 7af43a25f88ff0a53e5fa257b13bb1dc8a6d55eb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422612"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="25209-102">Typ częściowyC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="25209-102">partial type (C# Reference)</span></span>

<span data-ttu-id="25209-103">Definicje typu częściowego umożliwiają poddzielenie definicji klasy, struktury lub interfejsu na wiele plików.</span><span class="sxs-lookup"><span data-stu-id="25209-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="25209-104">W *file1.cs*:</span><span class="sxs-lookup"><span data-stu-id="25209-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="25209-105">W *file2.cs* deklaracji:</span><span class="sxs-lookup"><span data-stu-id="25209-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="25209-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25209-106">Remarks</span></span>

<span data-ttu-id="25209-107">Dzielenie klasy, struktury lub interfejsu za pomocą kilku plików może być przydatne podczas pracy z dużymi projektami lub z automatycznie generowanym kodem, takim jak [Projektant formularzy systemu Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="25209-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="25209-108">Typ częściowy może zawierać [metodę częściową](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="25209-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="25209-109">Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="25209-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="25209-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="25209-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="25209-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25209-111">See also</span></span>

- [<span data-ttu-id="25209-112">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="25209-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="25209-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="25209-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="25209-114">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="25209-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="25209-115">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="25209-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
