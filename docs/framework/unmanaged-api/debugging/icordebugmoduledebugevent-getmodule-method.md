---
title: "ICorDebugModuleDebugEvent::GetModule — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b11ab8991a9f44cf2868474a8a0f6dcc1c3308c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="c3d8b-102">ICorDebugModuleDebugEvent::GetModule — metoda</span><span class="sxs-lookup"><span data-stu-id="c3d8b-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="c3d8b-103">Pobiera moduł scalone, który został właśnie załadowany lub usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="c3d8b-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3d8b-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3d8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3d8b-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="c3d8b-106">[out] Wskaźnik do adresu ICorDebugModule obiekt, który reprezentuje scalonych moduł, który właśnie został załadowany lub zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="c3d8b-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3d8b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3d8b-107">Remarks</span></span>  
 <span data-ttu-id="c3d8b-108">Możesz wywołać [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodę, aby ustalić, czy moduł został załadowany lub zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="c3d8b-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3d8b-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3d8b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d8b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3d8b-110">Requirements</span></span>  
 <span data-ttu-id="c3d8b-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d8b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d8b-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3d8b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3d8b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3d8b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3d8b-114">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d8b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d8b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3d8b-115">See Also</span></span>  
 [<span data-ttu-id="c3d8b-116">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3d8b-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="c3d8b-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3d8b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
