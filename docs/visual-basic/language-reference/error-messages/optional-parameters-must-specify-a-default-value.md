---
title: Parametry opcjonalne muszą określać wartość domyślną
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: b32c150f0faf4a9dcec3cec7620c3a9c050f6f20
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696885"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="9c1d9-102">Parametry opcjonalne muszą określać wartość domyślną</span><span class="sxs-lookup"><span data-stu-id="9c1d9-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="9c1d9-103">Parametry opcjonalne muszą podawać wartości domyślne, których można użyć, jeśli żaden parametr nie jest dostarczany przez procedurę wywołującą.</span><span class="sxs-lookup"><span data-stu-id="9c1d9-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="9c1d9-104">**Identyfikator błędu:** BC30812</span><span class="sxs-lookup"><span data-stu-id="9c1d9-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c1d9-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9c1d9-105">To correct this error</span></span>  
  
- <span data-ttu-id="9c1d9-106">Określ wartości domyślne dla parametrów opcjonalnych; na przykład:</span><span class="sxs-lookup"><span data-stu-id="9c1d9-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```vb  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9c1d9-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c1d9-107">See also</span></span>

- [<span data-ttu-id="9c1d9-108">Optional</span><span class="sxs-lookup"><span data-stu-id="9c1d9-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
