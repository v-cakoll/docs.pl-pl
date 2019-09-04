---
title: Funkcje ciągów Canonical
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: 9013b8bd8505442666dd0688eaf2586959a61b70
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249094"
---
# <a name="string-canonical-functions"></a>Funkcje ciągów Canonical
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera funkcje w postaci kanonicznej.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono funkcje kanoniczne ciągu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`Concat(string1, string2)`|Zwraca ciąg, który zawiera `string2` dołączone do. `string1`<br /><br /> **Argumenty**<br /><br /> `string1`: Ciąg, do którego `string2` jest dołączany.<br /><br /> `string2`: Ciąg, który jest dołączany `string1`do.<br /><br /> **Wartość zwracana**<br /><br /> A `String`. Wystąpi błąd, jeśli długość ciągu wartości zwracanej jest większa niż maksymalna dozwolona długość.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|Zwraca `true` wartość `target` , jeśli jest `string`zawarta w.<br /><br /> **Argumenty**<br /><br /> `string`: Przeszukiwany ciąg.<br /><br /> `target`: Docelowy ciąg, który jest wyszukiwany.<br /><br /> **Wartość zwracana**<br /><br /> `true`Jeśli `target` jest zawarta w `false` `string`; w przeciwnym razie.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|Zwraca `true` wartość `target` , jeśli `string`kończyć się znakiem.<br /><br /> **Argumenty**<br /><br /> `string`: Przeszukiwany ciąg.<br /><br /> `target`: Ciąg docelowy przeszukany na końcu `string`.<br /><br /> **Wartość zwracana**<br /><br /> `True`w `string` przypadku zakończenia `target`z; `false`w przeciwnym razie.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')`**Uwaga:**  Jeśli używasz dostawcy danych SQL Server, ta funkcja zwraca wartość `false` , jeśli ciąg jest przechowywany w kolumnie ciągu o stałej długości i `target` jest stałą. W takim przypadku przeszukiwany jest cały ciąg, w tym wszystkie spacje końcowe uzupełniania. Możliwym obejściem jest przycinanie danych w ciągu o stałej długości, jak w poniższym przykładzie:`EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|Zwraca pozycję `target` wewnątrz `string`lub wartość 0, jeśli nie można jej odnaleźć. Zwraca wartość 1, aby wskazać początek `string`. Numerowanie indeksu rozpoczyna się od 1.<br /><br /> **Argumenty**<br /><br /> `target`: Ciąg, który jest wyszukiwany.<br /><br /> `string`: Przeszukiwany ciąg.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|Zwraca pierwsze `length` znaki z lewej `string`strony. Jeśli długość `string` jest mniejsza niż `length`, zwracany jest cały ciąg.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, ,,`Int64`Lub .`Byte` `Int32` `length`nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Zwraca (`Int32`) Długość ciągu znaków.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Zwraca `string` bez wiodącego odstępu.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|Zwraca `string1`, ze wszystkimi wystąpieniami `string2` zamienionymi `string3`przez.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Zwraca `string` z kolejnością znaków odwróconych.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Zwraca ostatnie `length` znaki `string`z. Jeśli długość `string` jest mniejsza niż `length`, zwracany jest cały ciąg.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, ,,`Int64`Lub .`Byte` `Int32` `length`nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Zwraca `string` bez końcowego odstępu.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.|  
|`Substring(string, start, length)`|Zwraca podciąg ciągu zaczynający się na pozycji `start`o `length` długości znaków. Początek 1 wskazuje pierwszy znak ciągu. Numerowanie indeksu rozpoczyna się od 1.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `start`: `Int16`, ,`Int32` I`Byte`. `Int64` `start`nie może być mniejsze niż jeden.<br /><br /> `length`: `Int16`, ,`Int32` I`Byte`. `Int64` `length`nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|Zwraca `true` wartość `string` , jeśli `target`zaczyna się od.<br /><br /> **Argumenty**<br /><br /> `string`: Przeszukiwany ciąg.<br /><br /> `target`: Docelowy ciąg wyszukiwany `string`na początku.<br /><br /> **Wartość zwracana**<br /><br /> `True`Jeśli `string` `false`zaczyna się od ;wprzeciwnymrazie.`target`<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Zwraca `string` z dużymi znakami przekonwertowanymi na małe litery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Zwraca `string` małe litery konwertowane na wielkie litery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Zwraca `string` bez odstępów wiodących i końcowych.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Te funkcje zostaną zwrócone `null` , jeśli `null` dane wejściowe.  
  
 Równoważne funkcje są dostępne w dostawcy zarządzanym przez klienta programu Microsoft SQL. Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Canonical](canonical-functions.md)
