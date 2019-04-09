---
title: Funkcje ciągów Canonical
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: bfd18f0302b897dabd7c75118e3892df6153ea63
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155288"
---
# <a name="string-canonical-functions"></a>Funkcje ciągów Canonical
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obejmuje funkcje ciągów canonical.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono ciąg [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`Concat(string1, string2)`|Zwraca ciąg, który zawiera `string2` dołączany do `string1`.<br /><br /> **Argumenty**<br /><br /> `string1`: Ciąg, do którego `string2` jest dołączany.<br /><br /> `string2`: Ciąg, który jest dołączany do `string1`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`. Wystąpi błąd, jeśli długość ciągu wartość zwracana jest większa niż maksymalna dozwolona długość.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|Zwraca `true` Jeśli `target` znajduje się w `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> `target`: Docelowy ciąg wyszukiwania.<br /><br /> **Wartość zwracana**<br /><br /> `true` Jeśli `target` znajduje się w `string`; w przeciwnym razie `false`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|Zwraca `true` Jeśli `target` kończy się `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> `target`: Ciąg docelowy wyszukiwane na końcu `string`.<br /><br /> **Wartość zwracana**<br /><br /> `True` Jeśli `string` kończy się `target`; w przeciwnym razie `false`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` ***Uwaga:**  Jeśli używasz dostawcy danych programu SQL Server, ta funkcja zwraca `false` Jeśli ciąg jest przechowywany w kolumnie o stałej długości ciągu i `target` jest stałą.IW tym przypadku cały ciąg jest przeszukiwany, włączając wszelkie dopełnienie spacje końcowe.AMożliwym obejściem jest można przycięcia danych w ciągu o stałej długości, jak w poniższym przykładzie:`EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|Zwraca pozycję `target` wewnątrz `string`, lub 0, jeśli nie można odnaleźć. Zwraca wartość 1 w celu określenia początku `string`. Indeks numerowania rozpoczyna się od 1.<br /><br /> **Argumenty**<br /><br /> `target`: Ciąg, który jest wyszukiwany.<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|Zwraca pierwszy `length` znaków z lewej części `string`. Jeśli długość `string` jest mniejsza niż `length`, zwracany jest cały ciąg.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, `Int32`, `Int64`, Lub `Byte`. `length` nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Zwraca (`Int32`) długość w znakach ciągu.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Zwraca `string` bez wiodącego biały znak.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|Zwraca `string1`, za pomocą wszystkich wystąpień `string2` zastępuje `string3`.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Zwraca `string` z kolejnością znaków odwrócony.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Zwraca ostatni `length` znaków z `string`. Jeśli długość `string` jest mniejsza niż `length`, zwracany jest cały ciąg.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, `Int32`, `Int64`, Lub `Byte`. `length` nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Zwraca `string` bez odstępu.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.|  
|`Substring(string, start, length)`|Zwraca podciąg ciągu, zaczynając od pozycji `start`, o długości `length` znaków. Początek 1 wskazuje pierwszym znakiem ciągu. Indeks numerowania rozpoczyna się od 1.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `start`: `Int16`, `Int32`, `Int64` i `Byte`. `start` nie może być mniejsza niż jeden.<br /><br /> `length`: `Int16`, `Int32`, `Int64` i `Byte`. `length` nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|Zwraca `true` Jeśli `string` rozpoczyna się od `target`.<br /><br /> **Argumenty**<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> `target`: Ciąg docelowy wyszukiwane na początku `string`.<br /><br /> **Wartość zwracana**<br /><br /> `True` Jeśli `string` rozpoczyna się od `target`; w przeciwnym razie `false`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Zwraca `string` przy użyciu wielkich liter konwertowane na małe litery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Zwraca `string` z małych liter przekonwertowany na wielkie litery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Zwraca `string` bez początkowe i końcowe biały.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.  
  
 Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
