---
title: "string (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
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
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 87df2b158b173072aad5257594e1b1482ae61067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="string-c-reference"></a><span data-ttu-id="5e0a7-102">string (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5e0a7-102">string (C# Reference)</span></span>
<span data-ttu-id="5e0a7-103">`string` Typu reprezentuje sekwencję zero lub więcej znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="5e0a7-104">`string`alias jest <xref:System.String> w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-104">`string` is an alias for <xref:System.String> in the .NET Framework.</span></span>  
  
 <span data-ttu-id="5e0a7-105">Mimo że `string` jest typem referencyjnym Operatory równości (`==` i `!=`) są zdefiniowane w celu porównania wartości `string` obiektów, nie odwołuje się do.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="5e0a7-106">Upraszcza to testowanie równości ciąg bardziej intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="5e0a7-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="5e0a7-108">Spowoduje to wyświetlenie "True", a następnie "False", ponieważ zawartość ciągi są równoważne, ale `a` i `b` nie odwołują się do tego samego wystąpienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="5e0a7-109">+ — Operator łączy ciągi:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="5e0a7-110">Spowoduje to utworzenie obiekt ciągu zawierający "good dzień".</span><span class="sxs-lookup"><span data-stu-id="5e0a7-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="5e0a7-111">Ciągi są *niezmienialnych*— zawartość obiekt ciągu nie można zmienić po utworzeniu obiektu, mimo że sprawia, że składnia okaże się, jak można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="5e0a7-112">Na przykład podczas pisania tego kodu kompilator faktycznie tworzy nowy obiekt ciągu do przechowywania Nowa sekwencja znaków, a ten nowy obiekt jest przypisany do b.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="5e0a7-113">Ciąg "h" następnie kwalifikuje się do wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="5e0a7-114">Można używać operatora [] dostępu tylko do odczytu do poszczególnych znaków `string`:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="5e0a7-115">Literały ciągu są typu `string` i mogą być zapisywane w dwóch formach cudzysłowy i @-quoted.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="5e0a7-116">Jako ciąg, który literały są ujęte w znaki cudzysłowu ("):</span><span class="sxs-lookup"><span data-stu-id="5e0a7-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="5e0a7-117">Literały ciągu może zawierać literał znakowy.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-117">String literals can contain any character literal.</span></span> <span data-ttu-id="5e0a7-118">Sekwencje unikowe są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-118">Escape sequences are included.</span></span> <span data-ttu-id="5e0a7-119">W poniższym przykładzie użyto — sekwencja specjalna `\\` dla ukośnik odwrotny, `\u0066` f, litery i `\n` dla nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="5e0a7-120">Kod wyjścia `\udddd` (gdzie `dddd` jest liczbą czterocyfrowe) reprezentuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="5e0a7-121">Kody ucieczki Unicode 8 cyfrowy również są rozpoznawane: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="5e0a7-122">Literały ciągu dosłownego wyrażenia rozpoczynać i również są ujęte w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-122">Verbatim string literals start with @ and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="5e0a7-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="5e0a7-124">Zaletą ciągi verbatim to sekwencji unikowych *nie* przetwarzania, które ułatwia zapisu, na przykład w pełni kwalifikowaną nazwą pliku:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="5e0a7-125">Aby uwzględnić znak podwójnego cudzysłowu w @-quoted string, dwukrotnie ją:</span><span class="sxs-lookup"><span data-stu-id="5e0a7-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="5e0a7-126">Użycie innego znaku @ odwołuje się do użycia do ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) identyfikatorów, które są słowa kluczowe języka C#.</span><span class="sxs-lookup"><span data-stu-id="5e0a7-126">Another use of the @ symbol is to use referenced ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) identifiers that are C# keywords.</span></span>  
  
 <span data-ttu-id="5e0a7-127">Aby uzyskać więcej informacji na temat ciągów w języku C#, zobacz [ciągów](../../../csharp/programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e0a7-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e0a7-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e0a7-128">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5e0a7-129">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5e0a7-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e0a7-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e0a7-130">See Also</span></span>  
 [<span data-ttu-id="5e0a7-131">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="5e0a7-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5e0a7-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5e0a7-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5e0a7-133">Najlepsze rozwiązania dotyczące używania ciągów</span><span class="sxs-lookup"><span data-stu-id="5e0a7-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)  
 [<span data-ttu-id="5e0a7-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5e0a7-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5e0a7-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5e0a7-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5e0a7-136">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="5e0a7-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="5e0a7-137">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="5e0a7-137">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="5e0a7-138">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="5e0a7-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="5e0a7-139">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="5e0a7-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="5e0a7-140">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="5e0a7-140">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
