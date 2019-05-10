---
title: Parametry opcjonalne muszą określać wartość domyślną
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 0f501b518d5b3f2d48ced33885da2afd353c609e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665672"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>Parametry opcjonalne muszą określać wartość domyślną
Następujące parametry opcjonalne, należy podać wartości domyślne, których można użyć, jeśli parametr nie jest dostarczana przez wywołanie procedury.  
  
 **Identyfikator błędu:** BC30812  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Określanie wartości domyślnych dla parametrów opcjonalnych; na przykład:  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
