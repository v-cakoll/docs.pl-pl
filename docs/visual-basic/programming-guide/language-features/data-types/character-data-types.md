---
title: Znakowe typy danych
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 33dd4c62776ae8c5ec0ce0a6d0858a7ed0d047fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401995"
---
# <a name="character-data-types-visual-basic"></a>Znaki — Typy danych (Visual Basic)
Visual Basic zawiera *typy danych znakowych* , które umożliwiają rozproszenie i drukowalne znaki. Chociaż obydwie zajmują się znakami Unicode, `Char` przechowuje pojedynczy znak, a `String` zawiera nieokreśloną liczbę znaków.  
  
 W przypadku tabeli wyświetlającej porównanie obok Visual Basic typów danych, zobacz [typy danych](../../../language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Typ char  
 `Char`Typ danych to pojedynczy dwubajtowy znak Unicode (16-bitowy). Jeśli zmienna zawsze przechowuje dokładnie jeden znak, zadeklaruj go jako `Char` . Przykład:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Każda możliwa wartość w `Char` zmiennej or `String` jest *punktem kodu*lub kodem znaku w zestawie znaków Unicode. Znaki Unicode obejmują podstawowy zestaw znaków ASCII, różne litery alfabetu, akcenty, symbole waluty, ułamki, znaki diakrytyczne i symbole matematyczne i techniczne.  
  
> [!NOTE]
> Zestaw znaków Unicode rezerwuje punkty kodu D800 przez DFFF (55296 do 55551 dziesiętnych) dla *par surogatów*, które wymagają wartości 2 16-bitowych do reprezentowania pojedynczego punktu kodu. `Char`Zmienna nie może zawierać pary zastępczej i `String` używa dwóch pozycji do przechowywania takiej pary.  
  
 Aby uzyskać więcej informacji, zobacz [char Data Type](../../../language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Typ ciągu  
 `String`Typ danych jest sekwencją zero lub więcej dwubajtowych (16-bitowych) znaków Unicode. Jeśli zmienna może zawierać nieokreśloną liczbę znaków, zadeklaruj ją jako `String` . Przykład:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Aby uzyskać więcej informacji, zobacz [Typ danych ciągu](../../../language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych podstawowych](elementary-data-types.md)
- [Złożone typy danych](composite-data-types.md)
- [Typy ogólne w Visual Basic](generic-types.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Konwersje plików w Visual Basic](type-conversions.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Znaki typu](type-characters.md)
