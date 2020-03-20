---
title: VerifyClientKey, funkcja (odwołanie do interfejsu API niezarządzanego)
description: VerifyClientKey Funkcja zapewnia klucz klienta ma poprawne zabezpieczenia.
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
ms.openlocfilehash: ebb794240494deb0c831b50e95461ec52017a215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176711"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="b9ad5-103">VerifyClientKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="b9ad5-103">VerifyClientKey function</span></span>
<span data-ttu-id="b9ad5-104">Zapewnia, że klucz klienta ma odpowiednie zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="b9ad5-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b9ad5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9ad5-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="b9ad5-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9ad5-106">Return value</span></span>

<span data-ttu-id="b9ad5-107">Jeśli funkcja powiedzie się, `ERROR_SUCCESS` zwracana wartość wynosi (0).</span><span class="sxs-lookup"><span data-stu-id="b9ad5-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="b9ad5-108">Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w *pliku WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="b9ad5-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9ad5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9ad5-109">Requirements</span></span>  
 <span data-ttu-id="b9ad5-110">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ad5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ad5-111">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="b9ad5-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b9ad5-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b9ad5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ad5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9ad5-113">See also</span></span>

- [<span data-ttu-id="b9ad5-114">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="b9ad5-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
