---
title: Typ „<typename>” jest typem delegowanym
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c308805f5e73d740ff18a40d95b9cc2576ac95fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013598"
---
# <a name="typename-is-a-delegate-type"></a>"\<typename >" jest typem delegowanym
"\<typename >" jest typem delegowanym. Konstrukcja delegata zezwala na tylko pojedyncze wyrażenie AddressOf listy argumentów. Często można używać wyrażenia AddressOf zamiast tworzenia delegata.  
  
 A `New` klauzuli tworzenia wystąpienia klasy delegata dostarcza listę nieprawidłowy argument dla konstruktora delegata.  
  
 Można podać tylko jeden `AddressOf` wyrażenia, tworząc nowe wystąpienie delegata.  
  
 Ten błąd może spowodować, jeżeli nie przepuszczasz argumentów do konstruktora delegata przekazać więcej niż jeden argument, czy w przypadku przekazania jeden argument, nie jest prawidłowym `AddressOf` wyrażenia.  
  
 **Identyfikator błędu:** BC32008  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Używanie pojedynczej `AddressOf` wyrażenia na liście argumentów dla klasy delegata w `New` klauzuli.  
  
## <a name="see-also"></a>Zobacz także

- [New, operator](../../../visual-basic/language-reference/operators/new-operator.md)
- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegaty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrukcje: Wywoływanie metody delegata](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
