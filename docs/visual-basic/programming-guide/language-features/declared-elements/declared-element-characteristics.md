---
title: "Zadeklarowana charakterystyka elementów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26ee27d3a1d085c6ab45ae850dbdac700aa208a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="declared-element-characteristics-visual-basic"></a>Zadeklarowana charakterystyka elementów (Visual Basic)
A *cech* elementu zadeklarowane jest elementem tego elementu, który ma wpływ na kod może interakcje z nią. Każdy element zadeklarowane ma co najmniej jeden z następujących właściwości skojarzone z nią:  
  
-   *Typ danych* — może zawierać wartości elementu i jak przechowuje te wartości. Aby uzyskać więcej informacji, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
-   *Okres istnienia* — okres czasu, w którym element jest dostępny do użycia. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Zakres* — zestaw żadnego kodu, który może odwoływać się do elementu bez kwalifikujących się jego nazwy. Aby uzyskać więcej informacji, zobacz [porady: kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Poziom dostępu* — uprawnienia dla kod, aby użyć elementu. Aby uzyskać więcej informacji, zobacz [porady: kontrolowanie dostępności zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Właściwości elementów  
 W poniższej tabeli przedstawiono zadeklarowane elementy i właściwości, które są stosowane do każdej z nich.  
  
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
  
 <sup>1</sup> zakres jest czasami nazywany *widoczność*.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadeklarowane elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
