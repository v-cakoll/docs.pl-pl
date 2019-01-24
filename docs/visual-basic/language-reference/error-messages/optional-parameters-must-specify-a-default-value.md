---
title: Parametry opcjonalne muszą określać wartość domyślną
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: dbbcc748a65942e3a89785b267e9231f4a4a01a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686182"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="b3521-102">Parametry opcjonalne muszą określać wartość domyślną</span><span class="sxs-lookup"><span data-stu-id="b3521-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="b3521-103">Następujące parametry opcjonalne, należy podać wartości domyślne, których można użyć, jeśli parametr nie jest dostarczana przez wywołanie procedury.</span><span class="sxs-lookup"><span data-stu-id="b3521-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="b3521-104">**Identyfikator błędu:** BC30812</span><span class="sxs-lookup"><span data-stu-id="b3521-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3521-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b3521-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b3521-106">Określanie wartości domyślnych dla parametrów opcjonalnych; na przykład:</span><span class="sxs-lookup"><span data-stu-id="b3521-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b3521-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3521-107">See also</span></span>
- [<span data-ttu-id="b3521-108">Optional</span><span class="sxs-lookup"><span data-stu-id="b3521-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
