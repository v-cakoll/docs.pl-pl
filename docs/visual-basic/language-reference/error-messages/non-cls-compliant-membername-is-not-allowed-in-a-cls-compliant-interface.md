---
title: "Zgodne z non-CLS &lt;membername&gt; jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74744b89ad72b6fd051f83ba38354d0a277555c8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>Zgodne z non-CLS &lt;membername&gt; jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS
Właściwość, procedura lub zdarzenie w interfejsie jest oznaczony jako `<CLSCompliant(True)>` gdy sam interfejs jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczony jako.  
  
 Dla interfejsu było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), wszystkie jego elementy członkowskie muszą być zgodne.  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności. Nie jest domyślnie dla tego parametru, a należy podać wartość.  
  
 Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40033  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Wymagaj zgodności ze specyfikacją CLS, kontrolę kodu źródłowego interfejsu oznaczyć interfejsu `<CLSCompliant(True)>` Jeśli wszyscy jej członkowie będą zgodne.  
  
-   Jeśli wymagają zgodności ze specyfikacją CLS i nie mają kontrolę nad interfejsu kodu źródłowego lub nie kwalifikuje się do zapewnienia zgodności, zdefiniuj tego elementu członkowskiego w ramach innego interfejsu.  
  
-   Jeśli potrzebna jest pozostawienie tego elementu członkowskiego w interfejsie bieżącej, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
