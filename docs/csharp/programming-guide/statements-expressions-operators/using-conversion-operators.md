---
title: Używanie operatorów konwersji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: d6b271c0d716a9b5dfb49b825d843d4345471147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578575"
---
# <a name="using-conversion-operators-c-programming-guide"></a>Używanie operatorów konwersji (Przewodnik programowania w języku C#)
Możesz użyć `implicit` operatorów konwersji, które są łatwiejsze w obsłudze, lub `explicit` operatorów konwersji, które wyraźnie wskazać dla każdego, kto kodu czy podczas konwertowania typu. W tym temacie przedstawiono oba rodzaje operatora konwersji.  
  
> [!NOTE]
>  Aby uzyskać informacji dotyczących konwersji typu prostego, zobacz [jak: Konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [jak: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: Konwertowanie ciągów szesnastkowych, które typy liczbowe](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), lub <xref:System.Convert>.  
  
## <a name="example"></a>Przykład  
 Jest to przykład operator jawnej konwersji. Ten operator konwertuje typ <xref:System.Byte> do typu wartości o nazwie `Digit`. Ponieważ nie wszystkie wartości bajtowe mogą być konwertowane na cyfrę, konwersja jest jawne oznacza, że należy użyć rzutowania, jak pokazano na `Main` metody.  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono operator niejawnej konwersji przez definiowanie operatora konwersji, która cofa w poprzednim przykładzie została: konwertuje wartość klasę o nazwie `Digit` do całkowitych <xref:System.Byte> typu. Ponieważ dowolną cyfrę mogą być konwertowane na <xref:System.Byte>, nie ma potrzeby zmusić użytkowników, aby była niejawna konwersja informacje.  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
- [is](../../../csharp/language-reference/keywords/is.md)
