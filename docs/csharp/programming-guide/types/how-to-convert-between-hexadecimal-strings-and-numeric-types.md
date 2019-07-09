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
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Instrukcje: Konwertowanie ciągów szesnastkowych, które typy liczbowe (C# Programming Guide)
Te przykłady pokazują, jak wykonywać następujące zadania:  
  
- Uzyskaj wartość szesnastkowa każdego znaku w [ciąg](../../../csharp/language-reference/keywords/string.md).  
  
- Uzyskaj [char](../../../csharp/language-reference/keywords/char.md) odpowiadający każdej wartości w ciągu szesnastkowego.  
  
- Konwertuj szesnastkowego `string` do [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).  
  
- Konwertuj szesnastkowego `string` do [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Konwertuj [bajtów](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) tablicy na wartość szesnastkową `string`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie generuje wartość szesnastkowa każdego znaku w `string`. Najpierw analizuje `string` do tablicy znaków. Następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> przy każdym znaku, aby uzyskać jego wartości numerycznej. Na koniec formatuje liczbę jako jej reprezentacji szesnastkowej w `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie analizuje `string` dla szesnastkowej wartości, a także generuje znak odpowiadający każdej wartości szesnastkowych. Najpierw wywołuje [podziału (Char\[\])](xref:System.String.Split(System.Char[])) metodę, aby uzyskać każdej wartości szesnastkowych, jako użytkownik indywidualny `string` w tablicy. Następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> można przekonwertować wartości szesnastkowych na wartość dziesiętną reprezentowane jako [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). Pokazuje dwa różne sposoby uzyskiwania znak odpowiadający kod znaku. Pierwszą techniką używa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadający argument liczby całkowitej jako `string`. Druga metoda jawnie rzutuje `int` do [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Przykład  
 Konwertuj szesnastkowego w inny sposób w tym przykładzie `string` do liczby całkowitej, wywołując <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak konwertować szesnastkowego `string` do [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md) przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy i <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak konwertować [bajtów](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) tablicy na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Zobacz także

- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](../../../csharp/programming-guide/types/index.md)
- [Instrukcje: Określanie, czy ciąg reprezentuje wartość numeryczną](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
