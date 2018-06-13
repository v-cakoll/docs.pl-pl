---
title: partial (typ) (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4f57149dd18deb08aa11b72d0a6d5f71b3838bd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266692"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="7a0a5-102">partial (typ) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7a0a5-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="7a0a5-103">Definicje typu częściowego umożliwiają definicji klasy, struktury lub interfejsu można podzielić na wiele plików.</span><span class="sxs-lookup"><span data-stu-id="7a0a5-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="7a0a5-104">W File1.cs:</span><span class="sxs-lookup"><span data-stu-id="7a0a5-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="7a0a5-105">W deklaracji File2.cs:</span><span class="sxs-lookup"><span data-stu-id="7a0a5-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="7a0a5-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a0a5-106">Remarks</span></span>  
 <span data-ttu-id="7a0a5-107">Dzielenie klasy, struktury lub interfejsu typu przez kilka plików może być przydatne podczas pracy z dużych projektów lub automatycznie wygenerowanego kodu, takim jak udostępniany przez [Projektant formularzy systemu Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7a0a5-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="7a0a5-108">Typ częściowego może zawierać [metody częściowej](../../../csharp/language-reference/keywords/partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="7a0a5-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="7a0a5-109">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7a0a5-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7a0a5-110">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7a0a5-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a0a5-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a0a5-111">See Also</span></span>  
 [<span data-ttu-id="7a0a5-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="7a0a5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7a0a5-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7a0a5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7a0a5-114">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="7a0a5-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="7a0a5-115">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="7a0a5-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
