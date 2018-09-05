---
title: 'Porady: konwertowanie ciągu na liczbę (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 1f11ba3981b219d3b3a7817afd75fa78f2ccf78a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521756"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="535cf-102">Porady: konwertowanie ciągu na liczbę (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="535cf-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="535cf-103">Można przekonwertować [ciąg](../../../csharp/language-reference/keywords/string.md) do liczby przy użyciu metod w <xref:System.Convert> klasy lub przy użyciu `TryParse` znaleźć metodę na różne typy liczbowe (int, long, float, itp.).</span><span class="sxs-lookup"><span data-stu-id="535cf-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="535cf-104">Jeśli masz ciąg, jest nieco bardziej efektywne i prostego do wywołania `TryParse` — metoda (na przykład [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)).</span><span class="sxs-lookup"><span data-stu-id="535cf-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)).</span></span>  <span data-ttu-id="535cf-105">Za pomocą <xref:System.Convert> metoda jest bardziej użyteczna w przypadku ogólnych obiekty, które implementują <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="535cf-105">Using a <xref:System.Convert> method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="535cf-106">Możesz użyć `Parse` lub `TryParse` metody na typ liczbowy, oczekujesz, że zawiera ciąg, taki jak <xref:System.Int32?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="535cf-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="535cf-107"><xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Metoda używa <xref:System.Int32.Parse%2A> wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="535cf-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="535cf-108">Jeśli ciąg nie jest w prawidłowym formacie `Parse` zgłasza wyjątek `TryParse` zwraca [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="535cf-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="535cf-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="535cf-109">Example</span></span>  
 <span data-ttu-id="535cf-110">`Parse` i `TryParse` metody Ignoruj biały znak na początku i na końcu ciągu, ale wszystkie inne znaki musi być znaki, które tworzą odpowiedni typ liczbowy (int, long, ulong, float, dziesiętny, itp.).</span><span class="sxs-lookup"><span data-stu-id="535cf-110">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="535cf-111">Dowolny biały obszar w ciągu znaków, które tworzą numer powodują wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="535cf-111">Any white space within the characters that form the number cause an error.</span></span>  <span data-ttu-id="535cf-112">Na przykład, można użyć `decimal.TryParse` można przeanalizować "10", "10.3", "10", ale możesz nie można użyć tej metody można przeanalizować 10 z "10 X", "1 0" (Uwaga miejsca), "10. 3" (Uwaga miejsca), "10e1" (`float.TryParse` działające w tym miejscu), i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="535cf-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="535cf-113">W przykładach pokazano zarówno pomyślnie, jak i nieudane wywołania `Parse` i `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="535cf-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="535cf-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="535cf-114">Example</span></span>  
 <span data-ttu-id="535cf-115">W poniższej tabeli wymieniono niektóre metody z <xref:System.Convert> klasę, która umożliwia.</span><span class="sxs-lookup"><span data-stu-id="535cf-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="535cf-116">Typ liczbowy</span><span class="sxs-lookup"><span data-stu-id="535cf-116">Numeric Type</span></span>|<span data-ttu-id="535cf-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="535cf-117">Method</span></span>|  
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
  
 <span data-ttu-id="535cf-118">Ten przykład wywołuje <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metodę, aby konwertować dane wejściowe [ciąg](../../../csharp/language-reference/keywords/string.md) do [int](../../../csharp/language-reference/keywords/int.md) .</span><span class="sxs-lookup"><span data-stu-id="535cf-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="535cf-119">Ten kod przechwytuje dwa najpopularniejsze wyjątki, które mogą zostać wyrzucone przez tę metodę <xref:System.FormatException> i <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="535cf-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="535cf-120">Jeśli liczbę można zwiększyć bez przepełnienia lokalizacji magazynu liczb całkowitych, program dodaje do wyniku 1 i drukuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="535cf-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="535cf-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="535cf-121">See Also</span></span>

- [<span data-ttu-id="535cf-122">Typy</span><span class="sxs-lookup"><span data-stu-id="535cf-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="535cf-123">Instrukcje: określanie, czy ciąg reprezentuje wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="535cf-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
- [<span data-ttu-id="535cf-124">Narzędzie formatowania programu .NET framework 4</span><span class="sxs-lookup"><span data-stu-id="535cf-124">.NET Framework 4 Formatting Utility</span></span>](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
