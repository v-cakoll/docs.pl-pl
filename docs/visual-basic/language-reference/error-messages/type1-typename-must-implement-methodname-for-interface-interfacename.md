---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; musi implementować &#39; &lt;methodname&gt; &#39; interfejsu &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: daeeab853f6a7f582542fa15ffc09ce749731d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39; musi implementować &#39; &lt;methodname&gt; &#39; interfejsu &#39; &lt;interfacename&gt;&#39;
Klasy lub struktury oświadczeń do zaimplementowania interfejsu, ale nie implementuje określonymi przez interfejs. Każdy element członkowski interfejsu musi być implementowana.  
  
 **Identyfikator błędu:** BC30149  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklaruje procedurę o tej samej nazwie i podpisie zgodnie z definicją w interfejsie. Należy uwzględnić co najmniej `End Function` lub `End Sub` instrukcji.  
  
2.  Dodaj `Implements` klauzuli na końcu `Function` lub `Sub` instrukcji. Na przykład:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
