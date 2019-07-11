---
title: Metoda ICorDebugModuleDebugEvent::GetModule
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: debf2e9dd08f6a35801932b22fbd985e7299b79f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764349"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="05031-102">Metoda ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="05031-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="05031-103">Pobiera scalonych moduł, który został właśnie załadowany lub usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="05031-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05031-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05031-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05031-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05031-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="05031-106">[out] Wskaźnik na adres ICorDebugModule obiekt, który reprezentuje scalonych moduł, który właśnie został załadowany lub zwolnione.</span><span class="sxs-lookup"><span data-stu-id="05031-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05031-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05031-107">Remarks</span></span>  
 <span data-ttu-id="05031-108">Możesz wywołać [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodę, aby ustalić, czy moduł został załadowany lub zwolnione.</span><span class="sxs-lookup"><span data-stu-id="05031-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05031-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="05031-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05031-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05031-110">Requirements</span></span>  
 <span data-ttu-id="05031-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05031-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05031-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05031-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05031-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05031-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05031-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05031-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05031-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05031-115">See also</span></span>

- [<span data-ttu-id="05031-116">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="05031-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="05031-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="05031-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
