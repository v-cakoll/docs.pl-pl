---
title: "Porady: określanie, czy ciąg reprezentuje wartość numeryczną (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 850c5d0e7a246b2319ba841dae9884c90390d38c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="1291a-102">Porady: określanie, czy ciąg reprezentuje wartość numeryczną (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1291a-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="1291a-103">Aby określić, czy ciąg jest prawidłowy reprezentację określonego typu liczbowego, użyj statycznych `TryParse` metodę, która jest zaimplementowana przez wszystkie pierwotne typy liczbowe, a także typy takich jak <xref:System.DateTime> i <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="1291a-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="1291a-104">Poniższy przykład przedstawia sposób określania, czy jest prawidłową "108" warunki [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="1291a-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="1291a-105">Jeśli ciąg zawiera znaków nienumerycznych lub wartość liczbowa jest za duża albo za mała dla tego typu określono, `TryParse` zwraca wartość false i Ustawia parametr out na zero.</span><span class="sxs-lookup"><span data-stu-id="1291a-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="1291a-106">W przeciwnym razie zwraca wartość true i Ustawia parametr out liczbowa wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="1291a-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1291a-107">Ciąg może zawierać tylko cyfry i nadal nie jest prawidłowa dla typu którego `TryParse` używanej metody.</span><span class="sxs-lookup"><span data-stu-id="1291a-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="1291a-108">Na przykład "256" nie jest prawidłową wartością dla `byte` , ale jest on prawidłowy dla `int`.</span><span class="sxs-lookup"><span data-stu-id="1291a-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="1291a-109">"98.6" nie jest prawidłową wartością dla `int` jest prawidłowy, ale `decimal`.</span><span class="sxs-lookup"><span data-stu-id="1291a-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1291a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1291a-110">Example</span></span>  
 <span data-ttu-id="1291a-111">W poniższych przykładach pokazano, jak używać `TryParse` z reprezentacji ciągu `long`, `byte`, i `decimal` wartości.</span><span class="sxs-lookup"><span data-stu-id="1291a-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1291a-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1291a-112">Robust Programming</span></span>  
 <span data-ttu-id="1291a-113">Liczbowe pierwotne typy również wdrożenie `Parse` statycznej metody, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą.</span><span class="sxs-lookup"><span data-stu-id="1291a-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="1291a-114">`TryParse`jest zazwyczaj bardziej wydajne, ponieważ właśnie zwraca wartość FAŁSZ, jeśli liczba jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="1291a-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1291a-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1291a-115">.NET Framework Security</span></span>  
 <span data-ttu-id="1291a-116">Zawsze używaj `TryParse` lub `Parse` metod do sprawdzania poprawności danych wejściowych użytkownika z formanty, takie jak pola tekstowe i pola kombi.</span><span class="sxs-lookup"><span data-stu-id="1291a-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1291a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1291a-117">See Also</span></span>  
 [<span data-ttu-id="1291a-118">Porady: Konwertowanie tablicy typu byte na liczbę całkowitą</span><span class="sxs-lookup"><span data-stu-id="1291a-118">How to: Convert a byte Array to an int</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
 [<span data-ttu-id="1291a-119">Porady: konwertowanie ciągu na liczbę</span><span class="sxs-lookup"><span data-stu-id="1291a-119">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
 [<span data-ttu-id="1291a-120">Porady: Konwertowanie ciągów szesnastkowych, które typy numeryczne</span><span class="sxs-lookup"><span data-stu-id="1291a-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
 [<span data-ttu-id="1291a-121">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="1291a-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)  
 [<span data-ttu-id="1291a-122">Formatowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="1291a-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
