---
title: partial (typ) (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 362a02815cb249d57c0bd19706714df1d71644f4
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929666"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="33b92-102">partial (typ) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="33b92-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="33b92-103">Definicje typu częściowego umożliwiają definicji klasy, struktury lub interfejsu ma być podzielony na wiele plików.</span><span class="sxs-lookup"><span data-stu-id="33b92-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="33b92-104">W File1.cs:</span><span class="sxs-lookup"><span data-stu-id="33b92-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="33b92-105">W File2.cs deklaracji:</span><span class="sxs-lookup"><span data-stu-id="33b92-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="33b92-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33b92-106">Remarks</span></span>  
 <span data-ttu-id="33b92-107">Podział klasy, struktury lub interfejsu typ za pośrednictwem kilku plików może być przydatny podczas pracy z dużymi projektami lub z automatycznie wygenerowanego kodu, takim jak udostępniany przez [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="33b92-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="33b92-108">Może zawierać typu częściowego [metody częściowej](../../../csharp/language-reference/keywords/partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="33b92-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="33b92-109">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="33b92-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="33b92-110">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="33b92-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33b92-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33b92-111">See Also</span></span>

- [<span data-ttu-id="33b92-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="33b92-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="33b92-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="33b92-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="33b92-114">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="33b92-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="33b92-115">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="33b92-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
