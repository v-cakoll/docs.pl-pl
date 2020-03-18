---
title: Jak konwertować między ciągami szesnastkowymi a typami liczbowymi - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 0e1f6ad2606b367d369c1c644c947831b2aa8289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698524"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="47def-102">Jak konwertować między ciągami szesnastkowymi a typami liczbowymi (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="47def-102">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>
<span data-ttu-id="47def-103">W poniższych przykładach przedstawiono sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="47def-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="47def-104">Uzyskaj wartość szesnastkowa każdego znaku w [ciągu](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="47def-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="47def-105">Uzyskać [znak,](../../language-reference/builtin-types/char.md) który odpowiada każdej wartości w ciągu szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="47def-105">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="47def-106">Konwertowanie szesnastkowego `string` [na int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="47def-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="47def-107">Konwertowanie szesnastkowego `string` na [pływak](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="47def-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="47def-108">Konwertowanie tablicy [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na szesnastkową `string`.</span><span class="sxs-lookup"><span data-stu-id="47def-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47def-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="47def-109">Example</span></span>  
 <span data-ttu-id="47def-110">W tym przykładzie wyprowadza wartość szesnastkową `string`każdego znaku w pliku .</span><span class="sxs-lookup"><span data-stu-id="47def-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="47def-111">Najpierw analizuje `string` do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="47def-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="47def-112">Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> każdy znak, aby uzyskać jego wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="47def-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="47def-113">Na koniec formatuje liczbę jako jego reprezentację szesnastkową w pliku `string`.</span><span class="sxs-lookup"><span data-stu-id="47def-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="47def-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="47def-114">Example</span></span>  
 <span data-ttu-id="47def-115">W tym przykładzie `string` analizuje wartości szesnastkowych i wyprowadza znak odpowiadający każdej wartości szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="47def-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="47def-116">Najpierw wywołuje [Split(Char)\[\]](xref:System.String.Split(System.Char[])) metoda, aby uzyskać każdą wartość szesnastkowa jako osoba `string` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="47def-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="47def-117">Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> przekonwertować wartość szesnastkową na wartość dziesiętną przedstawioną jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Pokazuje dwa różne sposoby uzyskania znaku odpowiadającego tego kodu znaku.</span><span class="sxs-lookup"><span data-stu-id="47def-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="47def-118">Pierwsza technika <xref:System.Char.ConvertFromUtf32%28System.Int32%29>używa , który zwraca znak odpowiadający `string`argumentowi liczby całkowitej jako .</span><span class="sxs-lookup"><span data-stu-id="47def-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="47def-119">Druga technika jawnie `int` rzuca do [znaku](../../language-reference/builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="47def-119">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="47def-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="47def-120">Example</span></span>  
 <span data-ttu-id="47def-121">W tym przykładzie przedstawiono inny sposób konwertowania `string` szesnastkowego <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> na liczbę całkowitą, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="47def-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="47def-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="47def-122">Example</span></span>  
 <span data-ttu-id="47def-123">W `string` poniższym przykładzie pokazano, jak przekonwertować szesnastkową do [float](../../language-reference/builtin-types/floating-point-numeric-types.md) przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy i <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="47def-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="47def-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="47def-124">Example</span></span>  
 <span data-ttu-id="47def-125">W poniższym przykładzie pokazano, jak przekonwertować tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="47def-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="47def-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47def-126">See also</span></span>

- [<span data-ttu-id="47def-127">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="47def-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="47def-128">Typy</span><span class="sxs-lookup"><span data-stu-id="47def-128">Types</span></span>](./index.md)
- [<span data-ttu-id="47def-129">Określanie, czy ciąg reprezentuje wartość numeryczną</span><span class="sxs-lookup"><span data-stu-id="47def-129">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
