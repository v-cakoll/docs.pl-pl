---
title: Jak ustalić, czy ciąg reprezentuje wartość liczbową - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 15a21a6298f8f0a57e0189554246202b220dd259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157068"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Jak ustalić, czy ciąg reprezentuje wartość liczbową (Przewodnik programowania C#)
Aby ustalić, czy ciąg jest prawidłową reprezentacją określonego typu `TryParse` liczbowego, należy użyć metody statycznej implementacyjnej przez <xref:System.DateTime> <xref:System.Net.IPAddress>wszystkie pierwotne typy liczbowe, a także według typów, takich jak i . W poniższym przykładzie pokazano, jak ustalić, czy "108" jest prawidłowym [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Jeśli ciąg zawiera znaki nieliczbowe lub wartość liczbowa jest zbyt duża lub `TryParse` zbyt mała dla określonego typu, zwraca wartość false i ustawia parametr out na zero. W przeciwnym razie zwraca true i ustawia out parametr u wartości liczbowej ciągu.  
  
> [!NOTE]
> Ciąg może zawierać tylko znaki liczbowe i nadal `TryParse` nie jest prawidłowy dla typu, którego metody używasz. Na przykład "256" nie jest `byte` prawidłową wartością, ale jest prawidłowa dla `int`. "98.6" nie jest prawidłową `int` wartością, `decimal`ale jest prawidłową wartością.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach `TryParse` przedstawiono sposób używania `long` `byte`z `decimal` reprezentacjami ciągów i wartościami.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Pierwotne typy liczbowe implementują również metodę `Parse` statyczną, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą. `TryParse`jest ogólnie bardziej wydajne, ponieważ po prostu zwraca false, jeśli liczba jest nieprawidłowa.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze `TryParse` używaj `Parse` metod lub do sprawdzania poprawności danych wejściowych użytkownika z formantów, takich jak pola tekstowe i pola kombi.  
  
## <a name="see-also"></a>Zobacz też

- [Konwertowanie tablicy typu Byte na liczbę całkowitą](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Konwertowanie ciągu na liczbę](../types/how-to-convert-a-string-to-a-number.md)
- [Konwertowanie ciągów szesnastkowych na typy liczbowe](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analizowanie ciągów numerycznych](../../../standard/base-types/parsing-numeric.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
