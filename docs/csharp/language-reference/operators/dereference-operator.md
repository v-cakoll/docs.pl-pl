---
title: -&gt; Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 09d67b8386da371f7d98a8171f60298b316091ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="93cb0-102">-&gt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="93cb0-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="93cb0-103">Operator `->` łączy wyłuskanie wskaźnika i dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="93cb0-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93cb0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93cb0-104">Remarks</span></span>  
 <span data-ttu-id="93cb0-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="93cb0-105">An expression of the form,</span></span>  
  
```  
x->y  
```  
  
 <span data-ttu-id="93cb0-106">(gdzie `x` to wskaźnik typu `T*`, a `y` to element członkowski `T`) jest odpowiednikiem wyrażenia</span><span class="sxs-lookup"><span data-stu-id="93cb0-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```  
(*x).y  
```  
  
 <span data-ttu-id="93cb0-107">Operatora `->` można używać tylko w kodzie, który jest oznaczony jako [niebezpieczny](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="93cb0-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="93cb0-108">Operator `->` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="93cb0-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93cb0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="93cb0-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="93cb0-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93cb0-110">See Also</span></span>  
 [<span data-ttu-id="93cb0-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="93cb0-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="93cb0-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="93cb0-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="93cb0-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="93cb0-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
