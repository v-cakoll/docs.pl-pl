---
title: '!= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e409e2a80886fd5f7f4cdbeaa9b4e3325f8a967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272442"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="48511-102">!= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="48511-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="48511-103">Operator nierówności (`!=`) zwraca wartość false, jeśli swoich argumentów, są takie same, wartości true w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="48511-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="48511-104">Operatory nierówności są wstępnie zdefiniowane dla wszystkich typów, w tym ciągu lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="48511-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="48511-105">Typy definiowane przez użytkownika można przeciążać `!=` operatora.</span><span class="sxs-lookup"><span data-stu-id="48511-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48511-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48511-106">Remarks</span></span>  
 <span data-ttu-id="48511-107">Dla wstępnie zdefiniowanych typów wartości, operator nierówności (`!=`) zwraca wartość true, jeśli wartości argumentów są różne, wartość false w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="48511-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="48511-108">Dla odwołania do typów innych niż `string`, `!=` zwraca wartość true, jeśli jego dwóch argumentów operacji odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="48511-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="48511-109">Aby uzyskać `string` typu `!=` porównuje wartości ciągów.</span><span class="sxs-lookup"><span data-stu-id="48511-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="48511-110">Typy wartości zdefiniowane przez użytkownika można przeciążać `!=` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="48511-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="48511-111">Dlatego można typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `!=` zachowuje się jak opisano powyżej dla obu typów odniesienia wstępnie zdefiniowane i zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="48511-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="48511-112">Jeśli `!=` jest przeciążony [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="48511-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="48511-113">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="48511-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48511-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="48511-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="48511-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48511-115">See Also</span></span>  
 [<span data-ttu-id="48511-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="48511-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="48511-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="48511-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="48511-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="48511-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
