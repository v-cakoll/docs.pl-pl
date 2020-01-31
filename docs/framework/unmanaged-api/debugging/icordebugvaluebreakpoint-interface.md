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
ms.openlocfilehash: e1bb5a6fd0550f7c25d46fa31ca11a10cec54986
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791074"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="566f4-102">ICorDebugValueBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="566f4-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="566f4-103">Rozszerza interfejs ICorDebugBreakpoint w celu zapewnienia dostępu do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="566f4-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="566f4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="566f4-104">Methods</span></span>  
  
|<span data-ttu-id="566f4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="566f4-105">Method</span></span>|<span data-ttu-id="566f4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="566f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="566f4-107">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="566f4-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="566f4-108">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wartość obiektu, na którym jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="566f4-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="566f4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="566f4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="566f4-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="566f4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="566f4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="566f4-111">Requirements</span></span>  
 <span data-ttu-id="566f4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="566f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="566f4-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="566f4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="566f4-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="566f4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="566f4-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="566f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566f4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="566f4-116">See also</span></span>

- [<span data-ttu-id="566f4-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="566f4-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
