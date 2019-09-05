---
title: 'Instrukcje: Określanie, czy ciąg reprezentuje znak wartości liczbowej C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 8fc5051893882a6dbdbb4c9097949794d4430a93
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252954"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="31d8d-102">Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="31d8d-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="31d8d-103">Aby określić, czy ciąg jest prawidłową reprezentacją określonego typu liczbowego, należy użyć statycznej `TryParse` metody, która jest implementowana przez wszystkie pierwotne typy liczbowe, a także typy takie jak <xref:System.DateTime> i <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="31d8d-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="31d8d-104">Poniższy przykład pokazuje, jak ustalić, czy "108" jest prawidłową [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="31d8d-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="31d8d-105">Jeśli ciąg zawiera znaki nienumeryczne lub wartość liczbowa jest za duża lub za mała dla określonego typu, `TryParse` zwraca wartość false i ustawia parametr out na wartość zero.</span><span class="sxs-lookup"><span data-stu-id="31d8d-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="31d8d-106">W przeciwnym razie zwraca wartość true i ustawia parametr out na wartość liczbową ciągu.</span><span class="sxs-lookup"><span data-stu-id="31d8d-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31d8d-107">Ciąg może zawierać tylko znaki numeryczne i nadal nie jest prawidłowy dla typu, którego `TryParse` Metoda jest używana.</span><span class="sxs-lookup"><span data-stu-id="31d8d-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="31d8d-108">Na przykład "256" nie jest prawidłową wartością dla `byte` , ale jest prawidłowy dla. `int`</span><span class="sxs-lookup"><span data-stu-id="31d8d-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="31d8d-109">"98,6" nie jest prawidłową wartością dla `int` , ale jest prawidłowy. `decimal`</span><span class="sxs-lookup"><span data-stu-id="31d8d-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31d8d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="31d8d-110">Example</span></span>  
 <span data-ttu-id="31d8d-111">W poniższych przykładach pokazano `TryParse` `long`, jak używać z reprezentacjami ciągów wartości `decimal` , `byte`, i.</span><span class="sxs-lookup"><span data-stu-id="31d8d-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="31d8d-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="31d8d-112">Robust Programming</span></span>  
 <span data-ttu-id="31d8d-113">Pierwotne typy liczbowe implementują `Parse` również metodę statyczną, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą.</span><span class="sxs-lookup"><span data-stu-id="31d8d-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="31d8d-114">`TryParse`jest zwykle bardziej wydajne, ponieważ zwraca wartość false, jeśli liczba jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="31d8d-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="31d8d-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="31d8d-115">.NET Framework Security</span></span>  
 <span data-ttu-id="31d8d-116">Zawsze używaj `TryParse` metod lub `Parse` do sprawdzania poprawności danych wejściowych użytkownika z kontrolek, takich jak pola tekstowe i pola kombi.</span><span class="sxs-lookup"><span data-stu-id="31d8d-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d8d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31d8d-117">See also</span></span>

- [<span data-ttu-id="31d8d-118">Instrukcje: Konwertuj tablicę bajtów na liczbę całkowitą</span><span class="sxs-lookup"><span data-stu-id="31d8d-118">How to: Convert a byte Array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="31d8d-119">Instrukcje: Konwertuj ciąg na liczbę</span><span class="sxs-lookup"><span data-stu-id="31d8d-119">How to: Convert a String to a Number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="31d8d-120">Instrukcje: Konwertuj między ciągi szesnastkowe i typy liczbowe</span><span class="sxs-lookup"><span data-stu-id="31d8d-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="31d8d-121">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="31d8d-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="31d8d-122">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="31d8d-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
