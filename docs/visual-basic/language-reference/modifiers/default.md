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
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836730"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
Identyfikuje właściwość jako domyślną właściwość klasy, struktury lub interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Klasy, struktury lub interfejsu można wyznaczyć co najwyżej jeden z jego właściwości jako *właściwość domyślna*pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr. Jeśli kod sprawia, że odwołanie do klasy lub struktury bez podania członek, Visual Basic rozpoznaje tego odwołania do właściwości domyślnej.  
  
 Właściwości domyślnych może spowodować zmniejszenie małe znaki kodu źródłowego, ale mogą robić więjsze kodu czytelność. Jeśli kod wywołujący nie są zaznajomieni z klasy lub struktury, jeśli go nawiązuje odwołanie do nazwy klasy lub struktury nie może być określone czy tego odwołania uzyskuje dostęp do, klasa lub struktura lub domyślnej właściwości. Może to prowadzić do błędów kompilatora lub błędy subtelne logiki czasu wykonywania.  
  
 Trochę zmniejsza ryzyko wystąpienia błędów właściwości domyślne przy użyciu zawsze [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawienie typu kompilatora sprawdzanie `On`.  
  
 Jeśli planujesz użyć wstępnie zdefiniowanych klasy lub struktury w kodzie, należy określić, czy ma ona właściwości domyślnej, a jeśli tak, jakie jego nazwa jest.  
  
 Z powodu niedogodności należy rozważyć nie definiuje właściwości domyślnych. Aby zwiększyć czytelność kodu należy również wziąć pod uwagę zawsze odwołujące się do wszystkich właściwości jawnie, nawet domyślne właściwości.  
  
 `Default` Modyfikatora można używać w tym kontekście:  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
