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
ms.openlocfilehash: 7026d135b02563b6c718be4096d2c5cad9d33cec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212285"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="54df7-102">ICorDebugModuleBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="54df7-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="54df7-103">Zapewnia dostęp do określonych modułów.</span><span class="sxs-lookup"><span data-stu-id="54df7-103">Provides access to specific modules.</span></span> <span data-ttu-id="54df7-104">Ten interfejs jest podklasą interfejsu ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="54df7-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54df7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="54df7-105">Methods</span></span>  
  
|<span data-ttu-id="54df7-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="54df7-106">Method</span></span>|<span data-ttu-id="54df7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="54df7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54df7-108">GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="54df7-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="54df7-109">Pobiera wskaźnik interfejsu do ICorDebugModule, który odwołuje się do modułu, w którym ustawiony jest ten punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="54df7-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54df7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54df7-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54df7-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="54df7-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54df7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54df7-112">Requirements</span></span>  
 <span data-ttu-id="54df7-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54df7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54df7-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54df7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54df7-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="54df7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54df7-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54df7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54df7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54df7-117">See also</span></span>

- [<span data-ttu-id="54df7-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="54df7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
