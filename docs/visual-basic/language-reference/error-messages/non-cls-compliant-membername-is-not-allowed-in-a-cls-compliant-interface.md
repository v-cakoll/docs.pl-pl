---
title: Element <membername> niezgodny ze specyfikacją CLS jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409403"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>Element \<membername> niezgodny ze specyfikacją CLS jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS
Właściwość, procedura lub zdarzenie w interfejsie jest oznaczone jako, `<CLSCompliant(True)>` gdy sam interfejs jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczony.  
  
 Aby interfejs był zgodny z [niezależnymi od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), wszystkie jego elementy członkowskie muszą być zgodne.  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, należy ustawić `isCompliant` parametr atrybutu na wartość `True` lub `False` w celu wskazania zgodności lub niezgodności. Dla tego parametru nie ma wartości domyślnej i należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> do elementu, jest on uznawany za niezgodny.  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40033  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli wymagasz zgodności ze specyfikacją CLS i masz kontrolę nad kodem źródłowym interfejsu, Oznacz interfejs tak, jakby `<CLSCompliant(True)>` wszystkie jego elementy członkowskie były zgodne.  
  
- Jeśli jest wymagana zgodność ze specyfikacją CLS i nie ma kontroli nad kodem źródłowym interfejsu lub jeśli nie kwalifikuje się do zgodności, zdefiniuj tego elementu członkowskiego w innym interfejsie.  
  
- Jeśli potrzebujesz, aby ten element członkowski pozostawał w bieżącym interfejsie, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>` .  
  
## <a name="see-also"></a>Zobacz też

- [Interface, instrukcja](../statements/interface-statement.md)
