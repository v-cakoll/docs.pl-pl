---
title: Default (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
