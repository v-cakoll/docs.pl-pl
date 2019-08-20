---
title: 'Instrukcje: Konwertowanie między ciągami szesnastkowymi i typami C# liczbowymi — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a7109945192fe1577cd1b96c8b4d6c05270d54e8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588370"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="a682f-102">Instrukcje: Konwertuj między ciągi szesnastkowe i typy liczboweC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="a682f-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="a682f-103">W poniższych przykładach pokazano, jak wykonywać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a682f-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="a682f-104">Uzyskaj wartość szesnastkową każdego znaku w [ciągu](../../language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="a682f-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/keywords/string.md).</span></span>  
  
- <span data-ttu-id="a682f-105">Uzyskaj [znak](../../language-reference/keywords/char.md) , który odpowiada każdej wartości w ciągu szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="a682f-105">Obtain the [char](../../language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="a682f-106">Konwertuj wartość szesnastkową na [](../../language-reference/builtin-types/integral-numeric-types.md)liczbę `string` całkowitą.</span><span class="sxs-lookup"><span data-stu-id="a682f-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="a682f-107">Konwertuj wartość szesnastkową `string` na wartość [zmiennoprzecinkową](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="a682f-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="a682f-108">Konwertuj tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na wartość szesnastkową `string`.</span><span class="sxs-lookup"><span data-stu-id="a682f-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a682f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a682f-109">Example</span></span>  
 <span data-ttu-id="a682f-110">Ten przykład wyprowadza wartość szesnastkową każdego znaku w `string`.</span><span class="sxs-lookup"><span data-stu-id="a682f-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="a682f-111">Najpierw analizuje `string` on tablicę znaków.</span><span class="sxs-lookup"><span data-stu-id="a682f-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="a682f-112">Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> każdy znak, aby uzyskać jego wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="a682f-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="a682f-113">Na koniec formatuje liczbę jako reprezentację szesnastkową w `string`.</span><span class="sxs-lookup"><span data-stu-id="a682f-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="a682f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a682f-114">Example</span></span>  
 <span data-ttu-id="a682f-115">Ten przykład analizuje `string` wartości szesnastkowe i wyprowadza znak odpowiadający każdej wartości szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="a682f-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="a682f-116">Najpierw wywołuje metodę [Split (Char\[\])](xref:System.String.Split(System.Char[])) , aby uzyskać każdą wartość szesnastkową jako pojedynczą `string` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a682f-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="a682f-117">Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> , aby przekonwertować wartość szesnastkową na wartość dziesiętną reprezentowaną jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Przedstawiono dwa różne sposoby uzyskania znaku odpowiadającego kodowi tego znaku.</span><span class="sxs-lookup"><span data-stu-id="a682f-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="a682f-118">Pierwsza technika używa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadający argumentowi Integer `string`jako.</span><span class="sxs-lookup"><span data-stu-id="a682f-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="a682f-119">Druga technika jawnie rzutuje `int` na [znak](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="a682f-119">The second technique explicitly casts the `int` to a [char](../../language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="a682f-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="a682f-120">Example</span></span>  
 <span data-ttu-id="a682f-121">Ten przykład pokazuje inny sposób konwersji szesnastkowej `string` na liczbę całkowitą, <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="a682f-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="a682f-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="a682f-122">Example</span></span>  
 <span data-ttu-id="a682f-123">Poniższy przykład pokazuje `string` <xref:System.BitConverter?displayProperty=nameWithType> [](../../language-reference/builtin-types/floating-point-numeric-types.md) ,jakkonwertowaćszesnastkowenazmiennoprzecinkoweprzyużyciuklasyi<xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a682f-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="a682f-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="a682f-124">Example</span></span>  
 <span data-ttu-id="a682f-125">Poniższy przykład pokazuje, jak skonwertować tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="a682f-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="a682f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a682f-126">See also</span></span>

- [<span data-ttu-id="a682f-127">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="a682f-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="a682f-128">Typy</span><span class="sxs-lookup"><span data-stu-id="a682f-128">Types</span></span>](./index.md)
- [<span data-ttu-id="a682f-129">Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="a682f-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
