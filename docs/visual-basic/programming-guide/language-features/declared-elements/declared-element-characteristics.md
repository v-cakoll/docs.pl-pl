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
ms.openlocfilehash: 9d1e327c25689bed1405ea9a627da6232abb707b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392951"
---
# <a name="declared-element-characteristics-visual-basic"></a>Zadeklarowana charakterystyka elementów (Visual Basic)
*Cechą* zadeklarowanego elementu jest aspekt tego elementu, który ma wpływ na sposób działania kodu. Każdy zadeklarowany element ma jedną lub więcej z następujących cech:  
  
- *Typ danych* — wartości, które może zawierać element, oraz sposób przechowywania tych wartości. Aby uzyskać więcej informacji, zobacz [typy danych](../../../language-reference/data-types/index.md).  
  
- *Okres istnienia* — okres czasu wykonywania, w którym element jest dostępny do użycia. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](lifetime.md).  
  
- *SCOPE* — zestaw wszystkich kodów, które mogą odwoływać się do elementu bez kwalifikowania jego nazwy. Aby uzyskać więcej informacji, zobacz [jak: kontrolowanie zakresu zmiennej](how-to-control-the-scope-of-a-variable.md).  
  
- *Poziom dostępu* — uprawnienie do kodu umożliwiające użycie elementu. Aby uzyskać więcej informacji, zobacz [jak: kontrolowanie dostępności zmiennej](how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Charakterystyki elementów  
 W poniższej tabeli przedstawiono zadeklarowane elementy i właściwości, które mają zastosowanie do każdego z nich.  
  
|Element|Typ danych|Okres istnienia|Zakres <sup>1</sup>|Poziom dostępu|  
|-------------|---------------|--------------|------------------------|------------------|  
|Zmienna|Tak|Tak|Tak|Tak|  
|Stały|Yes|Nie|Tak|Tak|  
|Wyliczenie|Yes|Nie|Tak|Tak|  
|Struktura|Nie|Nie|Tak|Tak|  
|Właściwość|Tak|Tak|Tak|Tak|  
|Metoda|Nie|Tak|Tak|Tak|  
|Procedura ( `Sub` lub `Function` )|Nie|Tak|Tak|Tak|  
|Parametr procedury|Tak|Tak|Tak|Nie|  
|Zwracanie funkcji|Tak|Tak|Tak|Nie|  
|Operator|Yes|Nie|Tak|Tak|  
|Interfejs|Nie|Nie|Tak|Tak|  
|Klasa|Nie|Nie|Tak|Tak|  
|Wydarzenie|Nie|Nie|Tak|Tak|  
|Delegat|Nie|Nie|Tak|Tak|  
  
 <sup>1</sup> zakres jest czasami określany jako *widoczność*.  
  
## <a name="see-also"></a>Zobacz też

- [Zadeklarowane elementy](index.md)
- [Nazwy zadeklarowanych elementów](declared-element-names.md)
- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Okres istnienia w Visual Basic](lifetime.md)
- [Zakres w Visual Basic](scope.md)
- [Poziomy dostępu w Visual Basic](access-levels.md)
- [Typy danych](../data-types/index.md)
- [Deklaracja zmiennej](../variables/variable-declaration.md)
