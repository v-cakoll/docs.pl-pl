---
title: Default (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: 555e15110c7af501de05d1f395a72ca4b7800054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
Identyfikuje właściwość jako domyślną właściwość klasy, struktury lub interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Klasy, struktury lub interfejsu można wyznaczyć co najwyżej jednej z jego właściwości jako *domyślna właściwość*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr. Jeśli kod sprawia, że odwołanie do klasy lub struktury bez określenia członka, Visual Basic rozpoznaje odwołujące się do właściwości domyślnej.  
  
 Właściwości domyślnych może spowodować zmniejszenie małych znaków kodu źródłowego, ale może wprowadzić czytelność kodu. Jeśli kod wywołujący nie są zaznajomieni z klasy lub struktury, podczas wykonywania odwołanie do nazwy klasy lub struktury nie może być niektórych czy uzyskuje dostęp tego odwołania do klasy lub struktury, sam lub domyślnej właściwości. Może to prowadzić do błędów kompilatora lub błędy niewielkie logiki czasu wykonywania.  
  
 Nieco zmniejsza ryzyko błędów właściwości domyślne przy użyciu zawsze [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md) można ustawić typ kompilatora sprawdzania `On`.  
  
 Jeśli planujesz użyć wstępnie zdefiniowanych klasy lub struktury w kodzie, należy określić, czy ma ona domyślnej właściwości, a jeśli tak, jakie jego nazwa jest.  
  
 Z powodu niedogodności należy rozważyć nie definiuje właściwości domyślnych. Aby zwiększyć czytelność kodu należy również wziąć pod uwagę zawsze odwołujących się do wszystkich właściwości jawnie, nawet domyślnej właściwości.  
  
 `Default` Modyfikatora można używać w tym kontekście:  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
