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
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Jak konwertować między ciągami szesnastkowymi a typami liczbowymi (Przewodnik programowania C#)
W poniższych przykładach przedstawiono sposób wykonywania następujących zadań:  
  
- Uzyskaj wartość szesnastkowa każdego znaku w [ciągu](../../language-reference/builtin-types/reference-types.md).  
  
- Uzyskać [znak,](../../language-reference/builtin-types/char.md) który odpowiada każdej wartości w ciągu szesnastkowym.  
  
- Konwertowanie szesnastkowego `string` [na int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Konwertowanie szesnastkowego `string` na [pływak](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Konwertowanie tablicy [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na szesnastkową `string`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyprowadza wartość szesnastkową `string`każdego znaku w pliku . Najpierw analizuje `string` do tablicy znaków. Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> każdy znak, aby uzyskać jego wartość liczbową. Na koniec formatuje liczbę jako jego reprezentację szesnastkową w pliku `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `string` analizuje wartości szesnastkowych i wyprowadza znak odpowiadający każdej wartości szesnastkowej. Najpierw wywołuje [Split(Char)\[\]](xref:System.String.Split(System.Char[])) metoda, aby uzyskać każdą wartość szesnastkowa jako osoba `string` w tablicy. Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> przekonwertować wartość szesnastkową na wartość dziesiętną przedstawioną jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Pokazuje dwa różne sposoby uzyskania znaku odpowiadającego tego kodu znaku. Pierwsza technika <xref:System.Char.ConvertFromUtf32%28System.Int32%29>używa , który zwraca znak odpowiadający `string`argumentowi liczby całkowitej jako . Druga technika jawnie `int` rzuca do [znaku](../../language-reference/builtin-types/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono inny sposób konwertowania `string` szesnastkowego <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> na liczbę całkowitą, wywołując metodę.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Przykład  
 W `string` poniższym przykładzie pokazano, jak przekonwertować szesnastkową do [float](../../language-reference/builtin-types/floating-point-numeric-types.md) przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy i <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak przekonwertować tablicę [bajtów](../../language-reference/builtin-types/integral-numeric-types.md) na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Zobacz też

- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Określanie, czy ciąg reprezentuje wartość numeryczną](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
