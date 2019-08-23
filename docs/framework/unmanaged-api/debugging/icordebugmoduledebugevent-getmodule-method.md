---
title: 'ICorDebugModuleDebugEvent:: GetModule — Metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e68fab11a881854ae4c3fe073f73150694d31ae5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965110"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="99465-102">ICorDebugModuleDebugEvent:: GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="99465-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="99465-103">Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="99465-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99465-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99465-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99465-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="99465-106">określoną Wskaźnik do adresu obiektu ICorDebugModule, który reprezentuje scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="99465-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99465-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99465-107">Remarks</span></span>  
 <span data-ttu-id="99465-108">Można wywołać metodę [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) , aby określić, czy moduł został załadowany, czy zwolniony.</span><span class="sxs-lookup"><span data-stu-id="99465-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99465-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99465-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99465-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99465-110">Requirements</span></span>  
 <span data-ttu-id="99465-111">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99465-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99465-112">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99465-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99465-113">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99465-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99465-114">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99465-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99465-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99465-115">See also</span></span>

- [<span data-ttu-id="99465-116">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="99465-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="99465-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="99465-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
