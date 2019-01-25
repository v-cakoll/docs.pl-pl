---
title: Właściwość domyślna &#39; &lt;propertyname1&gt; &#39; powoduje konflikt z właściwością domyślną &#39; &lt;NazwaWłaściwości2&gt; &#39; w &#39; &lt;classname&gt; &#39;i dlatego powinien być zadeklarowany jako &#39;cieni&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 3099467fa3c5a162c13c9235fb8d55375953ba3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521429"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Właściwość domyślna &#39; &lt;propertyname1&gt; &#39; powoduje konflikt z właściwością domyślną &#39; &lt;NazwaWłaściwości2&gt; &#39; w &#39; &lt;classname&gt; &#39;i dlatego powinien być zadeklarowany jako &#39;cieni&#39;
Właściwość jest zadeklarowany z taką samą nazwę jak właściwość zdefiniowana w klasie bazowej. W takiej sytuacji właściwości tej klasy należy w tle właściwości klasy bazowej.  
  
 Ta wiadomość jest ostrzeżenie. `Shadows` zakłada, że domyślnie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40007  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj `Shadows` — słowo kluczowe do deklaracji lub zmień nazwę właściwości został zadeklarowany.  
  
## <a name="see-also"></a>Zobacz także
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
