---
title: 'Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: a20850e6fc34b28975dbb2b6be819bf2e88f1f27
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244560"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="cf199-102">Instrukcje: Określanie, czy ciąg reprezentuje wartość numeryczną (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="cf199-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="cf199-103">Aby ustalić, czy ciąg jest prawidłową reprezentacją określonego typu liczbowego, używa się statycznej `TryParse` metodę, która jest zaimplementowana przez wszystkich pierwotnych typów liczbowych, a także typy takie jak <xref:System.DateTime> i <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="cf199-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="cf199-104">Poniższy przykład pokazuje, jak ustalić, czy jest nieprawidłowy "108" warunki [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="cf199-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="cf199-105">Jeśli ciąg zawiera znaki nienumeryczne lub wartość liczbowa jest zbyt duży lub za mały dla tego typu został określony, `TryParse` zwraca wartość false, a także Ustawia parametr out zero.</span><span class="sxs-lookup"><span data-stu-id="cf199-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="cf199-106">W przeciwnym razie zwraca wartość true i Ustawia parametr out liczbową wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="cf199-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf199-107">Ciąg może zawierać tylko znaki numeryczne i nadal nie jest prawidłowa dla typu którego `TryParse` używanej metody.</span><span class="sxs-lookup"><span data-stu-id="cf199-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="cf199-108">Na przykład "256" nie jest prawidłową wartością dla `byte` , ale jest on prawidłowy dla `int`.</span><span class="sxs-lookup"><span data-stu-id="cf199-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="cf199-109">"98.6" nie jest prawidłową wartością dla `int` , ale jest on prawidłowy `decimal`.</span><span class="sxs-lookup"><span data-stu-id="cf199-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf199-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf199-110">Example</span></span>  
 <span data-ttu-id="cf199-111">W poniższych przykładach pokazano sposób użycia `TryParse` za pomocą ciągów reprezentujących `long`, `byte`, i `decimal` wartości.</span><span class="sxs-lookup"><span data-stu-id="cf199-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cf199-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cf199-112">Robust Programming</span></span>  
 <span data-ttu-id="cf199-113">Pierwotny liczbowe również typy implementują `Parse` statyczną metodę, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą.</span><span class="sxs-lookup"><span data-stu-id="cf199-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="cf199-114">`TryParse` jest zazwyczaj bardziej efektywne, ponieważ po prostu zwraca wartość false, jeśli liczba jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="cf199-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cf199-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="cf199-115">.NET Framework Security</span></span>  
 <span data-ttu-id="cf199-116">Zawsze używaj `TryParse` lub `Parse` metod, aby sprawdzić dane wejściowe użytkownika z formantów takich jak pola tekstowe i pola kombi.</span><span class="sxs-lookup"><span data-stu-id="cf199-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf199-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf199-117">See Also</span></span>

- [<span data-ttu-id="cf199-118">Instrukcje: Konwertowanie tablicy typu byte na liczbę całkowitą</span><span class="sxs-lookup"><span data-stu-id="cf199-118">How to: Convert a byte Array to an int</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
- [<span data-ttu-id="cf199-119">Instrukcje: Konwertowanie ciągu na liczbę</span><span class="sxs-lookup"><span data-stu-id="cf199-119">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
- [<span data-ttu-id="cf199-120">Instrukcje: Konwertowanie ciągów szesnastkowych, które typy liczbowe</span><span class="sxs-lookup"><span data-stu-id="cf199-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
- [<span data-ttu-id="cf199-121">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="cf199-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)  
- [<span data-ttu-id="cf199-122">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="cf199-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
