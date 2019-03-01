---
title: 'Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: bc3b26a09705ad4b28147ea4c09b8039107de8e8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976723"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur (C# Programming Guide)
Ten przykład definiuje dwie struktury `RomanNumeral` i `BinaryNumeral`i przedstawiono konwersje między nimi.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
-   W poprzednim przykładzie instrukcji:  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     wykonuje konwersję z `RomanNumeral` do `BinaryNumeral`. Ponieważ nie istnieje żadne bezpośrednie konwersja `RomanNumeral` do `BinaryNumeral`, używane jest rzutowanie do konwersji z `RomanNumeral` do `int`i innym rzutowanie do konwersji z `int` do `BinaryNumeral`.  
  
-   Również — instrukcja  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     wykonuje konwersję z `BinaryNumeral` do `RomanNumeral`. Ponieważ `RomanNumeral` definiuje niejawna konwersja z `BinaryNumeral`, rzutowanie nie jest wymagana.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
