---
title: Parametry opcjonalne muszą określać wartość domyślną
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 8ec4627d070cc670ce04be3a5d0298dba0a279d0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582130"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="91781-102">Parametry opcjonalne muszą określać wartość domyślną</span><span class="sxs-lookup"><span data-stu-id="91781-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="91781-103">Parametry opcjonalne muszą podawać wartości domyślne, których można użyć, jeśli żaden parametr nie jest dostarczany przez procedurę wywołującą.</span><span class="sxs-lookup"><span data-stu-id="91781-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="91781-104">**Identyfikator błędu:** BC30812</span><span class="sxs-lookup"><span data-stu-id="91781-104">**Error ID:** BC30812</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="91781-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="91781-105">To correct this error</span></span>

<span data-ttu-id="91781-106">Określ wartości domyślne dla parametrów opcjonalnych; na przykład:</span><span class="sxs-lookup"><span data-stu-id="91781-106">Specify default values for optional parameters; for example:</span></span>

```vb
Sub Proc1(ByVal X As Integer,
      Optional ByVal Y As String = "Default Value")
    MsgBox("Default argument is: " & Y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="91781-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91781-107">See also</span></span>

- [<span data-ttu-id="91781-108">Optional</span><span class="sxs-lookup"><span data-stu-id="91781-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
