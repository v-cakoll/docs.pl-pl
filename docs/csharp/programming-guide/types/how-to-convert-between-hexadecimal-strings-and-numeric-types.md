---
title: "Porady: konwertowanie ciągów szestnastkowych na typy liczbowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91e5cff52c67e1e7930d92da7c87ab1f4a3120af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Porady: konwertowanie ciągów szestnastkowych na typy liczbowe (Przewodnik programowania w języku C#)
Poniższe przykłady pokazują, jak wykonywać następujące zadania:  
  
-   Uzyskaj wartość szesnastkową każdego znaku w [ciąg](../../../csharp/language-reference/keywords/string.md).  
  
-   Uzyskaj [char](../../../csharp/language-reference/keywords/char.md) odpowiadający każdej wartości w ciągu szesnastkowego.  
  
-   Konwertuj szesnastkowego `string` do [int](../../../csharp/language-reference/keywords/int.md).  
  
-   Konwertuj szesnastkowego `string` do [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Konwertuj [bajtów](../../../csharp/language-reference/keywords/byte.md) tablicy w postaci szesnastkowej `string`.  
  
## <a name="example"></a>Przykład  
 Wartość szesnastkowa każdego znaku w danych wyjściowych w tym przykładzie `string`. Najpierw analizuje `string` do tablicy znaków. A następnie wywołuje <xref:System.Convert.ToInt32%28System.Char%29> na każdego znaku w celu uzyskania jej wartość liczbową. Na koniec formatuje liczbę jako jego szesnastkową reprezentację w `string`.  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie analizuje `string` z szesnastkowej wartości i wyświetla znak odpowiadający każdej wartości szesnastkowe. Najpierw wywołuje [podziału (Char\[\])](xref:System.String.Split(System.Char[])) metody można uzyskać wartości szesnastkowe jako osoba `string` w tablicy. A następnie wywołuje <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> Aby przekonwertować wartość szesnastkowa reprezentowane jako wartości dziesiętnej [int](../../../csharp/language-reference/keywords/int.md). Przedstawia on dwa różne sposoby uzyskania znak odpowiadający kod znaku. Używa pierwszego technika <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, która zwraca znak odpowiadającego atrybutowi argument liczby całkowitej jako `string`. Druga metoda jawnie rzutuje `int` do [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono inny sposób, aby przekonwertować szesnastkowego `string` na liczbę całkowitą, wywołując <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konwertowania szesnastkowego `string` do [float](../../../csharp/language-reference/keywords/float.md) za pomocą <xref:System.BitConverter?displayProperty=nameWithType> klasy i <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metody.  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konwertowania [bajtów](../../../csharp/language-reference/keywords/byte.md) tablicy na ciąg szesnastkowy przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Porady: Określanie, czy ciąg reprezentuje wartość numeryczną](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
