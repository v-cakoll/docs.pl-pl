---
title: Domyślny
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
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351581"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
Identyfikuje właściwość jako domyślną właściwość klasy, struktury lub interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Klasa, struktura lub interfejs może wyznaczyć najwyżej jedną z właściwości jako *Właściwość domyślną*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr. Jeśli kod tworzy odwołanie do klasy lub struktury bez określania elementu członkowskiego, Visual Basic rozpoznaje to odwołanie do właściwości domyślnej.  
  
 Właściwości domyślne mogą spowodować niewielkie zmniejszenie kodu źródłowego, ale może to utrudnić odczytywanie kodu. Jeśli kod wywołujący nie jest zaznajomiony z klasą lub strukturą, gdy tworzy odwołanie do nazwy klasy lub struktury, nie można określić, czy odwołanie uzyskuje dostęp do samej klasy lub struktury, czy też do właściwości domyślnej. Może to prowadzić do błędów kompilatora lub niewielkich błędów logiki czasu wykonywania.  
  
 Możesz nieco skrócić ryzyko błędów właściwości domyślnych, zawsze używając [instrukcji Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) , aby ustawić sprawdzanie typu kompilatora do `On`.  
  
 Jeśli planujesz użycie wstępnie zdefiniowanej klasy lub struktury w kodzie, musisz określić, czy ma ona właściwość domyślną, a jeśli tak, to jaki jest jej nazwa.  
  
 Ze względu na te wady należy rozważyć niedefiniowanie właściwości domyślnych. Aby uzyskać czytelność kodu, należy również rozważyć zawsze odwołanie do wszystkich właściwości jawnie, nawet właściwości domyślnych.  
  
 Modyfikator `Default` może być używany w tym kontekście:  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
