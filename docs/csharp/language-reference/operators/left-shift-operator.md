---
title: '&lt;&lt; Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 036acd6159bcf5ca1677ee6383c9db357625cd67
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511136"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="cd6a6-102">&lt;&lt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cd6a6-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="cd6a6-103">Operator przesunięcia w lewo (`<<`) pierwszy argument operacji lewo o liczbę bitów określoną przez drugim argumentem operacji przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="cd6a6-104">Typ drugiego argumentu operacji musi być [int](../../../csharp/language-reference/keywords/int.md) lub typ, który ma wstępnie zdefiniowanych niejawnej konwersji liczbowych do `int`.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd6a6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd6a6-105">Remarks</span></span>  
 <span data-ttu-id="cd6a6-106">Jeśli pierwszy argument jest [int](../../../csharp/language-reference/keywords/int.md) lub [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitowy), licznik przesunięć oblicza niskiego rzędu pięć bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="cd6a6-107">Licznik przesunięć rzeczywistego jest bitów 0 do 31.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="cd6a6-108">Jeśli pierwszy argument jest [długie](../../../csharp/language-reference/keywords/long.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza mniej znaczące bity sześć, drugi operand.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="cd6a6-109">Licznik przesunięć rzeczywistego jest 0, 63 bity.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="cd6a6-110">Wszystkie bity wyższego rzędu, które są nie w zakresie typem pierwszego operandu po zmiany zostaną odrzucone i mniej znaczące bity puste są wypełnione przez zera.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="cd6a6-111">Operacje przesunięcia nigdy nie powodują przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="cd6a6-112">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia `<<` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)); typ pierwszy operand musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="cd6a6-113">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd6a6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd6a6-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="cd6a6-115">Komentarze</span><span class="sxs-lookup"><span data-stu-id="cd6a6-115">Comments</span></span>  
 <span data-ttu-id="cd6a6-116">Należy pamiętać, że `i<<1` i `i<<33` dają taki sam efekt, ponieważ 1 i 33 mają ten sam mniej znaczące bity pięć.</span><span class="sxs-lookup"><span data-stu-id="cd6a6-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6a6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd6a6-117">See Also</span></span>

- [<span data-ttu-id="cd6a6-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cd6a6-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="cd6a6-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cd6a6-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cd6a6-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="cd6a6-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
