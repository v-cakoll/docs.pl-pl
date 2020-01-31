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
ms.openlocfilehash: df3ad3fa4ef4eeee7e23ca1629da7a8b8ce09711
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792923"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="38ef1-102">ICorDebugModuleBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="38ef1-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="38ef1-103">Zapewnia dostęp do określonych modułów.</span><span class="sxs-lookup"><span data-stu-id="38ef1-103">Provides access to specific modules.</span></span> <span data-ttu-id="38ef1-104">Ten interfejs jest podklasą interfejsu ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="38ef1-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38ef1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="38ef1-105">Methods</span></span>  
  
|<span data-ttu-id="38ef1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="38ef1-106">Method</span></span>|<span data-ttu-id="38ef1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="38ef1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38ef1-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="38ef1-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="38ef1-109">Pobiera wskaźnik interfejsu do ICorDebugModule, który odwołuje się do modułu, w którym ustawiony jest ten punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="38ef1-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38ef1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38ef1-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38ef1-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="38ef1-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38ef1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38ef1-112">Requirements</span></span>  
 <span data-ttu-id="38ef1-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38ef1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38ef1-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38ef1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38ef1-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38ef1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38ef1-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38ef1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ef1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38ef1-117">See also</span></span>

- [<span data-ttu-id="38ef1-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="38ef1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
