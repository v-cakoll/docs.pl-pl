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
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Instrukcje: Konwertuj między ciągi szesnastkowe i typy liczboweC# (Przewodnik programowania)
W poniższych przykładach pokazano, jak wykonywać następujące zadania:  
  
- Uzyskaj wartość szesnastkową każdego znaku w [ciągu](../../language-reference/keywords/string.md).  
  
- Uzyskaj [znak](../../language-reference/keywords/char.md) , który odpowiada każdej wartości w ciągu szesnastkowym.  
  
- Konwertuj wartość szesnastkową na [](../../language-reference/builtin-types/integral-numeric-types.md)liczbę `string` całkowitą.  
  
- Konwertuj wartość szesnastkową `string` na wartość [zmiennoprzecinkową](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Konwertuj tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na wartość szesnastkową `string`.  
  
## <a name="example"></a>Przykład  
 Ten przykład wyprowadza wartość szesnastkową każdego znaku w `string`. Najpierw analizuje `string` on tablicę znaków. Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> każdy znak, aby uzyskać jego wartość liczbową. Na koniec formatuje liczbę jako reprezentację szesnastkową w `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Przykład  
 Ten przykład analizuje `string` wartości szesnastkowe i wyprowadza znak odpowiadający każdej wartości szesnastkowej. Najpierw wywołuje metodę [Split (Char\[\])](xref:System.String.Split(System.Char[])) , aby uzyskać każdą wartość szesnastkową jako pojedynczą `string` w tablicy. Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> , aby przekonwertować wartość szesnastkową na wartość dziesiętną reprezentowaną jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Przedstawiono dwa różne sposoby uzyskania znaku odpowiadającego kodowi tego znaku. Pierwsza technika używa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadający argumentowi Integer `string`jako. Druga technika jawnie rzutuje `int` na [znak](../../language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje inny sposób konwersji szesnastkowej `string` na liczbę całkowitą, <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> wywołując metodę.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje `string` <xref:System.BitConverter?displayProperty=nameWithType> [](../../language-reference/builtin-types/floating-point-numeric-types.md) ,jakkonwertowaćszesnastkowenazmiennoprzecinkoweprzyużyciuklasyi<xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonwertować tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Zobacz także

- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
