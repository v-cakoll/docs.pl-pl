---
title: "&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; membername&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords: BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05e0229d0259c519d4db265c017a5040b425c79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; membername&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;
"\<typename >' musi implementować"\<membername > "dla interfejsu"\<interfacename > ". Właściwość implementowania musi mieć pasujące "ReadOnly" / specyfikatory "WriteOnly".  
  
 Klasy lub struktury oświadczeń do zaimplementowania interfejsu, ale nie implementuje procedury, właściwości lub zdarzeń zdefiniowanych przez interfejs. Każdy element członkowski interfejsu musi być implementowana.  
  
 **Identyfikator błędu:** BC30154  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklaruje elementu członkowskiego o tej samej nazwie i podpisie zgodnie z definicją w interfejsie. Należy uwzględnić co najmniej `End Function`, `End Sub`, lub `End Property` instrukcji.  
  
2.  Dodaj `Implements` klauzuli na końcu `Function`, `Sub`, `Property`, lub `Event` instrukcji. Na przykład:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Podczas implementowania właściwości, upewnij się, że `ReadOnly` lub `WriteOnly` jest używana w taki sam sposób jak w definicji interfejsu.  
  
4.  Podczas implementowania właściwość, należy zadeklarować `Get` i `Set` procedur, zależnie od potrzeb.  
  
## <a name="see-also"></a>Zobacz też  
 [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
