---
title: Metoda ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 3927e57883ebe282b262cb03ececc3b2cd96fd46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123413"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="bc9aa-102">Metoda ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="bc9aa-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="bc9aa-103">Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) o tym, że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="bc9aa-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc9aa-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc9aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc9aa-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="bc9aa-106">podczas Składowa wyliczenia [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="bc9aa-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc9aa-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc9aa-107">Remarks</span></span>  
 <span data-ttu-id="bc9aa-108">Debuger wywołuje tę metodę, aby powiadomić [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="bc9aa-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc9aa-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bc9aa-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc9aa-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc9aa-110">Requirements</span></span>  
 <span data-ttu-id="bc9aa-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc9aa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc9aa-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc9aa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc9aa-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc9aa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc9aa-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc9aa-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9aa-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc9aa-115">See also</span></span>

- [<span data-ttu-id="bc9aa-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc9aa-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="bc9aa-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc9aa-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
