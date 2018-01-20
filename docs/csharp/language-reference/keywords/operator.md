---
title: "operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords: operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d035319318a710ccee62a0c64ce5981767a21ca
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="operator-c-reference"></a><span data-ttu-id="6cc22-102">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6cc22-102">operator (C# Reference)</span></span>
<span data-ttu-id="6cc22-103">Użyj `operator` — słowo kluczowe przeciążenia operatora wbudowane lub udzielenia konwersji zdefiniowanej przez użytkownika w deklaracji klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6cc22-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cc22-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cc22-104">Example</span></span>  
 <span data-ttu-id="6cc22-105">Poniżej znajduje się bardzo uproszczonego klasę liczbami ułamkowymi.</span><span class="sxs-lookup"><span data-stu-id="6cc22-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="6cc22-106">Przeciąża `+` i `*` operatory przeprowadzić ułamkowych Dodawanie i mnożenie i udostępnia również operatora konwersji tego konwertuje `Fraction` typ `double` typu.</span><span class="sxs-lookup"><span data-stu-id="6cc22-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6cc22-107">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6cc22-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6cc22-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cc22-108">See Also</span></span>  
 [<span data-ttu-id="6cc22-109">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6cc22-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6cc22-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6cc22-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6cc22-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6cc22-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6cc22-112">implicit</span><span class="sxs-lookup"><span data-stu-id="6cc22-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="6cc22-113">explicit</span><span class="sxs-lookup"><span data-stu-id="6cc22-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="6cc22-114">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="6cc22-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
