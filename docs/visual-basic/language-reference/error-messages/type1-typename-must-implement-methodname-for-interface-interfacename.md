---
title: "&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; methodname&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e803ec7d0054f2fa1b9ed2a731fd30c9c3060468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; methodname&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;
Klasy lub struktury oświadczeń do zaimplementowania interfejsu, ale nie implementuje określonymi przez interfejs. Każdy element członkowski interfejsu musi być implementowana.  
  
 **Identyfikator błędu:** BC30149  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklaruje procedurę o tej samej nazwie i podpisie zgodnie z definicją w interfejsie. Należy uwzględnić co najmniej `End Function` lub `End Sub` instrukcji.  
  
2.  Dodaj `Implements` klauzuli na końcu `Function` lub `Sub` instrukcji. Na przykład:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
