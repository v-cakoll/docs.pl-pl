---
title: return (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244780"
---
# <a name="return-c-reference"></a><span data-ttu-id="1a8a6-102">return (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1a8a6-102">return (C# Reference)</span></span>
<span data-ttu-id="1a8a6-103">`return` Kończy wykonywanie metody, w którym występuje i zwraca kontrolę do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="1a8a6-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="1a8a6-104">Może również zwracać wartość opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a8a6-104">It can also return an optional value.</span></span> <span data-ttu-id="1a8a6-105">Jeśli metoda jest `void` typu `return` instrukcji, można pominąć.</span><span class="sxs-lookup"><span data-stu-id="1a8a6-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="1a8a6-106">Jeśli znajduje się wewnątrz instrukcji return `try` bloku `finally` bloku, jeśli taki istnieje, zostanie wykonana zanim sterowanie powraca do wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="1a8a6-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a8a6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a8a6-107">Example</span></span>  
 <span data-ttu-id="1a8a6-108">W poniższym przykładzie metoda `CalculateArea()` zwraca zmienna lokalna `area` jako [double](../../../csharp/language-reference/keywords/double.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="1a8a6-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1a8a6-109">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1a8a6-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a8a6-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a8a6-110">See Also</span></span>  
 [<span data-ttu-id="1a8a6-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1a8a6-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1a8a6-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1a8a6-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1a8a6-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1a8a6-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1a8a6-114">return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a8a6-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="1a8a6-115">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="1a8a6-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
