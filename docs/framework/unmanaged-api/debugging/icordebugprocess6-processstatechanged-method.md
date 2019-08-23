---
title: Metoda ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb158b383745cd7e44c8fede6ddd43ae81ced2d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930763"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="16c51-102">Metoda ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="16c51-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="16c51-103">Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) o tym, że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="16c51-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16c51-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16c51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16c51-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="16c51-106">podczas Składowa wyliczenia [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="16c51-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16c51-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16c51-107">Remarks</span></span>  
 <span data-ttu-id="16c51-108">Debuger wywołuje tę metodę, aby powiadomić [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="16c51-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16c51-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16c51-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c51-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16c51-110">Requirements</span></span>  
 <span data-ttu-id="16c51-111">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c51-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c51-112">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16c51-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16c51-113">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16c51-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c51-114">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c51-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c51-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16c51-115">See also</span></span>

- [<span data-ttu-id="16c51-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="16c51-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="16c51-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="16c51-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
