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
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Porady: konwertowanie ciągów szestnastkowych na typy liczbowe (Przewodnik programowania w języku C#)
W poniższych przykładach pokazano, jak wykonywać następujące zadania:  
  
- Uzyskaj wartość szesnastkową każdego znaku w [ciągu](../../language-reference/builtin-types/reference-types.md).  
  
- Uzyskaj [znak](../../language-reference/keywords/char.md) , który odpowiada każdej wartości w ciągu szesnastkowym.  
  
- Konwertuj `string` szesnastkową na wartość typu [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Konwertuj `string` szesnastkową na wartość [zmiennoprzecinkową](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Konwertuj tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na `string`szesnastkową.  
  
## <a name="example"></a>Przykład  
 Ten przykład wyprowadza wartość szesnastkową każdego znaku w `string`. Najpierw analizuje `string` do tablicy znaków. Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> każdego znaku, aby uzyskać jego wartość liczbową. Na koniec formatuje liczbę jako reprezentację szesnastkową w `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Przykład  
 Ten przykład analizuje `string` wartości szesnastkowych i wyprowadza znak odpowiadający każdej wartości szesnastkowej. Najpierw wywołuje metodę [Split (Char\[\])](xref:System.String.Split(System.Char[])) , aby uzyskać każdą wartość szesnastkową jako pojedyncze `string` w tablicy. Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29>, aby przekonwertować wartość szesnastkową na wartość dziesiętną reprezentowaną jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Przedstawiono dwa różne sposoby uzyskania znaku odpowiadającego kodowi tego znaku. W pierwszej metodzie jest używany <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadający argumentowi Integer jako `string`. Druga technika jawnie rzutuje `int` na [znak](../../language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano inny sposób konwersji `string` szesnastkowej na liczbę całkowitą, wywołując metodę <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób konwersji `string` szesnastkowego na wartość [zmiennoprzecinkową](../../language-reference/builtin-types/floating-point-numeric-types.md) przy użyciu klasy <xref:System.BitConverter?displayProperty=nameWithType> i metody <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonwertować tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na ciąg szesnastkowy przy użyciu klasy <xref:System.BitConverter?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Zobacz także

- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Instrukcje: określanie, czy ciąg reprezentuje wartość liczbową](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
