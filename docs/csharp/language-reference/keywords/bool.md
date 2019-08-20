---
title: bool — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 3e4e83b52cd6b275e68039693c774f6490f2b88f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606060"
---
# <a name="bool-c-reference"></a><span data-ttu-id="198ad-102">bool (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="198ad-102">bool (C# Reference)</span></span>

<span data-ttu-id="198ad-103">Słowo kluczowe jest <xref:System.Boolean?displayProperty=nameWithType>aliasem. `bool`</span><span class="sxs-lookup"><span data-stu-id="198ad-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="198ad-104">Służy do deklarowania zmiennych do przechowywania wartości logicznych: [true](true-literal.md) i [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="198ad-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="198ad-105">Użyj tego `bool?` typu, jeśli potrzebujesz obsługi logiki trójwarstwowej, na przykład podczas pracy z bazami danych, które obsługują typ Boolean o wartości 3.</span><span class="sxs-lookup"><span data-stu-id="198ad-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="198ad-106">W przypadku `&` `|` operandów wstępnie zdefiniowane operatory i obsługują logikę z trzema wartościami. `bool?`</span><span class="sxs-lookup"><span data-stu-id="198ad-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="198ad-107">Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="198ad-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="198ad-108">Literały</span><span class="sxs-lookup"><span data-stu-id="198ad-108">Literals</span></span>

<span data-ttu-id="198ad-109">Do `bool` zmiennej można przypisać wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="198ad-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="198ad-110">Można również przypisać wyrażenie, które daje `bool` w wyniku `bool` zmienną.</span><span class="sxs-lookup"><span data-stu-id="198ad-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="198ad-111">Wartość `bool` domyślna zmiennej to `false`.</span><span class="sxs-lookup"><span data-stu-id="198ad-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="198ad-112">Wartość `bool?` domyślna zmiennej to `null`.</span><span class="sxs-lookup"><span data-stu-id="198ad-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="198ad-113">Konwersje</span><span class="sxs-lookup"><span data-stu-id="198ad-113">Conversions</span></span>

<span data-ttu-id="198ad-114">W C++programie wartość typu `bool` może zostać przekonwertowana na wartość typu `int`; innymi słowy, `false` jest równoznaczna z zerem i `true` jest odpowiednikiem wartości niezerowych.</span><span class="sxs-lookup"><span data-stu-id="198ad-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="198ad-115">W C#programie nie ma konwersji między `bool` typem i innymi typami.</span><span class="sxs-lookup"><span data-stu-id="198ad-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="198ad-116">Na przykład następująca `if` instrukcja jest nieprawidłowa w: C#</span><span class="sxs-lookup"><span data-stu-id="198ad-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="198ad-117">Aby przetestować zmienną typu `int`, należy jawnie porównać ją z wartością, taką jak zero, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="198ad-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="198ad-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="198ad-118">Example</span></span>

<span data-ttu-id="198ad-119">W tym przykładzie wprowadzasz znak z klawiatury, a program sprawdza, czy znak wejściowy jest literą.</span><span class="sxs-lookup"><span data-stu-id="198ad-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="198ad-120">Jeśli jest to litera, sprawdza, czy jest mała lub Wielka litera.</span><span class="sxs-lookup"><span data-stu-id="198ad-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="198ad-121">Te testy są wykonywane z <xref:System.Char.IsLetter%2A>, i <xref:System.Char.IsLower%2A>, z których `bool` oba zwracają typ:</span><span class="sxs-lookup"><span data-stu-id="198ad-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="198ad-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="198ad-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="198ad-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="198ad-123">See also</span></span>

- [<span data-ttu-id="198ad-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="198ad-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="198ad-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="198ad-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="198ad-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="198ad-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="198ad-127">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="198ad-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="198ad-128">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="198ad-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="198ad-129">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="198ad-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="198ad-130">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="198ad-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
