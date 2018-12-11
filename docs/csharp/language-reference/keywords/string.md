---
title: string (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: 66b1729363878f69f868b8b8fd6e9e7011426f27
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153127"
---
# <a name="string-c-reference"></a><span data-ttu-id="04cbf-102">string (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="04cbf-102">string (C# Reference)</span></span>

<span data-ttu-id="04cbf-103">`string` Typu reprezentuje sekwencję zero lub więcej znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="04cbf-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="04cbf-104">`string` jest aliasem dla <xref:System.String> na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="04cbf-104">`string` is an alias for <xref:System.String> in .NET.</span></span>

<span data-ttu-id="04cbf-105">Mimo że `string` jest typem referencyjnym, operatory równości (`==` i `!=`) są zdefiniowane w celu porównania wartości `string` obiektów, nie odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="04cbf-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="04cbf-106">To sprawia, że testowanie dla równości ciągu bardziej intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="04cbf-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="04cbf-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="04cbf-107">For example:</span></span>

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

<span data-ttu-id="04cbf-108">Spowoduje to wyświetlenie "True" i następnie "False", ponieważ zawartość ciągi są równoważne, ale `a` i `b` odwołuje się do tego samego wystąpienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="04cbf-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="04cbf-109">+ — Operator łączy ciągi:</span><span class="sxs-lookup"><span data-stu-id="04cbf-109">The + operator concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="04cbf-110">Spowoduje to utworzenie obiekt ciągu zawierający "good morning".</span><span class="sxs-lookup"><span data-stu-id="04cbf-110">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="04cbf-111">Ciągi są *niezmienne*— nie można zmienić zawartość obiekt ciągu, po utworzeniu obiektu, mimo że składnia sprawia, że wyświetlane tak, jakby można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="04cbf-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="04cbf-112">Na przykład kiedy piszesz kod, kompilator tworzy obiekt ciągu do przechowywania nowej sekwencji znaków, a nowy obiekt jest przypisany do b.</span><span class="sxs-lookup"><span data-stu-id="04cbf-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="04cbf-113">Ciąg "h" jest uprawniona do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="04cbf-113">The string "h" is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="04cbf-114">[] — Operator może służyć do dostępu tylko do odczytu do pojedynczych znaków z `string`:</span><span class="sxs-lookup"><span data-stu-id="04cbf-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="04cbf-115">Literały ciągów są typu `string` i mogą być zapisywane w dwóch formach, w cudzysłowach i @-quoted.</span><span class="sxs-lookup"><span data-stu-id="04cbf-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="04cbf-116">Jako ciąg, który literały są ujęte w podwójny cudzysłów ("):</span><span class="sxs-lookup"><span data-stu-id="04cbf-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="04cbf-117">Literały ciągu może zawierać dowolny znak literału.</span><span class="sxs-lookup"><span data-stu-id="04cbf-117">String literals can contain any character literal.</span></span> <span data-ttu-id="04cbf-118">Sekwencje unikowe są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="04cbf-118">Escape sequences are included.</span></span> <span data-ttu-id="04cbf-119">W poniższym przykładzie użyto sekwencja unikowa `\\` dla ukośnikiem, po którym `\u0066` literę f, i `\n` dla nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="04cbf-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> <span data-ttu-id="04cbf-120">Kod escape `\udddd` (gdzie `dddd` jest liczbę czterocyfrową) reprezentuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="04cbf-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="04cbf-121">Kodów wyjścia Unicode ośmiu cyfr, również są rozpoznawane: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="04cbf-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="04cbf-122">Ciąg Verbatim literały rozpoczynać `@` i również są ujęte w podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="04cbf-122">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="04cbf-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="04cbf-123">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="04cbf-124">Zaletą ciągi verbatim jest, że sekwencje ucieczki to *nie* przetwarzany, która ułatwia zapisu, na przykład w pełni kwalifikowaną nazwą pliku:</span><span class="sxs-lookup"><span data-stu-id="04cbf-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="04cbf-125">Aby uwzględnić znak podwójnego cudzysłowu w @-quoted ciąg, podwój go:</span><span class="sxs-lookup"><span data-stu-id="04cbf-125">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

<span data-ttu-id="04cbf-126">Inne zastosowania `@` znaki specjalne, zobacz [@ — identyfikator dosłownego wyrażenia](../tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="04cbf-126">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>

<span data-ttu-id="04cbf-127">Aby uzyskać więcej informacji na temat ciągów w języku C#, zobacz [ciągi](../../programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="04cbf-127">For more information about strings in C#, see [Strings](../../programming-guide/strings/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="04cbf-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="04cbf-128">Example</span></span>

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a><span data-ttu-id="04cbf-129">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="04cbf-129">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="04cbf-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04cbf-130">See also</span></span>

- [<span data-ttu-id="04cbf-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="04cbf-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="04cbf-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="04cbf-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="04cbf-133">Najlepsze rozwiązania dotyczące używania ciągów</span><span class="sxs-lookup"><span data-stu-id="04cbf-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="04cbf-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="04cbf-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="04cbf-135">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="04cbf-135">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="04cbf-136">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="04cbf-136">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="04cbf-137">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="04cbf-137">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="04cbf-138">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="04cbf-138">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="04cbf-139">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="04cbf-139">Formatting Numeric Results Table</span></span>](formatting-numeric-results-table.md)
