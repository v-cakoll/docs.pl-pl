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
ms.openlocfilehash: 83c3d9976f61513165e917da73dd50e846db3e83
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565206"
---
# <a name="data-types-in-visual-basic"></a>Typy danych w Visual Basic
*— Typ danych* elementu programistycznego odwołuje się do jakiego rodzaju dane można przechowywać i jak są przechowywane dane. Typy danych są stosowane do wszystkich wartości, które mogą być przechowywane w pamięci komputera i uczestniczyć w wyniku obliczenia wyrażenia. Każdej zmiennej, literał, — stała, wyliczenia, właściwości, parametr procedury, argumentu procedury i procedury zwracana wartość ma typ danych.  
  
## <a name="declared-data-types"></a>Zadeklarowane typy danych  
 Należy zdefiniować element programowania za pomocą instrukcji deklaracji i określić typ jej danych w taki sposób, przy użyciu `As` klauzuli. W poniższej tabeli przedstawiono instrukcje, których używasz do deklarowania różnych elementów.  
  
|Element programowania|Deklaracja typu danych|  
|-------------------------|---------------------------|  
|Zmienna|W [Dim — instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|literał|Znak literalny typu; zobacz "Znaki literału typu" w [znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Stała|W [Const — instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Wyliczenie|W [Enum — instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Właściwość|W [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr procedury|W [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md), [funkcji instrukcji](../../../../visual-basic/language-reference/statements/function-statement.md), lub [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argumentu procedury|W wywoływanym kodzie; Każdy argument jest elementem programowania, który został już zadeklarowany lub wyrażeniu zawierającym zadeklarowane elementy<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Wartość zwracana procedury|W [funkcji instrukcji](../../../../visual-basic/language-reference/statements/function-statement.md) lub [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Aby uzyskać listę typów danych języka Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
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
 [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)  
 [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
