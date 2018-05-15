---
title: Metoda ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5861762242412d7ab6f0c02f2b8f5c149f9453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="889e4-102">Metoda ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="889e4-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="889e4-103">Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) którym jest uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="889e4-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="889e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="889e4-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="889e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="889e4-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="889e4-106">[in] Członek [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="889e4-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="889e4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="889e4-107">Remarks</span></span>  
 <span data-ttu-id="889e4-108">Debuger wywołuje tę metodę, aby powiadomić [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) którym jest uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="889e4-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="889e4-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="889e4-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="889e4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="889e4-110">Requirements</span></span>  
 <span data-ttu-id="889e4-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="889e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="889e4-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="889e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="889e4-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="889e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="889e4-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="889e4-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889e4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="889e4-115">See Also</span></span>  
 [<span data-ttu-id="889e4-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="889e4-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="889e4-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="889e4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
