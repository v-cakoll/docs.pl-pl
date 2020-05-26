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
ms.openlocfilehash: 878dba37728734a777d2f95226b60bfbe9aae16a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805272"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="f3b6e-102">IDebuggerThreadControl::StartBlockingForDebugger — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3b6e-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="f3b6e-103">Powiadamia hosta o konieczności rozpoczęcia blokowania wszystkich wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="f3b6e-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3b6e-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3b6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3b6e-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="f3b6e-106">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="f3b6e-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3b6e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3b6e-107">Remarks</span></span>  
 <span data-ttu-id="f3b6e-108">`StartBlockingForDebugger`Metodę można wywołać w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f3b6e-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3b6e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3b6e-109">Requirements</span></span>  
 <span data-ttu-id="f3b6e-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3b6e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3b6e-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3b6e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3b6e-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3b6e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3b6e-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3b6e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b6e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3b6e-114">See also</span></span>

- [<span data-ttu-id="f3b6e-115">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3b6e-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
