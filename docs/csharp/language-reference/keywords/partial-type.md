---
title: częściowe odwołanie do C# typu
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715208"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="7080a-102">Typ częściowyC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="7080a-102">partial type (C# Reference)</span></span>

<span data-ttu-id="7080a-103">Definicje typu częściowego umożliwiają poddzielenie definicji klasy, struktury lub interfejsu na wiele plików.</span><span class="sxs-lookup"><span data-stu-id="7080a-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="7080a-104">W *file1.cs*:</span><span class="sxs-lookup"><span data-stu-id="7080a-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="7080a-105">W *file2.cs* deklaracji:</span><span class="sxs-lookup"><span data-stu-id="7080a-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="7080a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7080a-106">Remarks</span></span>

<span data-ttu-id="7080a-107">Dzielenie klasy, struktury lub interfejsu za pomocą kilku plików może być przydatne podczas pracy z dużymi projektami lub z automatycznie generowanym kodem, takim jak [Projektant formularzy systemu Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7080a-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="7080a-108">Typ częściowy może zawierać [metodę częściową](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="7080a-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="7080a-109">Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7080a-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7080a-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7080a-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7080a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7080a-111">See also</span></span>

- [<span data-ttu-id="7080a-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7080a-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7080a-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7080a-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7080a-114">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="7080a-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7080a-115">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="7080a-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
