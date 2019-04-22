---
title: Element <membername> niezgodny ze specyfikacją CLS jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: dbffe2bd196e798b90104aebb74269387660c794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840461"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>Non zgodne ze specyfikacją CLS \<membername > jest niedozwolone w interfejsie zgodnym ze specyfikacją CLS
Właściwość, procedura lub zdarzenie w interfejsie jest oznaczony jako `<CLSCompliant(True)>` po interfejsie, sama jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczona.  
  
 Dla interfejsu zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), wszystkich jej członków muszą być zgodne.  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności. Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40033  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Wymagaj zgodności ze specyfikacją CLS i mają kontrolę nad interfejsu kodu źródłowego, oznaczyć interfejsu `<CLSCompliant(True)>` Jeśli wszystkie jej składowe są zgodne.  
  
-   Jeśli wymagają zgodności ze specyfikacją CLS i nie mają kontrolę nad interfejsu kodu źródłowego lub nie kwalifikuje się jako zgodne, należy zdefiniować tego elementu członkowskiego, w ramach innego interfejsu.  
  
-   Jeśli wymagana jest pozostawienie tego elementu członkowskiego w interfejsie bieżącej, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub oznaczyć go jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
