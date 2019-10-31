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
ms.openlocfilehash: fb8cfb2d1c5902ecd0d5858ef21ba48b65b12506
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125332"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="214a1-102">ICorDebugController::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="214a1-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="214a1-103">Kończy proces z określonym kodem zakończenia.</span><span class="sxs-lookup"><span data-stu-id="214a1-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="214a1-104">Ta metoda jest otoką dla funkcji Win32 `TerminateProcess`.</span><span class="sxs-lookup"><span data-stu-id="214a1-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="214a1-105">W tym celu `Terminate` używa kodu zakończenia w taki sam sposób, w jaki funkcja Win32 `TerminateProcess` używa tej metody.</span><span class="sxs-lookup"><span data-stu-id="214a1-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="214a1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="214a1-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="214a1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="214a1-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="214a1-108">podczas Wartość liczbowa, która jest kodem zakończenia.</span><span class="sxs-lookup"><span data-stu-id="214a1-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="214a1-109">Prawidłowe wartości liczbowe są zdefiniowane w Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="214a1-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="214a1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="214a1-110">Remarks</span></span>  
 <span data-ttu-id="214a1-111">Jeśli proces zostanie zatrzymany po wywołaniu `Terminate`, proces powinien być kontynuowany przy użyciu metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby debuger otrzymał potwierdzenie zakończenia za pośrednictwem [ICorDebugManagedCallback:: ExitProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) lub [ICorDebugManagedCallback:: ExitAppDomain —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) , wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="214a1-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="214a1-112">Ta metoda nie jest implementowana przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="214a1-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="214a1-113">Oznacza to, że nie jest zaimplementowany na poziomie <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="214a1-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="214a1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="214a1-114">Requirements</span></span>  
 <span data-ttu-id="214a1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="214a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="214a1-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="214a1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="214a1-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="214a1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="214a1-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="214a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="214a1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="214a1-119">See also</span></span>
