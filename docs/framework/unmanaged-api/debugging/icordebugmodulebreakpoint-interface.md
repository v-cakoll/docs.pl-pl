---
title: ICorDebugModuleBreakpoint, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6a43a264fcaa94ce4e629d8db504e9d416f6b89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179715"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="138b7-102">ICorDebugModuleBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="138b7-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="138b7-103">Zapewnia dostęp do specyficznych modułów.</span><span class="sxs-lookup"><span data-stu-id="138b7-103">Provides access to specific modules.</span></span> <span data-ttu-id="138b7-104">Ten interfejs jest podklasą icordebugbreakpoint — interfejs.</span><span class="sxs-lookup"><span data-stu-id="138b7-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="138b7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="138b7-105">Methods</span></span>  
  
|<span data-ttu-id="138b7-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="138b7-106">Method</span></span>|<span data-ttu-id="138b7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="138b7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="138b7-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="138b7-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="138b7-109">Pobiera wskaźnik interfejsu do ICorDebugModule, który odwołuje się moduł, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="138b7-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="138b7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="138b7-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="138b7-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="138b7-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="138b7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="138b7-112">Requirements</span></span>  
 <span data-ttu-id="138b7-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="138b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="138b7-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="138b7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="138b7-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="138b7-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="138b7-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="138b7-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="138b7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="138b7-117">See also</span></span>

- [<span data-ttu-id="138b7-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="138b7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
