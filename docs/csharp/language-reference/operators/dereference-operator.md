---
title: -&gt; Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875856"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="07cbc-102">-&gt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="07cbc-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="07cbc-103">Operator `->` łączy wyłuskanie wskaźnika i dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="07cbc-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07cbc-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07cbc-104">Remarks</span></span>  
 <span data-ttu-id="07cbc-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="07cbc-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="07cbc-106">(gdzie `x` to wskaźnik typu `T*`, a `y` to element członkowski `T`) jest odpowiednikiem wyrażenia</span><span class="sxs-lookup"><span data-stu-id="07cbc-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="07cbc-107">Operatora `->` można używać tylko w kodzie, który jest oznaczony jako [niebezpieczny](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="07cbc-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="07cbc-108">Operator `->` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="07cbc-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07cbc-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="07cbc-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="07cbc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07cbc-110">See Also</span></span>

- [<span data-ttu-id="07cbc-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="07cbc-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="07cbc-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="07cbc-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="07cbc-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="07cbc-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
