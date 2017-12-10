---
title: "&#39; &lt;classname&gt;&#39; nie jest zgodne ze specyfikacją CLS, ponieważ interfejs &#39;&lt; InterfaceName&gt;&#39; implementuje nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60c41332d3a5d93b05df906eefdeeb0d1b67e638
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>&#39; &lt;classname&gt;&#39; nie jest zgodne ze specyfikacją CLS, ponieważ interfejs &#39;&lt; InterfaceName&gt;&#39; implementuje nie jest zgodne ze specyfikacją CLS
Klasy lub interfejsu jest oznaczony jako `<CLSCompliant(True)>` po pochodną lub implementuje typu, który jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczony jako.  
  
 Dla klasy lub interfejsu, aby było zgodne z [niezależność od języka i elementy niezależne od języka](../../../../docs/standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), jej hierarchii dziedziczenia całego muszą być zgodne. Oznacza to, że każdy typ, po którym dziedziczy, bezpośrednio lub pośrednio, muszą być zgodne. Podobnie jeśli klasa implementuje jeden lub więcej interfejsów, ich wszystkie muszą być zgodne w całym ich hierarchii dziedziczenia.  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności. Nie jest domyślnie dla tego parametru, a należy podać wartość.  
  
 Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40029  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli potrzebujesz zgodności ze specyfikacją CLS, należy zdefiniować tego typu w ramach systemu hierarchii lub wykonania innego dziedziczenia.  
  
-   Jeśli wymagasz, że ten typ pozostają w jego bieżącej hierarchii lub implementacji schemat dziedziczenia, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
