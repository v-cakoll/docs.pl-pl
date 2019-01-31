---
title: Element „<classname>” jest niezgodny ze specyfikacją CLS, ponieważ interfejs „<interfacename>”, który implementuje, jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 6743a0decebb9711a4e44d09b03fe32f88ff2f72
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283481"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>"\<nazwa_klasy >' nie jest zgodny ze specyfikacją CLS, ponieważ interfejs"\<interfacename > "go implementuje, jest niezgodny ze specyfikacją CLS
Klasy lub interfejsu, jest oznaczana `<CLSCompliant(True)>` po pochodzi od klasy lub typu, który jest oznaczony jako implementuje `<CLSCompliant(False)>` lub nie jest oznaczona.  
  
 Dla klasy lub interfejsu, aby zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej hierarchii dziedziczenia całego muszą być zgodne. Oznacza to, że każdy typ, po którym dziedziczy, bezpośrednio lub pośrednio, muszą być zgodne. Podobnie jeśli klasa implementuje jeden lub więcej interfejsów, ich wszystkie muszą być zgodne w całej swojej hierarchii dziedziczenia.  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności. Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40029  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli wymagana jest zgodność ze specyfikacją CLS, należy zdefiniować tego typu w ramach różnych dziedziczenia hierarchii lub implementacji systemu.  
  
-   Jeśli potrzebujesz, że tego typu pozostaną w jego bieżącej hierarchii lub implementacji schemat dziedziczenia, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub oznaczyć go jako `<CLSCompliant(False)>`.  
  
 
