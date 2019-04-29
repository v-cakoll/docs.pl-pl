---
title: bool — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d87da29872582e9c0d47a6c999312ce88252a5cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662078"
---
# <a name="bool-c-reference"></a><span data-ttu-id="30da4-102">bool (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="30da4-102">bool (C# Reference)</span></span>

<span data-ttu-id="30da4-103">`bool` — Słowo kluczowe jest aliasem <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30da4-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="30da4-104">Służy do deklarowania zmiennych do przechowywania wartości logiczne: [true](true-literal.md) i [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="30da4-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="30da4-105">Użyj `bool?` typu, jeśli wymagana jest obsługa przechowywanymi w trzech logiki, na przykład podczas pracy z bazami danych, które obsługują przechowywanymi w trzech typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="30da4-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="30da4-106">Dla `bool?` argumentów operacji, wstępnie zdefiniowane `&` i `|` Operatorzy pomocy technicznej przechowywanymi w trzech logiki.</span><span class="sxs-lookup"><span data-stu-id="30da4-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="30da4-107">Aby uzyskać więcej informacji, zobacz [Nullable logiczna operatorów logicznych](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) części [logiczna operatorów logicznych](../operators/boolean-logical-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="30da4-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="30da4-108">Literały</span><span class="sxs-lookup"><span data-stu-id="30da4-108">Literals</span></span>

<span data-ttu-id="30da4-109">Można przypisać wartość logiczną umożliwiającą `bool` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="30da4-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="30da4-110">Można także przypisać wyrażenie, które daje w wyniku `bool` do `bool` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="30da4-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="30da4-111">Wartość domyślna `bool` zmienna jest `false`.</span><span class="sxs-lookup"><span data-stu-id="30da4-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="30da4-112">Wartość domyślna `bool?` zmienna jest `null`.</span><span class="sxs-lookup"><span data-stu-id="30da4-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="30da4-113">Konwersje</span><span class="sxs-lookup"><span data-stu-id="30da4-113">Conversions</span></span>

<span data-ttu-id="30da4-114">W języku C++, wartości typu `bool` można przekonwertować na wartość typu `int`; innymi słowy, `false` jest odpowiednikiem zero i `true` jest odpowiednikiem wartości niezerowych.</span><span class="sxs-lookup"><span data-stu-id="30da4-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="30da4-115">W języku C# jest konwersja między `bool` typu a innymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="30da4-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="30da4-116">Na przykład następująca `if` instrukcja jest nieprawidłowa w języku C#:</span><span class="sxs-lookup"><span data-stu-id="30da4-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="30da4-117">Aby przetestować zmiennej typu `int`, trzeba jawnie porównania wartości, takich jak zero, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="30da4-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="30da4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="30da4-118">Example</span></span>

<span data-ttu-id="30da4-119">W tym przykładzie Wprowadź znak przy użyciu klawiatury i program sprawdza, czy znak danych wejściowych jest literą.</span><span class="sxs-lookup"><span data-stu-id="30da4-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="30da4-120">Jeśli jest literą, sprawdza, czy jest wielką czy małą literą.</span><span class="sxs-lookup"><span data-stu-id="30da4-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="30da4-121">Te testy są wykonywane przy użyciu <xref:System.Char.IsLetter%2A>, i <xref:System.Char.IsLower%2A>, zarówno które zwrotu `bool` typu:</span><span class="sxs-lookup"><span data-stu-id="30da4-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="30da4-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="30da4-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="30da4-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30da4-123">See also</span></span>

- [<span data-ttu-id="30da4-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="30da4-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="30da4-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="30da4-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="30da4-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="30da4-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="30da4-127">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="30da4-127">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="30da4-128">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="30da4-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="30da4-129">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="30da4-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="30da4-130">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="30da4-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
