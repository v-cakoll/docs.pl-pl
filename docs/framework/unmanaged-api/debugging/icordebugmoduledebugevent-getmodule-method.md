---
title: 'ICorDebugModuleDebugEvent:: GetModule — Metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 1df71ddbf1ee76cc8202d8f9e263b9d95b4aaa09
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213364"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="e922a-102">ICorDebugModuleDebugEvent:: GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="e922a-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="e922a-103">Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="e922a-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e922a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e922a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e922a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e922a-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="e922a-106">określoną Wskaźnik do adresu obiektu ICorDebugModule, który reprezentuje scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="e922a-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e922a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e922a-107">Remarks</span></span>  
 <span data-ttu-id="e922a-108">Można wywołać metodę [GetEventKind](icordebugdebugevent-geteventkind-method.md) , aby określić, czy moduł został załadowany, czy zwolniony.</span><span class="sxs-lookup"><span data-stu-id="e922a-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e922a-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e922a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e922a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e922a-110">Requirements</span></span>  
 <span data-ttu-id="e922a-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e922a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e922a-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e922a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e922a-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e922a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e922a-114">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e922a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e922a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e922a-115">See also</span></span>

- [<span data-ttu-id="e922a-116">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e922a-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="e922a-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e922a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
