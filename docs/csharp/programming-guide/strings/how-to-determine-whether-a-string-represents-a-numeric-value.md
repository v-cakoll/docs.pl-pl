---
title: Jak określić, czy ciąg reprezentuje znak wartości liczbowej — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: bd89024a0a9bd62927d2d5e0eda248b57bb7d21d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711925"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Jak ustalić, czy ciąg reprezentuje wartość liczbową (C# Przewodnik programowania)
Aby określić, czy ciąg jest prawidłową reprezentacją określonego typu liczbowego, należy użyć statycznej metody `TryParse`, która jest implementowana przez wszystkie pierwotne typy liczbowe, a także typy takie jak <xref:System.DateTime> i <xref:System.Net.IPAddress>. Poniższy przykład pokazuje, jak ustalić, czy "108" jest prawidłową [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Jeśli ciąg zawiera znaki nienumeryczne lub wartość liczbowa jest za duża lub za mała dla określonego typu, `TryParse` zwraca wartość false i ustawia parametr out na wartość zero. W przeciwnym razie zwraca wartość true i ustawia parametr out na wartość liczbową ciągu.  
  
> [!NOTE]
> Ciąg może zawierać tylko znaki numeryczne i nadal nie jest prawidłowy dla typu, którego Metoda `TryParse` jest używana. Na przykład "256" nie jest prawidłową wartością dla `byte`, ale jest prawidłowy dla `int`. "98,6" nie jest prawidłową wartością dla `int`, ale jest prawidłowym `decimal`.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać `TryParse` z reprezentacją ciągu `long`, `byte`i `decimal` wartości.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Pierwotne typy liczbowe implementują również `Parse` metodę statyczną, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą. `TryParse` jest zwykle bardziej wydajny, ponieważ zwraca wartość false, jeśli liczba jest nieprawidłowa.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Zawsze używaj metod `TryParse` lub `Parse` do sprawdzania poprawności danych wejściowych użytkownika z kontrolek, takich jak pola tekstowe i pola kombi.  
  
## <a name="see-also"></a>Zobacz także

- [Jak skonwertować tablicę bajtową na liczbę całkowitą](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Jak przekonwertować ciąg na liczbę](../types/how-to-convert-a-string-to-a-number.md)
- [Jak przekonwertować ciągi szesnastkowe i typy liczbowe](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analizowanie ciągów liczbowych](../../../standard/base-types/parsing-numeric.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
