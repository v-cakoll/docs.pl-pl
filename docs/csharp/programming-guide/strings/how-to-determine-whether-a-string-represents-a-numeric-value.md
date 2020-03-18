---
title: Jak ustalić, czy ciąg reprezentuje wartość liczbową - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 15a21a6298f8f0a57e0189554246202b220dd259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157068"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="04340-102">Jak ustalić, czy ciąg reprezentuje wartość liczbową (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="04340-102">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="04340-103">Aby ustalić, czy ciąg jest prawidłową reprezentacją określonego typu `TryParse` liczbowego, należy użyć metody statycznej implementacyjnej przez <xref:System.DateTime> <xref:System.Net.IPAddress>wszystkie pierwotne typy liczbowe, a także według typów, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="04340-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="04340-104">W poniższym przykładzie pokazano, jak ustalić, czy "108" jest prawidłowym [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="04340-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="04340-105">Jeśli ciąg zawiera znaki nieliczbowe lub wartość liczbowa jest zbyt duża lub `TryParse` zbyt mała dla określonego typu, zwraca wartość false i ustawia parametr out na zero.</span><span class="sxs-lookup"><span data-stu-id="04340-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="04340-106">W przeciwnym razie zwraca true i ustawia out parametr u wartości liczbowej ciągu.</span><span class="sxs-lookup"><span data-stu-id="04340-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04340-107">Ciąg może zawierać tylko znaki liczbowe i nadal `TryParse` nie jest prawidłowy dla typu, którego metody używasz.</span><span class="sxs-lookup"><span data-stu-id="04340-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="04340-108">Na przykład "256" nie jest `byte` prawidłową wartością, ale jest prawidłowa dla `int`.</span><span class="sxs-lookup"><span data-stu-id="04340-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="04340-109">"98.6" nie jest prawidłową `int` wartością, `decimal`ale jest prawidłową wartością.</span><span class="sxs-lookup"><span data-stu-id="04340-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04340-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="04340-110">Example</span></span>  
 <span data-ttu-id="04340-111">W poniższych przykładach `TryParse` przedstawiono sposób używania `long` `byte`z `decimal` reprezentacjami ciągów i wartościami.</span><span class="sxs-lookup"><span data-stu-id="04340-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="04340-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="04340-112">Robust Programming</span></span>  
 <span data-ttu-id="04340-113">Pierwotne typy liczbowe implementują również metodę `Parse` statyczną, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą.</span><span class="sxs-lookup"><span data-stu-id="04340-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="04340-114">`TryParse`jest ogólnie bardziej wydajne, ponieważ po prostu zwraca false, jeśli liczba jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="04340-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="04340-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04340-115">.NET Framework Security</span></span>  
 <span data-ttu-id="04340-116">Zawsze `TryParse` używaj `Parse` metod lub do sprawdzania poprawności danych wejściowych użytkownika z formantów, takich jak pola tekstowe i pola kombi.</span><span class="sxs-lookup"><span data-stu-id="04340-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04340-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04340-117">See also</span></span>

- [<span data-ttu-id="04340-118">Konwertowanie tablicy typu Byte na liczbę całkowitą</span><span class="sxs-lookup"><span data-stu-id="04340-118">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="04340-119">Konwertowanie ciągu na liczbę</span><span class="sxs-lookup"><span data-stu-id="04340-119">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="04340-120">Konwertowanie ciągów szesnastkowych na typy liczbowe</span><span class="sxs-lookup"><span data-stu-id="04340-120">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="04340-121">Analizowanie ciągów numerycznych</span><span class="sxs-lookup"><span data-stu-id="04340-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="04340-122">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="04340-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
