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
ms.openlocfilehash: d73a82ddbb15ba7895f1e5e10f7066909a3c7e43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697154"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="027f4-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="027f4-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="027f4-103">Pobiera moduł wyliczający dla aktywnego zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="027f4-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="027f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="027f4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="027f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="027f4-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="027f4-106">[out] Wskaźnik na adres obiektu "icordebugthreadenum —", który reprezentuje moduł wyliczający wszystkie zarządzane wątki, które są aktywne w procesie.</span><span class="sxs-lookup"><span data-stu-id="027f4-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="027f4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="027f4-107">Remarks</span></span>  
 <span data-ttu-id="027f4-108">Wątek jest uważany za aktywny po [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) wywołanie zwrotne zostało wysłane i przed [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) wywołanie zwrotne zostało wysłane .</span><span class="sxs-lookup"><span data-stu-id="027f4-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="027f4-109">Wątek nie może być muszą być ramek zarządzanych na swój stos.</span><span class="sxs-lookup"><span data-stu-id="027f4-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="027f4-110">Wątki, które mogą być wyliczane nawet zanim [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="027f4-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="027f4-111">Wyliczanie naturalnie będzie pusta.</span><span class="sxs-lookup"><span data-stu-id="027f4-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="027f4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="027f4-112">Requirements</span></span>  
 <span data-ttu-id="027f4-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="027f4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="027f4-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="027f4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="027f4-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="027f4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="027f4-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="027f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="027f4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="027f4-117">See also</span></span>

