---
title: ICorDebugProcess3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05900f55885f8f3a4c470d6842c42d0fc3e0171e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957456"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="6c519-102">ICorDebugProcess3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6c519-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="6c519-103">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="6c519-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c519-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6c519-104">Methods</span></span>  
  
|<span data-ttu-id="6c519-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6c519-105">Method</span></span>|<span data-ttu-id="6c519-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6c519-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c519-107">SetEnableCustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="6c519-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="6c519-108">Włącza i wyłącza niestandardowe powiadomienia debugera określonego typu.</span><span class="sxs-lookup"><span data-stu-id="6c519-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c519-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c519-109">Remarks</span></span>  
 <span data-ttu-id="6c519-110">Ten interfejs logicznie rozszerza interfejsy ICorDebugProcess i ICorDebugProcess2.</span><span class="sxs-lookup"><span data-stu-id="6c519-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c519-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6c519-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c519-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c519-112">Requirements</span></span>  
 <span data-ttu-id="6c519-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c519-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c519-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c519-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c519-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c519-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c519-116">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c519-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c519-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c519-117">See also</span></span>

- [<span data-ttu-id="6c519-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6c519-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6c519-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6c519-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
