---
title: Canonical funkcje ciągów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 8bead8bc61c06a2daf4dd95dca8808caf823f245
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="string-canonical-functions"></a>Canonical funkcje ciągów
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obejmuje funkcje canonical ciągów.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono ciąg [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`Concat (` `string1`, `string2``)`|Zwraca ciąg zawierający `string2` dołączany do `string1`.<br /><br /> **Argumenty**<br /><br /> `string1`: Ciąg, do którego `string2` jest dołączony.<br /><br /> `string2`: Ciąg, który jest dołączany do `string1`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`. Jeśli długość ciągu zwracana wartość jest większa niż maksymalna dozwolona długość, wystąpi błąd.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains (` `string`, `target``)`|Zwraca `true` Jeśli `target` znajduje się w `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> `target`Ciąg docelowego jest wyszukiwany.<br /><br /> **Wartość zwracana**<br /><br /> `true` Jeśli `target` znajduje się w `string`; w przeciwnym razie `false`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith (` `string`, `target``)`|Zwraca `true` Jeśli `target` kończy `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> `target`: Ciąg docelowego wyszukiwane na końcu `string`.<br /><br /> **Wartość zwracana**<br /><br /> `True` Jeśli `string` kończy `target`; w przeciwnym razie `false`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` **Uwaga:** Jeśli używasz dostawcy danych programu SQL Server, funkcja zwraca `false` Jeśli ciąg jest przechowywany w kolumnie ciągu o stałej długości i `target` jest stałą. W takim przypadku cały ciąg będzie przeszukiwana, w tym wszelkie uzupełnienia spacje końcowe. Możliwym obejściem jest trim danych w ciągu o stałej długości, jak w poniższym przykładzie: `EndsWith(TRIM(string), target)`|  
|`IndexOf(` `target`, `string``)`|Zwraca pozycję `target` wewnątrz `string`, lub 0, jeśli nie został odnaleziony. Zwraca wartość 1, aby wskazać początku `string`. Indeks numerowanie rozpoczyna się od 1.<br /><br /> **Argumenty**<br /><br /> `target`: Ciąg, który jest wyszukiwany.<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left (` `string`, `length``)`|Zwraca pierwszy `length` znaków z lewej strony `string`. Jeśli długość `string` jest mniejsza niż `length`, zostanie zwrócony cały ciąg.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, `Int32`, `Int64`, Lub `Byte`. `length` nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length (` `string` `)`|Zwraca (`Int32`) długość w znakach ciągu.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(` `string` `)`|Zwraca `string` bez spacji wiodących.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace (` `string1`, `string2`, `string3``)`|Zwraca `string1`, ze wszystkie wystąpienia `string2` zastępuje `string3`.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse (` `string` `)`|Zwraca `string` z kolejnością znaków wycofane.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right (` `string`, `length``)`|Zwraca ostatni `length` znaki `string`. Jeśli długość `string` jest mniejsza niż `length`, zostanie zwrócony cały ciąg.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, `Int32`, `Int64`, Lub `Byte`. `length` nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(` `string` `)`|Zwraca `string` bez spacji końcowych.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.|  
|`Substring (` `string`, `start`, `length``)`|Zwraca podciąg ciągu, zaczynając od pozycji `start`, o długości `length` znaków. Początek 1 oznacza pierwszego znaku ciągu. Indeks numerowanie rozpoczyna się od 1.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `start`: `Int16`, `Int32`, `Int64` i `Byte`. `start` nie może być mniejsza niż jedna.<br /><br /> `length`: `Int16`, `Int32`, `Int64` i `Byte`. `length` nie może być mniejsza od zera.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith (` `string`, `target``)`|Zwraca `true` Jeśli `string` rozpoczyna się od `target`.<br /><br /> **Argumenty**<br /><br /> `string`: Ciąg, który jest przeszukiwany.<br /><br /> `target`: Docelowy ciąg wyszukiwany w chwili rozpoczęcia `string`.<br /><br /> **Wartość zwracana**<br /><br /> `True` Jeśli `string` rozpoczyna się od `target`; w przeciwnym razie `false`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(` `string` `)`|Zwraca `string` z wielkich liter przekształcone na małe litery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(` `string` `)`|Zwraca `string` z małych liter przekonwertowany na wielkie litery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(` `string` `)`|Zwraca `string` bez spacje wiodące i końcowe.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Wartość zwracana**<br /><br /> A `String`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Te funkcje będą zwracać `null` Jeśli podane `null` wejściowego.  
  
 Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [SqlClient Entity Framework funkcji](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
