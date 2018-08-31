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
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43330935"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1440f-102">Operator /= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1440f-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="1440f-103">Operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="1440f-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1440f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1440f-104">Remarks</span></span>  
 <span data-ttu-id="1440f-105">Wyrażenie używające operatora przypisania `/=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="1440f-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="1440f-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="1440f-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="1440f-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1440f-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="1440f-108">[/ Operator](../../../csharp/language-reference/operators/division-operator.md) wstępnie zdefiniowany dla typów liczbowych wykonać dzielenie.</span><span class="sxs-lookup"><span data-stu-id="1440f-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="1440f-109">`/=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [/ operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1440f-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1440f-110">Na wszystkich złożone operatory przypisania przeciążenie operatora binarnego niejawnie przeciążenia równoważne przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="1440f-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1440f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="1440f-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1440f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1440f-112">See Also</span></span>

- [<span data-ttu-id="1440f-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1440f-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1440f-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1440f-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1440f-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1440f-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
