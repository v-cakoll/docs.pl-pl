---
title: Używanie operatorów konwersji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: e03fb12200bc15de9c1686edd40921201598621f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-conversion-operators-c-programming-guide"></a>Używanie operatorów konwersji (Przewodnik programowania w języku C#)
Można użyć `implicit` operatory konwersji, które są łatwiejsze do użycia, lub `explicit` operatory konwersji, wskazujące wyraźnie innym osobom odczytywanie kod czy podczas konwertowania typu. W tym temacie przedstawiono oba rodzaje operatora konwersji.  
  
> [!NOTE]
>  Aby uzyskać informacje o konwersji typu prostego, zobacz [jak: konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [porady: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: konwertowanie między ciągów szesnastkowych i numeryczne Typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), lub <xref:System.Convert>.  
  
## <a name="example"></a>Przykład  
 To jest przykład operator jawnej konwersji. Ten operator konwertuje z typu <xref:System.Byte> wartość typu o nazwie `Digit`. Ponieważ nie wszystkie bajty można przekonwertować na cyfrę, konwersja jest jawne, co oznacza że musi być używane rzutowanie, jak pokazano w `Main` metody.  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Przykład  
 W przykładzie pokazano operator niejawnej konwersji przez definiowanie operatora konwersji, która cofa w poprzednim przykładzie został: konwertuje z klasy wartości o nazwie `Digit` na typy całkowite <xref:System.Byte> typu. Ponieważ dowolną cyfrę może zostać przekonwertowany na <xref:System.Byte>, nie istnieje potrzeba aby wymusić użytkowników jako jawne o konwersji.  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [is](../../../csharp/language-reference/keywords/is.md)
