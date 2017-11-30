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
ms.openlocfilehash: 8fae5487d5daa5ada52d45919598d1abd217aee9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="operator-c-reference"></a><span data-ttu-id="f0ed5-102">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f0ed5-102">operator (C# Reference)</span></span>
<span data-ttu-id="f0ed5-103">Użyj `operator` — słowo kluczowe przeciążenia operatora wbudowane lub udzielenia konwersji zdefiniowanej przez użytkownika w deklaracji klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f0ed5-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0ed5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0ed5-104">Example</span></span>  
 <span data-ttu-id="f0ed5-105">Poniżej znajduje się bardzo uproszczonego klasę liczbami ułamkowymi.</span><span class="sxs-lookup"><span data-stu-id="f0ed5-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="f0ed5-106">Przeciąża + i * operatory przeprowadzić ułamkowych Dodawanie i mnożenie i udostępnia również operatora konwersji, który konwertuje typ ułamek typu double.</span><span class="sxs-lookup"><span data-stu-id="f0ed5-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f0ed5-107">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f0ed5-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0ed5-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0ed5-108">See Also</span></span>  
 [<span data-ttu-id="f0ed5-109">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f0ed5-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f0ed5-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f0ed5-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f0ed5-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f0ed5-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f0ed5-112">niejawne</span><span class="sxs-lookup"><span data-stu-id="f0ed5-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="f0ed5-113">jawne</span><span class="sxs-lookup"><span data-stu-id="f0ed5-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="f0ed5-114">Porady: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="f0ed5-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
