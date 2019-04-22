---
title: Właściwość domyślna „<propertyname1>" powoduje konflikt z właściwością domyślną „<propertyname2>” w „<classname>" i dlatego należy ją zadeklarować jako „Shadows”
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: ab45278b2e1199282e3066c34828b9bda716e162
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813174"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>Właściwość domyślna "\<propertyname1 >" powoduje konflikt z właściwością domyślną "\<NazwaWłaściwości2 >' w '\<nazwa_klasy >" i dlatego powinien być zadeklarowany jako "Shadows"
Właściwość jest zadeklarowany z taką samą nazwę jak właściwość zdefiniowana w klasie bazowej. W takiej sytuacji właściwości tej klasy należy w tle właściwości klasy bazowej.  
  
 Ta wiadomość jest ostrzeżenie. `Shadows` zakłada, że domyślnie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40007  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj `Shadows` — słowo kluczowe do deklaracji lub zmień nazwę właściwości został zadeklarowany.  
  
## <a name="see-also"></a>Zobacz także

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
