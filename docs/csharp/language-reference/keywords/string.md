---
title: "string (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8899eb75b1b7c556a1e92f173a4d0ca4135014c8
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="string-c-reference"></a><span data-ttu-id="0774f-102">string (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0774f-102">string (C# Reference)</span></span>
<span data-ttu-id="0774f-103">`string` Typu reprezentuje sekwencję zero lub więcej znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="0774f-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="0774f-104">`string` alias jest <xref:System.String> w .NET.</span><span class="sxs-lookup"><span data-stu-id="0774f-104">`string` is an alias for <xref:System.String> in .NET.</span></span>  
  
 <span data-ttu-id="0774f-105">Mimo że `string` jest typem referencyjnym Operatory równości (`==` i `!=`) są zdefiniowane w celu porównania wartości `string` obiektów, nie odwołuje się do.</span><span class="sxs-lookup"><span data-stu-id="0774f-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="0774f-106">Upraszcza to testowanie równości ciąg bardziej intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="0774f-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="0774f-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0774f-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="0774f-108">Spowoduje to wyświetlenie "True", a następnie "False", ponieważ zawartość ciągi są równoważne, ale `a` i `b` nie odwołują się do tego samego wystąpienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="0774f-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="0774f-109">+ — Operator łączy ciągi:</span><span class="sxs-lookup"><span data-stu-id="0774f-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="0774f-110">Spowoduje to utworzenie obiekt ciągu zawierający "good dzień".</span><span class="sxs-lookup"><span data-stu-id="0774f-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="0774f-111">Ciągi są *niezmienialnych*— zawartość obiekt ciągu nie można zmienić po utworzeniu obiektu, mimo że sprawia, że składnia okaże się, jak można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="0774f-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="0774f-112">Na przykład podczas pisania tego kodu kompilator faktycznie tworzy nowy obiekt ciągu do przechowywania Nowa sekwencja znaków, a ten nowy obiekt jest przypisany do b.</span><span class="sxs-lookup"><span data-stu-id="0774f-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="0774f-113">Ciąg "h" następnie kwalifikuje się do wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0774f-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="0774f-114">Można używać operatora [] dostępu tylko do odczytu do poszczególnych znaków `string`:</span><span class="sxs-lookup"><span data-stu-id="0774f-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="0774f-115">Literały ciągu są typu `string` i mogą być zapisywane w dwóch formach cudzysłowy i @-quoted.</span><span class="sxs-lookup"><span data-stu-id="0774f-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="0774f-116">Jako ciąg, który literały są ujęte w znaki cudzysłowu ("):</span><span class="sxs-lookup"><span data-stu-id="0774f-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="0774f-117">Literały ciągu może zawierać literał znakowy.</span><span class="sxs-lookup"><span data-stu-id="0774f-117">String literals can contain any character literal.</span></span> <span data-ttu-id="0774f-118">Sekwencje unikowe są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="0774f-118">Escape sequences are included.</span></span> <span data-ttu-id="0774f-119">W poniższym przykładzie użyto — sekwencja specjalna `\\` dla ukośnik odwrotny, `\u0066` f, litery i `\n` dla nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="0774f-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="0774f-120">Kod wyjścia `\udddd` (gdzie `dddd` jest liczbą czterocyfrowe) reprezentuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="0774f-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="0774f-121">Kody ucieczki Unicode 8 cyfrowy również są rozpoznawane: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="0774f-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="0774f-122">Literały ciągu dosłownego wyrażenia rozpoczynać `@` i również są ujęte w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="0774f-122">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="0774f-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0774f-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="0774f-124">Zaletą ciągi verbatim to sekwencji unikowych *nie* przetwarzania, które ułatwia zapisu, na przykład w pełni kwalifikowaną nazwą pliku:</span><span class="sxs-lookup"><span data-stu-id="0774f-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="0774f-125">Aby uwzględnić znak podwójnego cudzysłowu w @-quoted string, dwukrotnie ją:</span><span class="sxs-lookup"><span data-stu-id="0774f-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="0774f-126">Do innych celów z `@` znak specjalny, zobacz [@ — identyfikator dosłownego wyrażenia](../tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="0774f-126">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>  
  
 <span data-ttu-id="0774f-127">Aby uzyskać więcej informacji na temat ciągów w języku C#, zobacz [ciągów](../../../csharp/programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="0774f-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0774f-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="0774f-128">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0774f-129">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0774f-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0774f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0774f-130">See Also</span></span>  
 [<span data-ttu-id="0774f-131">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0774f-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0774f-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0774f-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0774f-133">Najlepsze rozwiązania dotyczące używania ciągów</span><span class="sxs-lookup"><span data-stu-id="0774f-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)  
 [<span data-ttu-id="0774f-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0774f-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0774f-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0774f-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0774f-136">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="0774f-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="0774f-137">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="0774f-137">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="0774f-138">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="0774f-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="0774f-139">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="0774f-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="0774f-140">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="0774f-140">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
