---
title: Parametry opcjonalne muszą określać wartość domyślną
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 6788a7908489591e266af6d141006f2aa2d0e6f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optional-parameters-must-specify-a-default-value"></a>Parametry opcjonalne muszą określać wartość domyślną
Parametry opcjonalne podać wartości domyślne, które mogą być używane, jeśli parametr nie zostanie podany przez wywołanie procedury.  
  
 **Identyfikator błędu:** BC30812  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Określ wartości domyślne dla parametrów opcjonalnych; na przykład:  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
