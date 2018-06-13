---
title: ICorDebugModuleDebugEvent::GetModule — metoda
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56ce5b3f5fb3c6d2a00c407afc303895273c2251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419494"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="93ff8-102">ICorDebugModuleDebugEvent::GetModule — metoda</span><span class="sxs-lookup"><span data-stu-id="93ff8-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="93ff8-103">Pobiera moduł scalone, który został właśnie załadowany lub usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="93ff8-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ff8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93ff8-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93ff8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93ff8-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="93ff8-106">[out] Wskaźnik do adresu ICorDebugModule obiekt, który reprezentuje scalonych moduł, który właśnie został załadowany lub zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="93ff8-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93ff8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93ff8-107">Remarks</span></span>  
 <span data-ttu-id="93ff8-108">Możesz wywołać [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodę, aby ustalić, czy moduł został załadowany lub zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="93ff8-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93ff8-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="93ff8-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93ff8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93ff8-110">Requirements</span></span>  
 <span data-ttu-id="93ff8-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93ff8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93ff8-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93ff8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93ff8-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93ff8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93ff8-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93ff8-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ff8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93ff8-115">See Also</span></span>  
 [<span data-ttu-id="93ff8-116">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="93ff8-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="93ff8-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="93ff8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
