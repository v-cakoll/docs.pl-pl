---
title: '&amp;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933955"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="a60d2-102">&amp;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a60d2-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="a60d2-103">Operator przypisania AND.</span><span class="sxs-lookup"><span data-stu-id="a60d2-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a60d2-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a60d2-104">Remarks</span></span>  
 <span data-ttu-id="a60d2-105">Wyrażenie używające operatora przypisania `&=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="a60d2-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```csharp  
x &= y  
```  
  
 <span data-ttu-id="a60d2-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="a60d2-106">is equivalent to</span></span>  
  
```csharp  
x = x & y  
```  
  
 <span data-ttu-id="a60d2-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="a60d2-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a60d2-108">[& — Operator](../../../csharp/language-reference/operators/and-operator.md) wykonuje logiczne i operacji na poziomie bitowym operandy typu całkowitego i operator logiczny oraz na `bool` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="a60d2-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="a60d2-109">`&=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia pliku binarnego [& — operator](../../../csharp/language-reference/operators/and-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a60d2-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a60d2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a60d2-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a60d2-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a60d2-111">See Also</span></span>

- [<span data-ttu-id="a60d2-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a60d2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a60d2-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a60d2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a60d2-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a60d2-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
