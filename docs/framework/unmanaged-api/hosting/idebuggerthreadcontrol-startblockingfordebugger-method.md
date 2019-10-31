---
title: IDebuggerThreadControl::StartBlockingForDebugger — Metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
ms.openlocfilehash: 72f7bee79e74c69acff90861ceada8a91afe2157
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134917"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="24064-102">IDebuggerThreadControl::StartBlockingForDebugger — Metoda</span><span class="sxs-lookup"><span data-stu-id="24064-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="24064-103">Powiadamia hosta o konieczności rozpoczęcia blokowania wszystkich wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="24064-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24064-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24064-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24064-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24064-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="24064-106">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="24064-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24064-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24064-107">Remarks</span></span>  
 <span data-ttu-id="24064-108">Metodę `StartBlockingForDebugger` można wywołać w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="24064-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24064-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24064-109">Requirements</span></span>  
 <span data-ttu-id="24064-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24064-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24064-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="24064-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24064-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="24064-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24064-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24064-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24064-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24064-114">See also</span></span>

- [<span data-ttu-id="24064-115">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="24064-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
