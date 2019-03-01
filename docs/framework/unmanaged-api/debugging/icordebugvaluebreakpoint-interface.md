---
title: ICorDebugValueBreakpoint — Interfejs
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
ms.openlocfilehash: e4c291c12de9cb95416e12e1a5fca273c542df36
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966370"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="7a881-102">ICorDebugValueBreakpoint — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7a881-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="7a881-103">Rozszerza icordebugbreakpoint — interfejs w celu zapewnienia dostępu do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="7a881-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a881-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7a881-104">Methods</span></span>  
  
|<span data-ttu-id="7a881-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7a881-105">Method</span></span>|<span data-ttu-id="7a881-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7a881-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a881-107">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="7a881-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="7a881-108">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wartość obiektu, na którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="7a881-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a881-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a881-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a881-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="7a881-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a881-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a881-111">Requirements</span></span>  
 <span data-ttu-id="7a881-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a881-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a881-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a881-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a881-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a881-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a881-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a881-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a881-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a881-116">See also</span></span>
- [<span data-ttu-id="7a881-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7a881-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
