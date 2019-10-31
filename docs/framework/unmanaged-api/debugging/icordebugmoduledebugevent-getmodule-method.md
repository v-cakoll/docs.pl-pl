---
title: 'ICorDebugModuleDebugEvent:: GetModule — Metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 5dc26d0367d01bc8da957c3ce648c3e529dddb08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096939"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="09a39-102">ICorDebugModuleDebugEvent:: GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="09a39-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="09a39-103">Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="09a39-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09a39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09a39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09a39-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="09a39-106">określoną Wskaźnik do adresu obiektu ICorDebugModule, który reprezentuje scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="09a39-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09a39-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09a39-107">Remarks</span></span>  
 <span data-ttu-id="09a39-108">Można wywołać metodę [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) , aby określić, czy moduł został załadowany, czy zwolniony.</span><span class="sxs-lookup"><span data-stu-id="09a39-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09a39-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="09a39-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a39-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09a39-110">Requirements</span></span>  
 <span data-ttu-id="09a39-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09a39-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a39-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09a39-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09a39-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09a39-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09a39-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a39-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a39-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09a39-115">See also</span></span>

- [<span data-ttu-id="09a39-116">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="09a39-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="09a39-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="09a39-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
