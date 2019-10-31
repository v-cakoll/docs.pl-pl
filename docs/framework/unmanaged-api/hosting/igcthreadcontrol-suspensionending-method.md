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
ms.openlocfilehash: 8d8efccde56d8d37a75b1d9bbec706411c6b1f45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134784"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="b424a-102">IGCThreadControl::SuspensionEnding — Metoda</span><span class="sxs-lookup"><span data-stu-id="b424a-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="b424a-103">Powiadamia hosta, że środowisko uruchomieniowe wznawia wątki po wyrzucaniu elementów bezużytecznych lub innym zawieszeniu.</span><span class="sxs-lookup"><span data-stu-id="b424a-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b424a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b424a-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b424a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b424a-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="b424a-106">podczas Generacja, na której wykonano odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="b424a-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b424a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b424a-107">Remarks</span></span>  
 <span data-ttu-id="b424a-108">Nie należy ponownie planować żadnych wątków w trakcie wywołania zwrotnego `SuspensionEnding`.</span><span class="sxs-lookup"><span data-stu-id="b424a-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b424a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b424a-109">Requirements</span></span>  
 <span data-ttu-id="b424a-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b424a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b424a-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b424a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b424a-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b424a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b424a-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b424a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b424a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b424a-114">See also</span></span>

- [<span data-ttu-id="b424a-115">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="b424a-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
