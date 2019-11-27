---
title: Charakterystyka zadeklarowanych elementów
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 4e03cd28fed5e0ae109337739251c11a0ff3424a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331624"
---
# <a name="declared-element-characteristics-visual-basic"></a>Zadeklarowana charakterystyka elementów (Visual Basic)
*Cechą* zadeklarowanego elementu jest aspekt tego elementu, który ma wpływ na sposób działania kodu. Każdy zadeklarowany element ma jedną lub więcej z następujących cech:  
  
- *Typ danych* — wartości, które może zawierać element, oraz sposób przechowywania tych wartości. Aby uzyskać więcej informacji, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
- *Okres istnienia* — okres czasu wykonywania, w którym element jest dostępny do użycia. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- *SCOPE* — zestaw wszystkich kodów, które mogą odwoływać się do elementu bez kwalifikowania jego nazwy. Aby uzyskać więcej informacji, zobacz [jak: kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
- *Poziom dostępu* — uprawnienie do kodu umożliwiające użycie elementu. Aby uzyskać więcej informacji, zobacz [jak: kontrolowanie dostępności zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Charakterystyki elementów  
 W poniższej tabeli przedstawiono zadeklarowane elementy i właściwości, które mają zastosowanie do każdego z nich.  
  
|Element|Typ danych|Okres istnienia|Zakres <sup>1</sup>|Poziom dostępu|  
|-------------|---------------|--------------|------------------------|------------------|  
|Zmienna|Tak|Tak|Tak|Tak|  
|Stała|Tak|Nie|Tak|Tak|  
|Wyliczenie|Tak|Nie|Tak|Tak|  
|Struktura|Nie|Nie|Tak|Tak|  
|Właściwość|Tak|Tak|Tak|Tak|  
|Metoda|Nie|Tak|Tak|Tak|  
|Procedura (`Sub` lub `Function`)|Nie|Tak|Tak|Tak|  
|Parametr procedury|Tak|Tak|Tak|Nie|  
|Zwracanie funkcji|Tak|Tak|Tak|Nie|  
|Operator|Tak|Nie|Tak|Tak|  
|Interface|Nie|Nie|Tak|Tak|  
|Class|Nie|Nie|Tak|Tak|  
|Zdarzenie|Nie|Nie|Tak|Tak|  
|Delegate|Nie|Nie|Tak|Tak|  
  
 <sup>1</sup> zakres jest czasami określany jako *widoczność*.  
  
## <a name="see-also"></a>Zobacz także

- [Zadeklarowane elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
