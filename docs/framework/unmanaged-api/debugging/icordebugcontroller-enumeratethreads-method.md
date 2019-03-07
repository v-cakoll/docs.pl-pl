---
title: ICorDebugController::EnumerateThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4bb4072c574edeac1c531978fac75595c252e0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481602"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="6b5d8-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b5d8-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="6b5d8-103">Pobiera moduł wyliczający dla aktywnego zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="6b5d8-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b5d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b5d8-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b5d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b5d8-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="6b5d8-106">[out] Wskaźnik na adres obiektu "icordebugthreadenum —", który reprezentuje moduł wyliczający wszystkie zarządzane wątki, które są aktywne w procesie.</span><span class="sxs-lookup"><span data-stu-id="6b5d8-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b5d8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b5d8-107">Remarks</span></span>  
 <span data-ttu-id="6b5d8-108">Wątek jest uważany za aktywny po [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) wywołanie zwrotne zostało wysłane i przed [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) wywołanie zwrotne zostało wysłane .</span><span class="sxs-lookup"><span data-stu-id="6b5d8-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="6b5d8-109">Wątek nie może być muszą być ramek zarządzanych na swój stos.</span><span class="sxs-lookup"><span data-stu-id="6b5d8-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="6b5d8-110">Wątki, które mogą być wyliczane nawet zanim [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6b5d8-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="6b5d8-111">Wyliczanie naturalnie będzie pusta.</span><span class="sxs-lookup"><span data-stu-id="6b5d8-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b5d8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b5d8-112">Requirements</span></span>  
 <span data-ttu-id="6b5d8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b5d8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b5d8-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b5d8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b5d8-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b5d8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b5d8-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b5d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b5d8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b5d8-117">See also</span></span>

