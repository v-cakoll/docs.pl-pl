---
title: Operator /= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: c31ff374e6af4c08c329a971fdd8af169e239395
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="099d6-102">Operator /= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="099d6-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="099d6-103">Operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="099d6-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="099d6-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="099d6-104">Remarks</span></span>  
 <span data-ttu-id="099d6-105">Za pomocą wyrażenia `/=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="099d6-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="099d6-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="099d6-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="099d6-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="099d6-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="099d6-108">[/ — Operator](../../../csharp/language-reference/operators/division-operator.md) jest wstępnie zdefiniowane na typy liczbowe do wykonania podziału.</span><span class="sxs-lookup"><span data-stu-id="099d6-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="099d6-109">`/=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [/ — operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="099d6-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="099d6-110">Na wszystkich złożone operatory przypisania niejawnie przeciążanie operatora binarnego overloads równoważne przydział złożony.</span><span class="sxs-lookup"><span data-stu-id="099d6-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="099d6-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="099d6-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="099d6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="099d6-112">See Also</span></span>  
 [<span data-ttu-id="099d6-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="099d6-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="099d6-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="099d6-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="099d6-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="099d6-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
