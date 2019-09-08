---
title: VerifyClientKey — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja VerifyClientKey gwarantuje, że klucz klienta ma poprawne zabezpieczenia.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b674e959ab93cf76b84e2af41e875a50b7d115f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798191"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="26bfa-103">VerifyClientKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="26bfa-103">VerifyClientKey function</span></span>
<span data-ttu-id="26bfa-104">Zapewnia, że klucz klienta ma poprawne zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="26bfa-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="26bfa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="26bfa-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="26bfa-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="26bfa-106">Return value</span></span>

<span data-ttu-id="26bfa-107">Jeśli funkcja się powiedzie, zwracaną wartością jest `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="26bfa-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="26bfa-108">Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero zdefiniowanym w *Winerror. h*.</span><span class="sxs-lookup"><span data-stu-id="26bfa-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="26bfa-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26bfa-109">Requirements</span></span>  
 <span data-ttu-id="26bfa-110">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26bfa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26bfa-111">**Nagłówki** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="26bfa-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="26bfa-112">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26bfa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bfa-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26bfa-113">See also</span></span>

- [<span data-ttu-id="26bfa-114">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="26bfa-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
