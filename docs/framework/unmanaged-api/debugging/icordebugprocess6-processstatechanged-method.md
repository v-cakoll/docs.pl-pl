---
title: Metoda ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4dcee3b396d9533f3169db1ea54a6cdc6086c8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166149"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="87386-102">Metoda ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="87386-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="87386-103">Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="87386-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87386-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87386-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87386-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87386-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="87386-106">[in] Członek [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) wyliczenia</span><span class="sxs-lookup"><span data-stu-id="87386-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87386-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87386-107">Remarks</span></span>  
 <span data-ttu-id="87386-108">Debuger wywołuje tę metodę, aby powiadomić [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="87386-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87386-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="87386-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87386-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87386-110">Requirements</span></span>  
 <span data-ttu-id="87386-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87386-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87386-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87386-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87386-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87386-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87386-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87386-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87386-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87386-115">See also</span></span>

- [<span data-ttu-id="87386-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="87386-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="87386-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="87386-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
