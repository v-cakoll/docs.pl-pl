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
ms.openlocfilehash: 928d7fb6a40873641ae3e91e057c272b946a0091
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393717"
---
# <a name="data-types-in-visual-basic"></a>Typy danych w Visual Basic
*Typ danych* elementu programistycznego odnosi się do rodzaju danych, które mogą być przechowywane, i sposobu przechowywania tych danych. Typy danych mają zastosowanie do wszystkich wartości, które mogą być przechowywane w pamięci komputera lub do oceny wyrażenia. Każda zmienna, literał, stała, Wyliczenie, właściwość, parametr procedury, argument procedury i wartość zwracana przez procedurę ma typ danych.  
  
## <a name="declared-data-types"></a>Zadeklarowane typy danych  
 Należy zdefiniować element programistyczny z instrukcją deklaracji i określić jego typ danych z `As` klauzulą. W poniższej tabeli przedstawiono instrukcje używane do deklarowania różnych elementów.  
  
|Element programowania|Deklaracja typu danych|  
|-------------------------|---------------------------|  
|Zmienna|W [instrukcji Dim](../../../language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literał|Znakiem typu literału; Zobacz "znaki typu literal" w [znakach typu](type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Stały|W [instrukcji const](../../../language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Wyliczenie|W [instrukcji enum](../../../language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Właściwość|W [instrukcji właściwości](../../../language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr procedury|W instrukcji [Sub](../../../language-reference/statements/sub-statement.md), [instrukcji funkcyjnej](../../../language-reference/statements/function-statement.md)lub [instrukcji operatora](../../../language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argument procedury|W kodzie wywołującym; Każdy argument jest elementem programistycznym, który został już zadeklarowany, lub wyrażeniem zawierającym zadeklarowane elementy<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Zwracana wartość procedury|W [instrukcji funkcyjnej](../../../language-reference/statements/function-statement.md) lub [instrukcji operatora](../../../language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Aby uzyskać listę typów danych Visual Basic, zobacz [typy danych](../../../language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [Znaki typu](type-characters.md)
- [Typy danych podstawowych](elementary-data-types.md)
- [Złożone typy danych](composite-data-types.md)
- [Typy ogólne w Visual Basic](generic-types.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Konwersje plików w Visual Basic](type-conversions.md)
- [Struktury](structures.md)
- [Krotki](tuples.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Typy danych](../../../language-reference/data-types/index.md)
- [Skuteczne stosowanie typów danych](efficient-use-of-data-types.md)
