---
title: 'Porady: konwertowanie ciągów szestnastkowych na typy liczbowe (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 1a5bde0a9169a78e179a69c7a2f4080e5a465f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334704"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="e2a08-102">Porady: konwertowanie ciągów szestnastkowych na typy liczbowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e2a08-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="e2a08-103">Poniższe przykłady pokazują, jak wykonywać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e2a08-103">These examples show you how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="e2a08-104">Uzyskaj wartość szesnastkową każdego znaku w [ciąg](../../../csharp/language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="e2a08-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
-   <span data-ttu-id="e2a08-105">Uzyskaj [char](../../../csharp/language-reference/keywords/char.md) odpowiadający każdej wartości w ciągu szesnastkowego.</span><span class="sxs-lookup"><span data-stu-id="e2a08-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
-   <span data-ttu-id="e2a08-106">Konwertuj szesnastkowego `string` do [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="e2a08-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
-   <span data-ttu-id="e2a08-107">Konwertuj szesnastkowego `string` do [float](../../../csharp/language-reference/keywords/float.md).</span><span class="sxs-lookup"><span data-stu-id="e2a08-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md).</span></span>  
  
-   <span data-ttu-id="e2a08-108">Konwertuj [bajtów](../../../csharp/language-reference/keywords/byte.md) tablicy w postaci szesnastkowej `string`.</span><span class="sxs-lookup"><span data-stu-id="e2a08-108">Convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2a08-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2a08-109">Example</span></span>  
 <span data-ttu-id="e2a08-110">Wartość szesnastkowa każdego znaku w danych wyjściowych w tym przykładzie `string`.</span><span class="sxs-lookup"><span data-stu-id="e2a08-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="e2a08-111">Najpierw analizuje `string` do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="e2a08-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="e2a08-112">A następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> na każdego znaku w celu uzyskania jej wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="e2a08-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="e2a08-113">Na koniec formatuje liczbę jako jego szesnastkową reprezentację w `string`.</span><span class="sxs-lookup"><span data-stu-id="e2a08-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e2a08-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2a08-114">Example</span></span>  
 <span data-ttu-id="e2a08-115">W tym przykładzie analizuje `string` z szesnastkowej wartości i wyświetla znak odpowiadający każdej wartości szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="e2a08-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="e2a08-116">Najpierw wywołuje [podziału (Char\[\])](xref:System.String.Split(System.Char[])) metody można uzyskać wartości szesnastkowe jako osoba `string` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e2a08-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="e2a08-117">A następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> Aby przekonwertować wartość szesnastkowa reprezentowane jako wartości dziesiętnej [int](../../../csharp/language-reference/keywords/int.md). Przedstawia on dwa różne sposoby uzyskania znak odpowiadający kod znaku.</span><span class="sxs-lookup"><span data-stu-id="e2a08-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/keywords/int.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="e2a08-118">Używa pierwszego technika <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadającego atrybutowi argument liczby całkowitej jako `string`.</span><span class="sxs-lookup"><span data-stu-id="e2a08-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="e2a08-119">Druga metoda jawnie rzutuje `int` do [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="e2a08-119">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="e2a08-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2a08-120">Example</span></span>  
 <span data-ttu-id="e2a08-121">W tym przykładzie przedstawiono inny sposób, aby przekonwertować szesnastkowego `string` na liczbę całkowitą, wywołując <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.</span><span class="sxs-lookup"><span data-stu-id="e2a08-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="e2a08-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2a08-122">Example</span></span>  
 <span data-ttu-id="e2a08-123">Poniższy przykład przedstawia sposób konwertowania szesnastkowego `string` do [float](../../../csharp/language-reference/keywords/float.md) za pomocą <xref:System.BitConverter?displayProperty=nameWithType> klasy i <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e2a08-123">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.Int32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="e2a08-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2a08-124">Example</span></span>  
 <span data-ttu-id="e2a08-125">Poniższy przykład przedstawia sposób konwertowania [bajtów](../../../csharp/language-reference/keywords/byte.md) tablicy na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="e2a08-125">The following example shows how to convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e2a08-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2a08-126">See Also</span></span>  
 [<span data-ttu-id="e2a08-127">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="e2a08-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="e2a08-128">Typy</span><span class="sxs-lookup"><span data-stu-id="e2a08-128">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="e2a08-129">Instrukcje: określanie, czy ciąg reprezentuje wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="e2a08-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
