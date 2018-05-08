---
title: '&#39;&lt;Właściwość TypeName&gt; &#39; jest typem delegowanym'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39;&lt;Właściwość TypeName&gt; &#39; jest typem delegowanym
"\<typename >" jest typem delegowanym. Delegat konstrukcji zezwala na tylko jedno wyrażenie AddressOf jako listy argumentów. Wyrażenia AddressOf można często zamiast konstrukcji obiektu delegowanego.  
  
 A `New` klauzuli tworzenia wystąpienia klasy delegata dostarcza listy nieprawidłowy argument do konstruktora delegata.  
  
 Można podać tylko jeden `AddressOf` wyrażenie podczas tworzenia nowego wystąpienia obiektu delegowanego.  
  
 Ten błąd może spowodować żadnych argumentów nie jest przekazywany do konstruktora delegata, jeśli przekazać więcej niż jeden argument lub w przypadku przekazania pojedynczy argument który nie jest prawidłową `AddressOf` wyrażenia.  
  
 **Identyfikator błędu:** BC32008  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj pojedynczego `AddressOf` wyrażenia argumentu na liście w klasie obiektów delegowanych `New` klauzuli.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator New](../../../visual-basic/language-reference/operators/new-operator.md)  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Instrukcje: wywoływanie metody delegata](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
