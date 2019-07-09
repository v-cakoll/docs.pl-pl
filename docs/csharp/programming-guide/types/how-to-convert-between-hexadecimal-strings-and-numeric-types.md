---
title: 'Instrukcje: Konwertowanie ciągów szesnastkowych, które typy liczbowe - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 2b896fb645113bc33b6a320948770947adc16dab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661143"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="c1a77-102">Instrukcje: Konwertowanie ciągów szesnastkowych, które typy liczbowe (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="c1a77-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="c1a77-103">Te przykłady pokazują, jak wykonywać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c1a77-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="c1a77-104">Uzyskaj wartość szesnastkowa każdego znaku w [ciąg](../../../csharp/language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="c1a77-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
- <span data-ttu-id="c1a77-105">Uzyskaj [char](../../../csharp/language-reference/keywords/char.md) odpowiadający każdej wartości w ciągu szesnastkowego.</span><span class="sxs-lookup"><span data-stu-id="c1a77-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="c1a77-106">Konwertuj szesnastkowego `string` do [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c1a77-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="c1a77-107">Konwertuj szesnastkowego `string` do [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c1a77-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="c1a77-108">Konwertuj [bajtów](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) tablicy na wartość szesnastkową `string`.</span><span class="sxs-lookup"><span data-stu-id="c1a77-108">Convert a [byte](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1a77-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1a77-109">Example</span></span>  
 <span data-ttu-id="c1a77-110">W tym przykładzie generuje wartość szesnastkowa każdego znaku w `string`.</span><span class="sxs-lookup"><span data-stu-id="c1a77-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="c1a77-111">Najpierw analizuje `string` do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="c1a77-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="c1a77-112">Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> przy każdym znaku, aby uzyskać jego wartości numerycznej.</span><span class="sxs-lookup"><span data-stu-id="c1a77-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="c1a77-113">Na koniec formatuje liczbę jako jej reprezentacji szesnastkowej w `string`.</span><span class="sxs-lookup"><span data-stu-id="c1a77-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="c1a77-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1a77-114">Example</span></span>  
 <span data-ttu-id="c1a77-115">W tym przykładzie analizuje `string` dla szesnastkowej wartości, a także generuje znak odpowiadający każdej wartości szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="c1a77-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="c1a77-116">Najpierw wywołuje [podziału (Char\[\])](xref:System.String.Split(System.Char[])) metodę, aby uzyskać każdej wartości szesnastkowych, jako użytkownik indywidualny `string` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c1a77-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="c1a77-117">Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> można przekonwertować wartości szesnastkowych na wartość dziesiętną reprezentowane jako [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). Pokazuje dwa różne sposoby uzyskiwania znak odpowiadający kod znaku.</span><span class="sxs-lookup"><span data-stu-id="c1a77-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="c1a77-118">Pierwszą techniką używa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadający argument liczby całkowitej jako `string`.</span><span class="sxs-lookup"><span data-stu-id="c1a77-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="c1a77-119">Druga metoda jawnie rzutuje `int` do [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="c1a77-119">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="c1a77-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1a77-120">Example</span></span>  
 <span data-ttu-id="c1a77-121">Konwertuj szesnastkowego w inny sposób w tym przykładzie `string` do liczby całkowitej, wywołując <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.</span><span class="sxs-lookup"><span data-stu-id="c1a77-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="c1a77-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1a77-122">Example</span></span>  
 <span data-ttu-id="c1a77-123">Poniższy przykład pokazuje, jak konwertować szesnastkowego `string` do [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md) przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy i <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c1a77-123">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="c1a77-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1a77-124">Example</span></span>  
 <span data-ttu-id="c1a77-125">Poniższy przykład pokazuje, jak konwertować [bajtów](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) tablicy na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="c1a77-125">The following example shows how to convert a [byte](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="c1a77-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1a77-126">See also</span></span>

- [<span data-ttu-id="c1a77-127">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="c1a77-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="c1a77-128">Typy</span><span class="sxs-lookup"><span data-stu-id="c1a77-128">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="c1a77-129">Instrukcje: Określanie, czy ciąg reprezentuje wartość numeryczną</span><span class="sxs-lookup"><span data-stu-id="c1a77-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
