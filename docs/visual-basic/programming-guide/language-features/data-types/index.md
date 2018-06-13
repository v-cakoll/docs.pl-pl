---
title: Typy danych w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 855e32463284604fc27d4b73331ae48967dddefb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650455"
---
# <a name="data-types-in-visual-basic"></a>Typy danych w Visual Basic
*— Typ danych* elementu programowania odwołuje się do jakiego rodzaju dane można przechowywać i jak są przechowywane dane. Typy danych są stosowane do wszystkich wartości, które mogą być przechowywane w pamięci komputera lub udziału podczas obliczania wyrażenia. Każdej zmiennej, literał, stała, wyliczenie, właściwości, parametru procedury, argumentu procedury oraz procedury zwracanej wartości musi typu danych.  
  
## <a name="declared-data-types"></a>Zadeklarowany typy danych  
 Zdefiniuj elementu programistycznego z instrukcją deklaracji oraz określić jego typu danych z `As` klauzuli. W poniższej tabeli przedstawiono instrukcje używanego do zadeklarowania różnych elementów.  
  
|Element programowania|Deklaracja typu danych|  
|-------------------------|---------------------------|  
|Zmienna|W [Dim — instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literału|Znak literalny typu; zobacz "Literał znaków typu" w [znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Stała|W [Const — instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Wyliczenie|W [Enum — instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Właściwość|W [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr procedury|W [Sub instrukcji](../../../../visual-basic/language-reference/statements/sub-statement.md), [funkcji instrukcji](../../../../visual-basic/language-reference/statements/function-statement.md), lub [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argumentu procedury|W wywoływanym kodzie; Każdy argument jest elementem programowania, który został już zadeklarowany lub wyrażenia zawierającego zadeklarowane elementy<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Wartość zwracana procedury|W [funkcji instrukcji](../../../../visual-basic/language-reference/statements/function-statement.md) lub [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Aby uzyskać listę typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Krotki](tuples.md)     
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
