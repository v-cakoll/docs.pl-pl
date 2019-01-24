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
ms.openlocfilehash: 75dc379baf8d92b9b27bdb58ccab930c2d4f91e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709172"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="e9d59-102">ICorDebugProcess3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e9d59-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="e9d59-103">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="e9d59-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9d59-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e9d59-104">Methods</span></span>  
  
|<span data-ttu-id="e9d59-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e9d59-105">Method</span></span>|<span data-ttu-id="e9d59-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e9d59-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9d59-107">SetEnableCustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="e9d59-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="e9d59-108">Włącza i wyłącza niestandardowymi powiadomieniami debugera określonego typu.</span><span class="sxs-lookup"><span data-stu-id="e9d59-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9d59-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9d59-109">Remarks</span></span>  
 <span data-ttu-id="e9d59-110">Ten interfejs rozszerza logicznie ICorDebugProcess i ICorDebugProcess2 interfejsów.</span><span class="sxs-lookup"><span data-stu-id="e9d59-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9d59-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="e9d59-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9d59-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9d59-112">Requirements</span></span>  
 <span data-ttu-id="e9d59-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9d59-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9d59-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9d59-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9d59-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9d59-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9d59-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9d59-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d59-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9d59-117">See also</span></span>
- [<span data-ttu-id="e9d59-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e9d59-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e9d59-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e9d59-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
