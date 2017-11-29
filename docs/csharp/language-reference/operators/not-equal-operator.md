---
title: "!= — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b69d0b12734e690f0ba0209ccbbc7627ff92fe8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="65032-102">!= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="65032-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="65032-103">Operator nierówności (`!=`) zwraca wartość false, jeśli swoich argumentów, są takie same, wartości true w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="65032-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="65032-104">Operatory nierówności są wstępnie zdefiniowane dla wszystkich typów, w tym ciągu lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="65032-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="65032-105">Typy definiowane przez użytkownika można przeciążać `!=` operatora.</span><span class="sxs-lookup"><span data-stu-id="65032-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65032-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65032-106">Remarks</span></span>  
 <span data-ttu-id="65032-107">Dla wstępnie zdefiniowanych typów wartości, operator nierówności (`!=`) zwraca wartość true, jeśli wartości argumentów są różne, wartość false w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="65032-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="65032-108">Dla odwołania do typów innych niż `string`, `!=` zwraca wartość true, jeśli jego dwóch argumentów operacji odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="65032-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="65032-109">Aby uzyskać `string` typu `!=` porównuje wartości ciągów.</span><span class="sxs-lookup"><span data-stu-id="65032-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="65032-110">Typy wartości zdefiniowane przez użytkownika można przeciążać `!=` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="65032-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="65032-111">Dlatego można typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `!=` zachowuje się jak opisano powyżej dla obu typów odniesienia wstępnie zdefiniowane i zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65032-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="65032-112">Jeśli `!=` jest przeciążony [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="65032-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="65032-113">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="65032-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65032-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="65032-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="65032-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65032-115">See Also</span></span>  
 [<span data-ttu-id="65032-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="65032-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="65032-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="65032-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65032-118">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="65032-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
