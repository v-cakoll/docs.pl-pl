---
title: bool — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d6b0cb91dd9b8159919b0d155bb2f9773e7ba534
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "40239897"
---
# <a name="bool-c-reference"></a><span data-ttu-id="c1f1d-102">bool (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c1f1d-102">bool (C# Reference)</span></span>

<span data-ttu-id="c1f1d-103">`bool` — Słowo kluczowe jest aliasem <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c1f1d-104">Służy do deklarowania zmiennych do przechowywania wartości logiczne [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="c1f1d-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c1f1d-105">Jeśli potrzebujesz zmiennej typu Boolean, który może mieć również wartość `null`, użyj `bool?`.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="c1f1d-106">Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c1f1d-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>

## <a name="literals"></a><span data-ttu-id="c1f1d-107">Literały</span><span class="sxs-lookup"><span data-stu-id="c1f1d-107">Literals</span></span>

<span data-ttu-id="c1f1d-108">Można przypisać wartość logiczną umożliwiającą `bool` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="c1f1d-109">Można także przypisać wyrażenie, które daje w wyniku `bool` do `bool` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="c1f1d-110">Wartość domyślna `bool` zmienna jest `false`.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="c1f1d-111">Wartość domyślna `bool?` zmienna jest `null`.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-111">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="c1f1d-112">Konwersje</span><span class="sxs-lookup"><span data-stu-id="c1f1d-112">Conversions</span></span>

<span data-ttu-id="c1f1d-113">W języku C++, wartości typu `bool` można przekonwertować na wartość typu `int`; innymi słowy, `false` jest odpowiednikiem zero i `true` jest odpowiednikiem wartości niezerowych.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="c1f1d-114">W języku C# jest konwersja między `bool` typu a innymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="c1f1d-115">Na przykład następująca `if` instrukcja jest nieprawidłowa w języku C#:</span><span class="sxs-lookup"><span data-stu-id="c1f1d-115">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="c1f1d-116">Aby przetestować zmiennej typu `int`, trzeba jawnie porównania wartości, takich jak zero, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c1f1d-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="c1f1d-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1f1d-117">Example</span></span>

<span data-ttu-id="c1f1d-118">W tym przykładzie Wprowadź znak przy użyciu klawiatury i program sprawdza, czy znak danych wejściowych jest literą.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="c1f1d-119">Jeśli jest literą, sprawdza, czy jest wielką czy małą literą.</span><span class="sxs-lookup"><span data-stu-id="c1f1d-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="c1f1d-120">Te testy są wykonywane przy użyciu <xref:System.Char.IsLetter%2A>, i <xref:System.Char.IsLower%2A>, zarówno które zwrotu `bool` typu:</span><span class="sxs-lookup"><span data-stu-id="c1f1d-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="c1f1d-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c1f1d-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c1f1d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1f1d-122">See also</span></span>

[<span data-ttu-id="c1f1d-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c1f1d-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="c1f1d-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c1f1d-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="c1f1d-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c1f1d-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="c1f1d-126">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="c1f1d-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
[<span data-ttu-id="c1f1d-127">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="c1f1d-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[<span data-ttu-id="c1f1d-128">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="c1f1d-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[<span data-ttu-id="c1f1d-129">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="c1f1d-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  