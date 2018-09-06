---
title: Operator -- (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 615b100447233856ab3740d075d69e3ae19285fd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037805"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="38c84-102">Operator -- (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="38c84-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="38c84-103">Operator dekrementacji (`--`) zmniejsza wartość jego argumentu operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="38c84-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="38c84-104">Operator dekrementacji może występować przed argumentem operacji lub po nim: `--variable` i `variable--`.</span><span class="sxs-lookup"><span data-stu-id="38c84-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="38c84-105">Pierwszą formą jest dekrementacja prefiksowa.</span><span class="sxs-lookup"><span data-stu-id="38c84-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="38c84-106">Wynikiem tej operacji jest wartość argumentu operacji po zmniejszeniu.</span><span class="sxs-lookup"><span data-stu-id="38c84-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="38c84-107">Drugą formą jest dekrementacja odwrotna. </span><span class="sxs-lookup"><span data-stu-id="38c84-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="38c84-108">Wynikiem tej operacji jest wartość argumentu przed zmniejszeniem.</span><span class="sxs-lookup"><span data-stu-id="38c84-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38c84-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38c84-109">Remarks</span></span>  
 <span data-ttu-id="38c84-110">Typy numeryczne i wyliczenia mają wstępnie zdefiniowane operatory dekrementacji.</span><span class="sxs-lookup"><span data-stu-id="38c84-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="38c84-111">W typach definiowanych przez użytkownika można przeciążać operator `--` (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="38c84-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="38c84-112">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="38c84-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38c84-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="38c84-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="38c84-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38c84-114">See Also</span></span>

- [<span data-ttu-id="38c84-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="38c84-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="38c84-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="38c84-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="38c84-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="38c84-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
