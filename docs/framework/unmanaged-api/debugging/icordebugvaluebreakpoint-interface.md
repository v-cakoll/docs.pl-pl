---
title: ICorDebugValueBreakpoint, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 778359a7d26b6e2f19984a1f7ff06a527f2449f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167749"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="fd23b-102">ICorDebugValueBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd23b-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="fd23b-103">Rozszerza icordebugbreakpoint — interfejs w celu zapewnienia dostępu do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="fd23b-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd23b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fd23b-104">Methods</span></span>  
  
|<span data-ttu-id="fd23b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd23b-105">Method</span></span>|<span data-ttu-id="fd23b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fd23b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd23b-107">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="fd23b-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="fd23b-108">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wartość obiektu, na którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="fd23b-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd23b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd23b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd23b-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="fd23b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd23b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd23b-111">Requirements</span></span>  
 <span data-ttu-id="fd23b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd23b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd23b-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd23b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd23b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd23b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd23b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd23b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd23b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd23b-116">See also</span></span>

- [<span data-ttu-id="fd23b-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fd23b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
