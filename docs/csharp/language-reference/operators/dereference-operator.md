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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552169"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="a6ae7-102">-&gt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a6ae7-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="a6ae7-103">Operator `->` łączy wyłuskanie wskaźnika i dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a6ae7-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6ae7-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6ae7-104">Remarks</span></span>  
 <span data-ttu-id="a6ae7-105">Wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="a6ae7-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="a6ae7-106">(gdzie `x` to wskaźnik typu `T*`, a `y` to element członkowski `T`) jest odpowiednikiem wyrażenia</span><span class="sxs-lookup"><span data-stu-id="a6ae7-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="a6ae7-107">Operatora `->` można używać tylko w kodzie, który jest oznaczony jako [niebezpieczny](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="a6ae7-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="a6ae7-108">Operator `->` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="a6ae7-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6ae7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6ae7-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a6ae7-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6ae7-110">See Also</span></span>

- [<span data-ttu-id="a6ae7-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a6ae7-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a6ae7-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a6ae7-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a6ae7-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a6ae7-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
