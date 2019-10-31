---
title: ICorDebugModuleBreakpoint — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: 2bc5c21d2e1256d0e79390bea10aafcdefbed0d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110334"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="2ab8b-102">ICorDebugModuleBreakpoint — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2ab8b-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="2ab8b-103">Zapewnia dostęp do określonych modułów.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-103">Provides access to specific modules.</span></span> <span data-ttu-id="2ab8b-104">Ten interfejs jest podklasą interfejsu ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ab8b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2ab8b-105">Methods</span></span>  
  
|<span data-ttu-id="2ab8b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2ab8b-106">Method</span></span>|<span data-ttu-id="2ab8b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2ab8b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ab8b-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="2ab8b-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="2ab8b-109">Pobiera wskaźnik interfejsu do ICorDebugModule, który odwołuje się do modułu, w którym ustawiony jest ten punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ab8b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ab8b-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ab8b-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ab8b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ab8b-112">Requirements</span></span>  
 <span data-ttu-id="2ab8b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ab8b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ab8b-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2ab8b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ab8b-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2ab8b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ab8b-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ab8b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab8b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ab8b-117">See also</span></span>

- [<span data-ttu-id="2ab8b-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2ab8b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
