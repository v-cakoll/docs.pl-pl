---
title: Operator /= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 1d9b918c66ce361067d906a055df5adb25a5a308
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a48cb-102">Operator /= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a48cb-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="a48cb-103">Operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="a48cb-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a48cb-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a48cb-104">Remarks</span></span>  
 <span data-ttu-id="a48cb-105">Za pomocą wyrażenia `/=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="a48cb-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="a48cb-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="a48cb-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="a48cb-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="a48cb-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a48cb-108">[/ — Operator](../../../csharp/language-reference/operators/division-operator.md) jest wstępnie zdefiniowane na typy liczbowe do wykonania podziału.</span><span class="sxs-lookup"><span data-stu-id="a48cb-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="a48cb-109">`/=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [/ — operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a48cb-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a48cb-110">Na wszystkich złożone operatory przypisania niejawnie przeciążanie operatora binarnego overloads równoważne przydział złożony.</span><span class="sxs-lookup"><span data-stu-id="a48cb-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a48cb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a48cb-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a48cb-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a48cb-112">See Also</span></span>  
 [<span data-ttu-id="a48cb-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a48cb-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a48cb-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a48cb-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a48cb-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a48cb-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
