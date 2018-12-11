---
title: / = — Operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 0487088fa5420f2d15541aa3f7b1d4ec604195bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241249"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="317a9-102">Operator /= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="317a9-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="317a9-103">Operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="317a9-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="317a9-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="317a9-104">Remarks</span></span>  
 <span data-ttu-id="317a9-105">Wyrażenie używające operatora przypisania `/=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="317a9-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="317a9-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="317a9-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="317a9-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="317a9-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="317a9-108">[/ Operator](../../../csharp/language-reference/operators/division-operator.md) wstępnie zdefiniowany dla typów liczbowych wykonać dzielenie.</span><span class="sxs-lookup"><span data-stu-id="317a9-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="317a9-109">`/=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [/ operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="317a9-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="317a9-110">Na wszystkich złożone operatory przypisania przeciążenie operatora binarnego niejawnie przeciążenia równoważne przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="317a9-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="317a9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="317a9-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="317a9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="317a9-112">See Also</span></span>

- [<span data-ttu-id="317a9-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="317a9-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="317a9-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="317a9-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="317a9-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="317a9-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
