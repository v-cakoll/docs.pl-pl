---
title: "ICorDebugController::EnumerateThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.EnumerateThreads
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7575bf2b50f11fab1c14f8fb28dc65e079c21de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="80b64-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="80b64-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="80b64-103">Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="80b64-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80b64-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80b64-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80b64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80b64-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="80b64-106">[out] Wskaźnik do obiektu "ICorDebugThreadEnum", który reprezentuje moduł wyliczający dla wszystkich zarządzanych wątków, które są aktywne w procesie adres.</span><span class="sxs-lookup"><span data-stu-id="80b64-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80b64-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80b64-107">Remarks</span></span>  
 <span data-ttu-id="80b64-108">Wątek jest uważany za aktywny po [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) wywołanie zwrotne zostało wysłane i przed [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) wywołanie zwrotne zostało wysłane. .</span><span class="sxs-lookup"><span data-stu-id="80b64-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="80b64-109">Zarządzanego wątku nie mogą muszą być ramek zarządzanych na swój stos.</span><span class="sxs-lookup"><span data-stu-id="80b64-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="80b64-110">Wątki mogą być wyliczane nawet zanim [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="80b64-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="80b64-111">Wyliczenie naturalnie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="80b64-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80b64-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80b64-112">Requirements</span></span>  
 <span data-ttu-id="80b64-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80b64-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80b64-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80b64-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80b64-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80b64-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80b64-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80b64-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80b64-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80b64-117">See Also</span></span>  
 
