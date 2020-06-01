---
title: Jak określić, czy ciąg reprezentuje wartość liczbową — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 37437460ea4c6ca216f2844d63af3688ccc984c6
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241724"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Jak określić, czy ciąg reprezentuje wartość liczbową (Przewodnik programowania w języku C#)
Aby określić, czy ciąg jest prawidłową reprezentacją określonego typu liczbowego, należy użyć statycznej `TryParse` metody, która jest implementowana przez wszystkie pierwotne typy liczbowe, a także typy takie jak <xref:System.DateTime> i <xref:System.Net.IPAddress> . Poniższy przykład pokazuje, jak ustalić, czy "108" jest prawidłową [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Jeśli ciąg zawiera znaki nienumeryczne lub wartość liczbowa jest za duża lub za mała dla określonego typu, `TryParse` zwraca wartość false i ustawia parametr out na wartość zero. W przeciwnym razie zwraca wartość true i ustawia parametr out na wartość liczbową ciągu.  
  
> [!NOTE]
> Ciąg może zawierać tylko znaki numeryczne i nadal nie jest prawidłowy dla typu, którego `TryParse` Metoda jest używana. Na przykład "256" nie jest prawidłową wartością dla `byte` , ale jest prawidłowy dla `int` . "98,6" nie jest prawidłową wartością dla `int` , ale jest prawidłowy `decimal` .  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać `TryParse` z reprezentacjami ciągów `long` `byte` wartości,, i `decimal` .  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Pierwotne typy liczbowe implementują również `Parse` metodę statyczną, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą. `TryParse`jest zwykle bardziej wydajne, ponieważ zwraca wartość false, jeśli liczba jest nieprawidłowa.  
  
## <a name="net-security"></a>Zabezpieczenia platformy .NET  
 Zawsze używaj `TryParse` metod lub `Parse` do sprawdzania poprawności danych wejściowych użytkownika z kontrolek, takich jak pola tekstowe i pola kombi.  
  
## <a name="see-also"></a>Zobacz też

- [Konwertowanie tablicy typu Byte na liczbę całkowitą](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Konwertowanie ciągu na liczbę](../types/how-to-convert-a-string-to-a-number.md)
- [Konwertowanie ciągów szesnastkowych na typy liczbowe](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analizowanie ciągów liczbowych](../../../standard/base-types/parsing-numeric.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
