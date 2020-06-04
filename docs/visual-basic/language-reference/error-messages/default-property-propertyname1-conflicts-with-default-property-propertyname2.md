---
title: Właściwość domyślna „<propertyname1>" powoduje konflikt z właściwością domyślną „<propertyname2>” w „<classname>" i dlatego należy ją zadeklarować jako „Shadows”
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409728"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>Właściwość domyślna „\<propertyname1>" powoduje konflikt z właściwością domyślną „\<propertyname2>” w „\<classname>" i dlatego należy ją zadeklarować jako „Shadows”
Właściwość jest zadeklarowana z taką samą nazwą jak Właściwość zdefiniowana w klasie bazowej. W tej sytuacji właściwość w tej klasie powinna zasłaniać właściwość klasy bazowej.  
  
 Ten komunikat jest ostrzeżeniem. `Shadows`jest domyślnie przyjmowana. Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40007  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj `Shadows` słowo kluczowe do deklaracji lub Zmień nazwę zadeklarowanej właściwości.  
  
## <a name="see-also"></a>Zobacz też

- [Shadows](../modifiers/shadows.md)
- [Przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
