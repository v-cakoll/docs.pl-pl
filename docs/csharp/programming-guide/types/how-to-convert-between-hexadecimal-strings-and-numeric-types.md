---
title: 'Instrukcje: konwertowanie między ciągami szesnastkowymi i typami liczbowymi — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: e5013891db827e27b3cda55135fff4ee287cfcb4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423136"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="65c90-102">Porady: konwertowanie ciągów szestnastkowych na typy liczbowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="65c90-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="65c90-103">W poniższych przykładach pokazano, jak wykonywać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="65c90-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="65c90-104">Uzyskaj wartość szesnastkową każdego znaku w [ciągu](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="65c90-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="65c90-105">Uzyskaj [znak](../../language-reference/keywords/char.md) , który odpowiada każdej wartości w ciągu szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="65c90-105">Obtain the [char](../../language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="65c90-106">Konwertuj `string` szesnastkową na wartość typu [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="65c90-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="65c90-107">Konwertuj `string` szesnastkową na wartość [zmiennoprzecinkową](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="65c90-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="65c90-108">Konwertuj tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na `string`szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="65c90-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65c90-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="65c90-109">Example</span></span>  
 <span data-ttu-id="65c90-110">Ten przykład wyprowadza wartość szesnastkową każdego znaku w `string`.</span><span class="sxs-lookup"><span data-stu-id="65c90-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="65c90-111">Najpierw analizuje `string` do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="65c90-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="65c90-112">Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> każdego znaku, aby uzyskać jego wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="65c90-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="65c90-113">Na koniec formatuje liczbę jako reprezentację szesnastkową w `string`.</span><span class="sxs-lookup"><span data-stu-id="65c90-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="65c90-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="65c90-114">Example</span></span>  
 <span data-ttu-id="65c90-115">Ten przykład analizuje `string` wartości szesnastkowych i wyprowadza znak odpowiadający każdej wartości szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="65c90-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="65c90-116">Najpierw wywołuje metodę [Split (Char\[\])](xref:System.String.Split(System.Char[])) , aby uzyskać każdą wartość szesnastkową jako pojedyncze `string` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="65c90-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="65c90-117">Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29>, aby przekonwertować wartość szesnastkową na wartość dziesiętną reprezentowaną jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Przedstawiono dwa różne sposoby uzyskania znaku odpowiadającego kodowi tego znaku.</span><span class="sxs-lookup"><span data-stu-id="65c90-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="65c90-118">W pierwszej metodzie jest używany <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadający argumentowi Integer jako `string`.</span><span class="sxs-lookup"><span data-stu-id="65c90-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="65c90-119">Druga technika jawnie rzutuje `int` na [znak](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="65c90-119">The second technique explicitly casts the `int` to a [char](../../language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="65c90-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="65c90-120">Example</span></span>  
 <span data-ttu-id="65c90-121">W tym przykładzie pokazano inny sposób konwersji `string` szesnastkowej na liczbę całkowitą, wywołując metodę <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.</span><span class="sxs-lookup"><span data-stu-id="65c90-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="65c90-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="65c90-122">Example</span></span>  
 <span data-ttu-id="65c90-123">Poniższy przykład ilustruje sposób konwersji `string` szesnastkowego na wartość [zmiennoprzecinkową](../../language-reference/builtin-types/floating-point-numeric-types.md) przy użyciu klasy <xref:System.BitConverter?displayProperty=nameWithType> i metody <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65c90-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="65c90-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="65c90-124">Example</span></span>  
 <span data-ttu-id="65c90-125">Poniższy przykład pokazuje, jak skonwertować tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na ciąg szesnastkowy przy użyciu klasy <xref:System.BitConverter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65c90-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="65c90-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65c90-126">See also</span></span>

- [<span data-ttu-id="65c90-127">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="65c90-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="65c90-128">Typy</span><span class="sxs-lookup"><span data-stu-id="65c90-128">Types</span></span>](./index.md)
- [<span data-ttu-id="65c90-129">Instrukcje: określanie, czy ciąg reprezentuje wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="65c90-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
