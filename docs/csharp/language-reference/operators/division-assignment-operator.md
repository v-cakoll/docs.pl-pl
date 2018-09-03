---
title: Operator /= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 8fff048cc441181aa3f0e3c0c638d501aaf9de3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43477948"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b8a31-102">Operator /= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b8a31-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="b8a31-103">Operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="b8a31-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8a31-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8a31-104">Remarks</span></span>  
 <span data-ttu-id="b8a31-105">Wyrażenie używające operatora przypisania `/=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="b8a31-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="b8a31-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="b8a31-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="b8a31-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="b8a31-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b8a31-108">[/ Operator](../../../csharp/language-reference/operators/division-operator.md) wstępnie zdefiniowany dla typów liczbowych wykonać dzielenie.</span><span class="sxs-lookup"><span data-stu-id="b8a31-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="b8a31-109">`/=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [/ operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b8a31-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="b8a31-110">Na wszystkich złożone operatory przypisania przeciążenie operatora binarnego niejawnie przeciążenia równoważne przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="b8a31-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8a31-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8a31-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b8a31-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8a31-112">See Also</span></span>

- [<span data-ttu-id="b8a31-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b8a31-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b8a31-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b8a31-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b8a31-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b8a31-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
