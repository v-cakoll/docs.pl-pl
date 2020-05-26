---
title: IGCThreadControl::SuspensionEnding — Metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 8300daf0d39745ceda80f6c56da7e3c459a97468
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805119"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="955af-102">IGCThreadControl::SuspensionEnding — Metoda</span><span class="sxs-lookup"><span data-stu-id="955af-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="955af-103">Powiadamia hosta, że środowisko uruchomieniowe wznawia wątki po wyrzucaniu elementów bezużytecznych lub innym zawieszeniu.</span><span class="sxs-lookup"><span data-stu-id="955af-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="955af-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="955af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="955af-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="955af-106">podczas Generacja, na której wykonano odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="955af-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="955af-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="955af-107">Remarks</span></span>  
 <span data-ttu-id="955af-108">Nie należy ponownie planować żadnych wątków w trakcie `SuspensionEnding` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="955af-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="955af-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="955af-109">Requirements</span></span>  
 <span data-ttu-id="955af-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="955af-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="955af-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="955af-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="955af-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="955af-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="955af-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="955af-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955af-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="955af-114">See also</span></span>

- [<span data-ttu-id="955af-115">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="955af-115">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
