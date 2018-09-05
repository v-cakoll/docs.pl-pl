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
ms.openlocfilehash: 3b031c6e3dc04637128f95ca8e922d3298981287
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553575"
---
# <a name="character-data-types-visual-basic"></a>Znaki — Typy danych (Visual Basic)
Visual Basic oferuje *typ danych znakowych* radzenia sobie z drukowania i zawiera znaki. Gdy oba postępowania ze znakami Unicode `Char` zawiera pojedynczy znak, natomiast `String` zawiera nieokreśloną liczbę znaków.  
  
 Dla tabeli, która wyświetla porównania side-by-side typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>CHAR — typ  
 `Char` Typ danych jest jednym dwóch-bajtowych wartości znakowych Unicode (16-bitowy). Jeśli zmienna przechowuje zawsze dokładnie jeden znak, Zadeklaruj go jako `Char`. Na przykład:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Każdej możliwej wartości w `Char` lub `String` zmienna jest *punktem kodu*, lub kod znaku w zestawie znaków Unicode. Znaki Unicode obejmują podstawowy zestaw znaków ASCII, różne inne litery alfabetu, akcentów, symbole walut, ułamki, znaki diakrytyczne i symbole matematyczne i technicznych.  
  
> [!NOTE]
>  Zestaw znaków Unicode rezerwy kod wskazuje D800 za pośrednictwem DFFF (55296 za pośrednictwem 55551 dziesiętna) dla *zastępczych par*, które wymagają dwóch wartości 16-bitowych reprezentuje punkt kodu jednego. A `Char` zmiennej nie może utrzymywać para zastępcza i `String` używa dwóch pozycji do przechowywania tych pary.  
  
 Aby uzyskać więcej informacji, zobacz [Char — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>String — typ  
 `String` — Typ danych to sekwencja zero lub więcej znaków Unicode (16-bitowy) dwóch bajtów. Jeśli zmienna może zawierać dowolną liczbę znaków, Zadeklaruj go jako `String`. Na przykład:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Aby uzyskać więcej informacji, zobacz [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
