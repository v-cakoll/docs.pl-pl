---
title: 'Porady: implementowanie zdefiniowanych przez użytkownika konwersji struktur (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 178d9e2f92c5c1989253a16d866052a1fc42c10e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339933"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Porady: implementowanie zdefiniowanych przez użytkownika konwersji struktur (Przewodnik programowania w języku C#)
W tym przykładzie definiuje dwie struktury `RomanNumeral` i `BinaryNumeral`i pokazuje konwersji między nimi.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
-   W poprzednim przykładzie instrukcji:  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     wykonuje konwersję z `RomanNumeral` do `BinaryNumeral`. Ponieważ nie jest bezpośrednio konwersja z `RomanNumeral` do `BinaryNumeral`, rzutowanie służy do konwertowania z `RomanNumeral` do `int`i innym rzutowanie do przekonwertowania z `int` do `BinaryNumeral`.  
  
-   Również — instrukcja  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     wykonuje konwersję z `BinaryNumeral` do `RomanNumeral`. Ponieważ `RomanNumeral` definiuje niejawna konwersja z `BinaryNumeral`, rzutowanie nie jest wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
