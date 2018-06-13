---
title: goto (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 2dd70a30b885dcdae9637b02e8c34ac39f4879fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216807"
---
# <a name="goto-c-reference"></a><span data-ttu-id="a2637-102">goto (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a2637-102">goto (C# Reference)</span></span>
<span data-ttu-id="a2637-103">`goto` Instrukcji przesyła formantu programu bezpośrednio z etykietą instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a2637-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="a2637-104">Typowym zastosowaniem `goto` się transfer kontroli do określonej etykiety przypadek switch lub etykieta domyślna w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a2637-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="a2637-105">`goto` Instrukcji przydaje się także wykorzystanie głęboko zagnieżdżone pętle.</span><span class="sxs-lookup"><span data-stu-id="a2637-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2637-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2637-106">Example</span></span>  
 <span data-ttu-id="a2637-107">W poniższym przykładzie pokazano, za pomocą `goto` w [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a2637-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="a2637-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2637-108">Example</span></span>  
 <span data-ttu-id="a2637-109">W poniższym przykładzie pokazano, przy użyciu `goto` umożliwiające rozbicie z pętli zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="a2637-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a2637-110">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a2637-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a2637-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2637-111">See Also</span></span>  
 [<span data-ttu-id="a2637-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a2637-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a2637-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a2637-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a2637-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a2637-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a2637-115">goto, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a2637-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="a2637-116">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="a2637-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
