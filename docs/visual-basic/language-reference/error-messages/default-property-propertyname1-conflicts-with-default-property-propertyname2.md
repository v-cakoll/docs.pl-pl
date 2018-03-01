---
title: "Domyślne właściwości &#39; &lt;propertyname1&gt;&#39; powoduje konflikt z właściwością domyślną &#39;&lt; NazwaWłaściwości2&gt;&#39; w &#39;&lt; ClassName&gt;&#39; i dlatego powinien być zadeklarowany jako &#39; Shadows &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Domyślne właściwości &#39; &lt;propertyname1&gt;&#39; powoduje konflikt z właściwością domyślną &#39;&lt; NazwaWłaściwości2&gt;&#39; w &#39;&lt; ClassName&gt;&#39; i dlatego powinien być zadeklarowany jako &#39; Shadows &#39;
Właściwość zadeklarowana z taką samą nazwę jak właściwość zdefiniowaną w klasie podstawowej. W takiej sytuacji właściwości tej klasy należy obserwować właściwości klasy podstawowej.  
  
 Ten komunikat jest ostrzeżenie. `Shadows`przyjęto, że domyślnie. Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40007  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj `Shadows` — słowo kluczowe do deklaracji lub zmień nazwę właściwości został zadeklarowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
