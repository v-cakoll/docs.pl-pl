---
title: Typy danych
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 01529b36a68b8db6febb80b69a7bd81486a47087
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346350"
---
# <a name="data-types-in-visual-basic"></a>Typy danych w Visual Basic
*Typ danych* elementu programistycznego odnosi się do rodzaju danych, które mogą być przechowywane, i sposobu przechowywania tych danych. Typy danych mają zastosowanie do wszystkich wartości, które mogą być przechowywane w pamięci komputera lub do oceny wyrażenia. Każda zmienna, literał, stała, Wyliczenie, właściwość, parametr procedury, argument procedury i wartość zwracana przez procedurę ma typ danych.  
  
## <a name="declared-data-types"></a>Zadeklarowane typy danych  
 Należy zdefiniować element programistyczny z instrukcją deklaracji i określić jego typ danych z klauzulą `As`. W poniższej tabeli przedstawiono instrukcje używane do deklarowania różnych elementów.  
  
|Element programowania|Deklaracja typu danych|  
|-------------------------|---------------------------|  
|Zmienna|W [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Wpisać|Znakiem typu literału; Zobacz "znaki typu literal" w [znakach typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Stała|W [instrukcji const](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Wyliczenie|W [instrukcji enum](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Właściwość|W [instrukcji właściwości](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr procedury|W instrukcji [Sub](../../../../visual-basic/language-reference/statements/sub-statement.md), [instrukcji funkcyjnej](../../../../visual-basic/language-reference/statements/function-statement.md)lub [instrukcji operatora](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argument procedury|W kodzie wywołującym; Każdy argument jest elementem programistycznym, który został już zadeklarowany, lub wyrażeniem zawierającym zadeklarowane elementy<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Zwracana wartość procedury|W [instrukcji funkcyjnej](../../../../visual-basic/language-reference/statements/function-statement.md) lub [instrukcji operatora](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Aby uzyskać listę typów danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Krotki](tuples.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
