---
title: "Porady: konwertowanie ciągu na liczbę (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3dc67bc2f25bba14df0e3ce6859bb8bc9094871c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="74034-102">Porady: konwertowanie ciągu na liczbę (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="74034-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="74034-103">Możesz przekonwertować [ciąg](../../../csharp/language-reference/keywords/string.md) na liczbę za pomocą metod w <xref:System.Convert> klasy lub przy użyciu `TryParse` znaleziono metody na różne typy liczbowe (int, long, float, itp.).</span><span class="sxs-lookup"><span data-stu-id="74034-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="74034-104">Jeśli masz ciąg jest nieco bardziej wydajne i bezpośrednie wywoływanie `TryParse` — metoda (na przykład `int.TryParse("11")`).</span><span class="sxs-lookup"><span data-stu-id="74034-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="74034-105">Przy użyciu `Convert` metoda jest bardziej użyteczna w przypadku ogólnych obiekty, które implementują <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="74034-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="74034-106">Można użyć `Parse` lub `TryParse` metody na typ liczbowy oczekiwany ciąg zawiera, takich jak <xref:System.Int32?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="74034-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="74034-107"><xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Używa metody <xref:System.Int32.Parse%2A> wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="74034-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="74034-108">Jeśli ciąg nie jest prawidłowym formatem `Parse` zgłasza wyjątek `TryParse` zwraca [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="74034-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74034-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="74034-109">Example</span></span>  
 <span data-ttu-id="74034-110">`Parse` i `TryParse` metody Ignoruj odstępy na początku i na końcu ciągu, ale wszystkie inne znaki muszą być znaki, które tworzą odpowiedni typ liczbowy (int, long, ulong, float, decimal, itp.).</span><span class="sxs-lookup"><span data-stu-id="74034-110">The `Parse` and `TryParse` methods ignore whitespace at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="74034-111">Żadnych spacji w ciągu znaków, które tworzą numer spowodować wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="74034-111">Any whitespace within the characters that form the number cause an error.</span></span>  <span data-ttu-id="74034-112">Na przykład można użyć `decimal.TryParse` można przeanalizować "10", "10.3", "10", ale nie można użyć tej metody można przeanalizować 10 "10 X", "1 0" (Uwaga miejsca), "10. 3" (Uwaga miejsca), "10e1" (`float.TryParse` działa w tym miejscu) i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="74034-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="74034-113">Poniższe przykłady pokazują zarówno zakończone powodzeniem i niepowodzeniem wywołania `Parse` i `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="74034-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="74034-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="74034-114">Example</span></span>  
 <span data-ttu-id="74034-115">W poniższej tabeli przedstawiono niektóre metody z <xref:System.Convert> klasy, który można użyć.</span><span class="sxs-lookup"><span data-stu-id="74034-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="74034-116">Typ liczbowy</span><span class="sxs-lookup"><span data-stu-id="74034-116">Numeric Type</span></span>|<span data-ttu-id="74034-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="74034-117">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="74034-118">W tym przykładzie wywołuje <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metody można skonwertować danych wejściowych [ciąg](../../../csharp/language-reference/keywords/string.md) do [int](../../../csharp/language-reference/keywords/int.md) .</span><span class="sxs-lookup"><span data-stu-id="74034-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="74034-119">Dwa najczęściej wyjątki, które mogą być generowane przez tę metodę przechwytuje kod <xref:System.FormatException> i <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="74034-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="74034-120">Jeśli liczbę można zwiększyć bez przepełnienia lokalizacji magazynu liczb całkowitych, program dodaje do wyniku 1 i drukuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="74034-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="74034-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74034-121">See Also</span></span>  
 [<span data-ttu-id="74034-122">Typy</span><span class="sxs-lookup"><span data-stu-id="74034-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="74034-123">Porady: Określanie, czy ciąg reprezentuje wartość numeryczną</span><span class="sxs-lookup"><span data-stu-id="74034-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [<span data-ttu-id="74034-124">Narzędzie formatowania programu .NET framework 4</span><span class="sxs-lookup"><span data-stu-id="74034-124">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
