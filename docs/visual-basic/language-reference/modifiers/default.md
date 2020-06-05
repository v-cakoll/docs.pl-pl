---
title: Domyślne
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
ms.openlocfilehash: 0c2808795d6fcbad7892369fd7f460ebf0406093
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372975"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
Identyfikuje właściwość jako domyślną właściwość klasy, struktury lub interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Klasa, struktura lub interfejs może wyznaczyć najwyżej jedną z właściwości jako *Właściwość domyślną*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr. Jeśli kod tworzy odwołanie do klasy lub struktury bez określania elementu członkowskiego, Visual Basic rozpoznaje to odwołanie do właściwości domyślnej.  
  
 Właściwości domyślne mogą spowodować niewielkie zmniejszenie kodu źródłowego, ale może to utrudnić odczytywanie kodu. Jeśli kod wywołujący nie jest zaznajomiony z klasą lub strukturą, gdy tworzy odwołanie do nazwy klasy lub struktury, nie można określić, czy odwołanie uzyskuje dostęp do samej klasy lub struktury, czy też do właściwości domyślnej. Może to prowadzić do błędów kompilatora lub niewielkich błędów logiki czasu wykonywania.  
  
 Możesz nieco skrócić ryzyko błędów właściwości domyślnych, zawsze używając [instrukcji Option Strict](../statements/option-strict-statement.md) , aby ustawić sprawdzanie typu kompilatora `On` .  
  
 Jeśli planujesz użycie wstępnie zdefiniowanej klasy lub struktury w kodzie, musisz określić, czy ma ona właściwość domyślną, a jeśli tak, to jaki jest jej nazwa.  
  
 Ze względu na te wady należy rozważyć niedefiniowanie właściwości domyślnych. Aby uzyskać czytelność kodu, należy również rozważyć zawsze odwołanie do wszystkich właściwości jawnie, nawet właściwości domyślnych.  
  
 `Default`Modyfikator może być używany w tym kontekście:  
  
 [Property — Instrukcja](../statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Słowa kluczowe](../keywords/index.md)
