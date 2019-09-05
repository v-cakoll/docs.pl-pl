---
title: 'Instrukcje: Określanie, czy ciąg reprezentuje znak wartości liczbowej C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 8fc5051893882a6dbdbb4c9097949794d4430a93
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252954"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową (C# Przewodnik programowania)
Aby określić, czy ciąg jest prawidłową reprezentacją określonego typu liczbowego, należy użyć statycznej `TryParse` metody, która jest implementowana przez wszystkie pierwotne typy liczbowe, a także typy takie jak <xref:System.DateTime> i <xref:System.Net.IPAddress>. Poniższy przykład pokazuje, jak ustalić, czy "108" jest prawidłową [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Jeśli ciąg zawiera znaki nienumeryczne lub wartość liczbowa jest za duża lub za mała dla określonego typu, `TryParse` zwraca wartość false i ustawia parametr out na wartość zero. W przeciwnym razie zwraca wartość true i ustawia parametr out na wartość liczbową ciągu.  
  
> [!NOTE]
> Ciąg może zawierać tylko znaki numeryczne i nadal nie jest prawidłowy dla typu, którego `TryParse` Metoda jest używana. Na przykład "256" nie jest prawidłową wartością dla `byte` , ale jest prawidłowy dla. `int` "98,6" nie jest prawidłową wartością dla `int` , ale jest prawidłowy. `decimal`  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano `TryParse` `long`, jak używać z reprezentacjami ciągów wartości `decimal` , `byte`, i.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Pierwotne typy liczbowe implementują `Parse` również metodę statyczną, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą. `TryParse`jest zwykle bardziej wydajne, ponieważ zwraca wartość false, jeśli liczba jest nieprawidłowa.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze używaj `TryParse` metod lub `Parse` do sprawdzania poprawności danych wejściowych użytkownika z kontrolek, takich jak pola tekstowe i pola kombi.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konwertuj tablicę bajtów na liczbę całkowitą](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Instrukcje: Konwertuj ciąg na liczbę](../types/how-to-convert-a-string-to-a-number.md)
- [Instrukcje: Konwertuj między ciągi szesnastkowe i typy liczbowe](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analizowanie ciągów liczbowych](../../../standard/base-types/parsing-numeric.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
