---
title: Operator — słowo kluczowe - C# odwołania
ms.custom: seodec18
description: Dowiedz się, jak przeciążenia wbudowanym operatorem języka C#
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: cdc052da4457a59cc66848780e944ccf203acf39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661077"
---
# <a name="operator-c-reference"></a><span data-ttu-id="13f7a-103">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="13f7a-103">operator (C# Reference)</span></span>

<span data-ttu-id="13f7a-104">Użyj `operator` — słowo kluczowe przeciążenia wbudowanym operatorem lub podać konwersja zdefiniowana przez użytkownika, w deklaracji klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="13f7a-104">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

<span data-ttu-id="13f7a-105">Aby przeciążyć operator na niestandardowej klasy lub struktury, musisz utworzyć Deklaracja operatora w odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="13f7a-105">To overload an operator on a custom class or struct, you create an operator declaration in the corresponding type.</span></span> <span data-ttu-id="13f7a-106">Deklaracja operatora, który przeciążenia wbudowanym operatorem języka C# musi spełniać następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="13f7a-106">The operator declaration that overloads a built-in C# operator must satisfy the following rules:</span></span>

- <span data-ttu-id="13f7a-107">Obejmuje zarówno `public` i `static` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="13f7a-107">It includes both a `public` and a `static` modifier.</span></span>
- <span data-ttu-id="13f7a-108">Zawiera on `operator X` gdzie `X` to nazwa lub symbol operatora jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="13f7a-108">It includes `operator X` where `X` is the name or symbol of the operator being overloaded.</span></span>
- <span data-ttu-id="13f7a-109">Operatory jednoargumentowe mieć jeden parametr, a operatory dwuargumentowe mają dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="13f7a-109">Unary operators have one parameter, and binary operators have two parameters.</span></span> <span data-ttu-id="13f7a-110">W każdym przypadku co najmniej jeden parametr musi być taki sam jak klasy lub struktury, która deklaruje operator.</span><span class="sxs-lookup"><span data-stu-id="13f7a-110">In each case, at least one parameter must be the same type as the class or struct that declares the operator.</span></span>

<span data-ttu-id="13f7a-111">Aby uzyskać informacje na temat definiowania operatorów konwersji, zobacz [jawne](explicit.md) i [niejawne](implicit.md) artykuły — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="13f7a-111">For information about how to define conversion operators, see the [explicit](explicit.md) and [implicit](implicit.md) keyword articles.</span></span>

<span data-ttu-id="13f7a-112">Aby uzyskać omówienie, które mogą być przeciążone operatory języka C#, zobacz [operatory z możliwością przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="13f7a-112">For an overview of the C# operators that can be overloaded, see the [Overloadable operators](../../programming-guide/statements-expressions-operators/overloadable-operators.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="13f7a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="13f7a-113">Example</span></span>

<span data-ttu-id="13f7a-114">W poniższym przykładzie zdefiniowano `Fraction` typ, który reprezentuje cyfry ułamkowe.</span><span class="sxs-lookup"><span data-stu-id="13f7a-114">The following example defines a `Fraction` type that represents fractional numbers.</span></span> <span data-ttu-id="13f7a-115">Przeciąża `+` i `*` operatory przeprowadzić ułamkowe Dodawanie i mnożenie, a także operator konwersji na to, że konwertuje `Fraction` typ `double` typu.</span><span class="sxs-lookup"><span data-stu-id="13f7a-115">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="13f7a-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="13f7a-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="13f7a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13f7a-117">See also</span></span>

- [<span data-ttu-id="13f7a-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="13f7a-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13f7a-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="13f7a-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13f7a-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="13f7a-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="13f7a-121">implicit</span><span class="sxs-lookup"><span data-stu-id="13f7a-121">implicit</span></span>](implicit.md)
- [<span data-ttu-id="13f7a-122">explicit</span><span class="sxs-lookup"><span data-stu-id="13f7a-122">explicit</span></span>](explicit.md)
- [<span data-ttu-id="13f7a-123">Operatory z możliwością przeciążenia</span><span class="sxs-lookup"><span data-stu-id="13f7a-123">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="13f7a-124">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="13f7a-124">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
