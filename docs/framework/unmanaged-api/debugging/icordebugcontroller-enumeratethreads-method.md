---
title: "ICorDebugController::EnumerateThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61d96aa6c8ae4a50c3afbcd84033244208e2444d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="119e3-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="119e3-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="119e3-103">Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="119e3-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="119e3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="119e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="119e3-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="119e3-106">[out] Wskaźnik do obiektu "ICorDebugThreadEnum", który reprezentuje moduł wyliczający dla wszystkich zarządzanych wątków, które są aktywne w procesie adres.</span><span class="sxs-lookup"><span data-stu-id="119e3-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="119e3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="119e3-107">Remarks</span></span>  
 <span data-ttu-id="119e3-108">Wątek jest uważany za aktywny po [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) wywołanie zwrotne zostało wysłane i przed [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) wywołanie zwrotne zostało wysłane. .</span><span class="sxs-lookup"><span data-stu-id="119e3-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="119e3-109">Zarządzanego wątku nie mogą muszą być ramek zarządzanych na swój stos.</span><span class="sxs-lookup"><span data-stu-id="119e3-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="119e3-110">Wątki mogą być wyliczane nawet zanim [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="119e3-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="119e3-111">Wyliczenie naturalnie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="119e3-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119e3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="119e3-112">Requirements</span></span>  
 <span data-ttu-id="119e3-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119e3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119e3-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="119e3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="119e3-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="119e3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="119e3-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119e3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119e3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="119e3-117">See Also</span></span>  
 
