---
title: ICorDebugController::Terminate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee1c30809567097e67b6b1e40f5534429d748abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964370"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="e5c78-102">ICorDebugController::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5c78-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="e5c78-103">Kończy proces z określonym kodem zakończenia.</span><span class="sxs-lookup"><span data-stu-id="e5c78-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5c78-104">Ta metoda jest otoką dla funkcji Win32 `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="e5c78-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="e5c78-105">W tym `Terminate` celu program używa kodu zakończenia w taki sam sposób, w `TerminateProcess` jaki używa go funkcja Win32.</span><span class="sxs-lookup"><span data-stu-id="e5c78-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c78-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5c78-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5c78-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5c78-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="e5c78-108">podczas Wartość liczbowa, która jest kodem zakończenia.</span><span class="sxs-lookup"><span data-stu-id="e5c78-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="e5c78-109">Prawidłowe wartości liczbowe są zdefiniowane w Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="e5c78-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5c78-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5c78-110">Remarks</span></span>  
 <span data-ttu-id="e5c78-111">Jeśli proces zostanie zatrzymany po `Terminate` wywołaniu, proces powinien być kontynuowany przy użyciu metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby debuger otrzymał potwierdzenie zakończenia za pośrednictwem [ICorDebugManagedCallback:: ExitProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) lub [ICorDebugManagedCallback:: ExitAppDomain —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) , wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="e5c78-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5c78-112">Ta metoda nie jest implementowana przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5c78-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="e5c78-113">Oznacza to, że nie jest zaimplementowana <xref:System.AppDomain> na poziomie.</span><span class="sxs-lookup"><span data-stu-id="e5c78-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5c78-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5c78-114">Requirements</span></span>  
 <span data-ttu-id="e5c78-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c78-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c78-116">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5c78-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5c78-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5c78-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5c78-118">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5c78-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c78-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5c78-119">See also</span></span>
