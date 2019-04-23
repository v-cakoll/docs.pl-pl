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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179715"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="ca6eb-102">ICorDebugModuleBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca6eb-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="ca6eb-103">Zapewnia dostęp do specyficznych modułów.</span><span class="sxs-lookup"><span data-stu-id="ca6eb-103">Provides access to specific modules.</span></span> <span data-ttu-id="ca6eb-104">Ten interfejs jest podklasą icordebugbreakpoint — interfejs.</span><span class="sxs-lookup"><span data-stu-id="ca6eb-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca6eb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ca6eb-105">Methods</span></span>  
  
|<span data-ttu-id="ca6eb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca6eb-106">Method</span></span>|<span data-ttu-id="ca6eb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ca6eb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca6eb-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="ca6eb-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="ca6eb-109">Pobiera wskaźnik interfejsu do ICorDebugModule, który odwołuje się moduł, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="ca6eb-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca6eb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca6eb-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca6eb-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="ca6eb-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6eb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca6eb-112">Requirements</span></span>  
 <span data-ttu-id="ca6eb-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6eb-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca6eb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca6eb-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca6eb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca6eb-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6eb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca6eb-117">See also</span></span>

- [<span data-ttu-id="ca6eb-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ca6eb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
