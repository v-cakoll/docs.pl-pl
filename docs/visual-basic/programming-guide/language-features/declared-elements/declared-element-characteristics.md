---
title: Zadeklarowana charakterystyka elementów (Visual Basic)
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
ms.openlocfilehash: 27dad8b2fbfbc8d17090df201bf36eb080966f51
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536524"
---
# <a name="declared-element-characteristics-visual-basic"></a>Zadeklarowana charakterystyka elementów (Visual Basic)
A *cechy* zadeklarowany element jest elementem tego elementu, który ma wpływ na sposób kod może korzystać z niego. Każdy element zadeklarowany ma co najmniej jeden z następujących właściwości, które są skojarzone z nią:  
  
-   *Typ danych* — może zawierać wartości elementu i jak przechowuje te wartości. Aby uzyskać więcej informacji, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
-   *Okres istnienia* — okres czasu, przez który element jest dostępny do użytku. Aby uzyskać więcej informacji, zobacz [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Zakres* — zestaw cały kod, który może odwoływać się do elementu bez kwalifikowania nazwy. Aby uzyskać więcej informacji, zobacz [porady: kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Poziom dostępu* — uprawnienia dla kod, aby użyć tego elementu. Aby uzyskać więcej informacji, zobacz [porady: kontrolowanie dostępności zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Właściwości elementów  
 W poniższej tabeli przedstawiono deklarowanych elementów i właściwości, które są stosowane do każdego z nich.  
  
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
|Return — funkcja|Tak|Tak|Tak|Nie|  
|Operator|Tak|Nie|Tak|Tak|  
|Interface|Nie|Nie|Tak|Tak|  
|Class|Nie|Nie|Tak|Tak|  
|Zdarzenie|Nie|Nie|Tak|Tak|  
|Delegate|Nie|Nie|Tak|Tak|  
  
 <sup>1</sup> zakres jest czasami określane jako *widoczność*.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadeklarowane elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
