---
title: Znaki — Typy danych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965678"
---
# <a name="character-data-types-visual-basic"></a>Znaki — Typy danych (Visual Basic)
Visual Basic zawiera *typy danych znakowych* , które umożliwiają rozproszenie i drukowalne znaki. Chociaż obydwie zajmują się znakami `Char` Unicode, przechowuje pojedynczy `String` znak, a zawiera nieokreśloną liczbę znaków.  
  
 W przypadku tabeli wyświetlającej porównanie obok Visual Basic typów danych, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Typ char  
 Typ `Char` danych to pojedynczy dwubajtowy znak Unicode (16-bitowy). Jeśli zmienna zawsze przechowuje dokładnie jeden znak, zadeklaruj go jako `Char`. Przykład:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Każda możliwa wartość w `Char` zmiennej or `String` jest *punktem kodu*lub kodem znaku w zestawie znaków Unicode. Znaki Unicode obejmują podstawowy zestaw znaków ASCII, różne litery alfabetu, akcenty, symbole waluty, ułamki, znaki diakrytyczne i symbole matematyczne i techniczne.  
  
> [!NOTE]
> Zestaw znaków Unicode rezerwuje punkty kodu D800 przez DFFF (55296 do 55551 dziesiętnych) dla *par surogatów*, które wymagają wartości 2 16-bitowych do reprezentowania pojedynczego punktu kodu. Zmienna nie może zawierać pary zastępczej `String` i używa dwóch pozycji do przechowywania takiej pary. `Char`  
  
 Aby uzyskać więcej informacji, zobacz [char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Typ ciągu  
 Typ `String` danych jest sekwencją zero lub więcej dwubajtowych (16-bitowych) znaków Unicode. Jeśli zmienna może zawierać nieokreśloną liczbę znaków, zadeklaruj ją jako `String`. Na przykład:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Aby uzyskać więcej informacji, zobacz [Typ danych ciągu](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
