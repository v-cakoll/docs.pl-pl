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
ms.openlocfilehash: 73b84179717e4b96a5c3637b85ae936a23bbf42d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748857"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="44bc5-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="44bc5-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="44bc5-103">Pobiera moduł wyliczający dla aktywnego zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="44bc5-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44bc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44bc5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44bc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44bc5-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="44bc5-106">[out] Wskaźnik na adres obiektu "icordebugthreadenum —", który reprezentuje moduł wyliczający wszystkie zarządzane wątki, które są aktywne w procesie.</span><span class="sxs-lookup"><span data-stu-id="44bc5-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44bc5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44bc5-107">Remarks</span></span>  
 <span data-ttu-id="44bc5-108">Wątek jest uważany za aktywny po [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) wywołanie zwrotne zostało wysłane i przed [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) wywołanie zwrotne zostało wysłane .</span><span class="sxs-lookup"><span data-stu-id="44bc5-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="44bc5-109">Wątek nie może być muszą być ramek zarządzanych na swój stos.</span><span class="sxs-lookup"><span data-stu-id="44bc5-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="44bc5-110">Wątki, które mogą być wyliczane nawet zanim [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="44bc5-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="44bc5-111">Wyliczanie naturalnie będzie pusta.</span><span class="sxs-lookup"><span data-stu-id="44bc5-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44bc5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44bc5-112">Requirements</span></span>  
 <span data-ttu-id="44bc5-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44bc5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44bc5-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44bc5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44bc5-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44bc5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44bc5-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44bc5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bc5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44bc5-117">See also</span></span>
