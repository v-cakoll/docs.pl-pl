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
ms.openlocfilehash: f92a44283e59bd80421758a63b40bc5289c3628b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="string-c-reference"></a>string (odwołanie w C#)
`string` Typu reprezentuje sekwencję zero lub więcej znaków Unicode. `string` alias jest <xref:System.String> w .NET.  
  
 Mimo że `string` jest typem referencyjnym Operatory równości (`==` i `!=`) są zdefiniowane w celu porównania wartości `string` obiektów, nie odwołuje się do. Upraszcza to testowanie równości ciąg bardziej intuicyjne. Na przykład:  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Spowoduje to wyświetlenie "True", a następnie "False", ponieważ zawartość ciągi są równoważne, ale `a` i `b` nie odwołują się do tego samego wystąpienia ciągu.  
  
 + — Operator łączy ciągi:  
  
```csharp  
string a = "good " + "morning";  
```  
  
 Spowoduje to utworzenie obiekt ciągu zawierający "good dzień".  
  
 Ciągi są *niezmienialnych*— zawartość obiekt ciągu nie można zmienić po utworzeniu obiektu, mimo że sprawia, że składnia okaże się, jak można to zrobić. Na przykład podczas pisania tego kodu kompilator faktycznie tworzy nowy obiekt ciągu do przechowywania Nowa sekwencja znaków, a ten nowy obiekt jest przypisany do b. Ciąg "h" następnie kwalifikuje się do wyrzucanie elementów bezużytecznych.  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 Można używać operatora [] dostępu tylko do odczytu do poszczególnych znaków `string`:  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Literały ciągu są typu `string` i mogą być zapisywane w dwóch formach cudzysłowy i @-quoted. Jako ciąg, który literały są ujęte w znaki cudzysłowu ("):  
  
```csharp  
"good morning"  // a string literal  
```  
  
 Literały ciągu może zawierać literał znakowy. Sekwencje unikowe są uwzględniane. W poniższym przykładzie użyto — sekwencja specjalna `\\` dla ukośnik odwrotny, `\u0066` f, litery i `\n` dla nowego wiersza.  
  
```csharp  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  Kod wyjścia `\udddd` (gdzie `dddd` jest liczbą czterocyfrowe) reprezentuje znak Unicode U +`dddd`. Kody ucieczki Unicode 8 cyfrowy również są rozpoznawane: `\Udddddddd`.  
  
 Literały ciągu dosłownego wyrażenia rozpoczynać `@` i również są ujęte w cudzysłów. Na przykład:  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 Zaletą ciągi verbatim to sekwencji unikowych *nie* przetwarzania, które ułatwia zapisu, na przykład w pełni kwalifikowaną nazwą pliku:  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Aby uwzględnić znak podwójnego cudzysłowu w @-quoted string, dwukrotnie ją:  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Do innych celów z `@` znak specjalny, zobacz [@ — identyfikator dosłownego wyrażenia](../tokens/verbatim.md).  
  
 Aby uzyskać więcej informacji na temat ciągów w języku C#, zobacz [ciągów](../../../csharp/programming-guide/strings/index.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Najlepsze rozwiązania dotyczące używania ciągów](../../../standard/base-types/best-practices-strings.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
 [Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)  
 [Tworzenie nowych ciągów](../../../standard/base-types/creating-new.md)  
 [Formatowanie tabeli wyników liczbowych](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
