---
title: "Znaki — Typy danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1066444ba3a98f26fc2a35135a50b2954c6b992
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="character-data-types-visual-basic"></a>Znaki — Typy danych (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]udostępnia *znakowe typy danych* radzenia sobie z znaków drukowalnych i którą można wyświetlić. Gdy oba postępowania w przypadku znaków Unicode, `Char` przechowuje pojedynczym znakiem, podczas gdy `String` zawiera nieokreśloną liczbę znaków.  
  
 Dla tabeli, która zawiera porównanie side-by-side [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="char-type"></a>CHAR — typ  
 `Char` Typ danych to pojedynczy znak Unicode dwubajtowych (16-bitowe). Jeśli zmienna przechowuje zawsze dokładnie jeden znak, Zadeklaruj ją jako `Char`. Na przykład:  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 Każdej możliwej wartości w `Char` lub `String` zmienna jest *punktem kodu*, lub kod znaku w zestawie znaków Unicode. Znaków Unicode należą do zestawu znaków ASCII, różnych innych litery alfabetu, akcentów, symbol waluty, ułamków, znaków diakrytycznych i symbole matematyczne i technicznych.  
  
> [!NOTE]
>  Zestaw znaków Unicode rezerw D800 za pośrednictwem DFFF (55296 za pośrednictwem 55551 decimal) dla punktów kod *dwuskładnikowy pary*, co wymaga dwóch wartości 16-bitowych reprezentuje punkt jeden kod. A `Char` zmiennej nie może zawierać para zastępcza, a `String` używa do przechowywania takich parze dwie pozycje.  
  
 Aby uzyskać więcej informacji, zobacz [Char — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>String — typ  
 `String` — Typ danych jest sekwencją zero lub więcej znaków Unicode (16-bitowy) dwubajtowych. Jeśli zmienna może zawierać dowolną liczbę znaków, Zadeklaruj ją jako `String`. Na przykład:  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozwiązywanie problemów z typów danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
