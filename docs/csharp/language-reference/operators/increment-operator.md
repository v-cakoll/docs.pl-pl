---
title: "++ — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9a97a-102">++ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9a97a-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="9a97a-103">Operator inkrementacji (`++`) zwiększa jej argument operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="9a97a-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="9a97a-104">Operator inkrementacji może występować przed lub po jej argument: `++variable` i `variable++`.</span><span class="sxs-lookup"><span data-stu-id="9a97a-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a97a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a97a-105">Remarks</span></span>  
 <span data-ttu-id="9a97a-106">Pierwszy formularz jest operacja zwiększenia prefiks.</span><span class="sxs-lookup"><span data-stu-id="9a97a-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="9a97a-107">Wynikiem operacji jest wartość operandu po została zwiększona.</span><span class="sxs-lookup"><span data-stu-id="9a97a-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="9a97a-108">Drugi formularz jest operacją operatory przyrostka inkrementacji.</span><span class="sxs-lookup"><span data-stu-id="9a97a-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="9a97a-109">Wynikiem operacji jest wartość operandu przed została zwiększona.</span><span class="sxs-lookup"><span data-stu-id="9a97a-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="9a97a-110">Typy numeryczne i wyliczenia mają wstępnie zdefiniowane operatory inkrementacji.</span><span class="sxs-lookup"><span data-stu-id="9a97a-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="9a97a-111">Typy definiowane przez użytkownika można przeciążać `++` operatora.</span><span class="sxs-lookup"><span data-stu-id="9a97a-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="9a97a-112">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="9a97a-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a97a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a97a-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9a97a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a97a-114">See Also</span></span>  
 [<span data-ttu-id="9a97a-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9a97a-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9a97a-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9a97a-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9a97a-117">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="9a97a-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
