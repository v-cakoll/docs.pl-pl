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
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="0647b-102">Parametry opcjonalne muszą określać wartość domyślną</span><span class="sxs-lookup"><span data-stu-id="0647b-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="0647b-103">Parametry opcjonalne podać wartości domyślne, które mogą być używane, jeśli parametr nie zostanie podany przez wywołanie procedury.</span><span class="sxs-lookup"><span data-stu-id="0647b-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="0647b-104">**Identyfikator błędu:** BC30812</span><span class="sxs-lookup"><span data-stu-id="0647b-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0647b-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0647b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="0647b-106">Określ wartości domyślne dla parametrów opcjonalnych; na przykład:</span><span class="sxs-lookup"><span data-stu-id="0647b-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0647b-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0647b-107">See Also</span></span>  
 [<span data-ttu-id="0647b-108">Optional</span><span class="sxs-lookup"><span data-stu-id="0647b-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
