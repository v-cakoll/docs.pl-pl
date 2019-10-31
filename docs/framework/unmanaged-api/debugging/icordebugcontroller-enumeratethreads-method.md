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
ms.openlocfilehash: 291f6c05171b5e507afaa70537aafdc9002a506e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125412"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="4a692-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a692-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="4a692-103">Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="4a692-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a692-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a692-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a692-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a692-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="4a692-106">określoną Wskaźnik do adresu obiektu "ICorDebugThreadEnum", który reprezentuje moduł wyliczający dla wszystkich zarządzanych wątków, które są aktywne w procesie.</span><span class="sxs-lookup"><span data-stu-id="4a692-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a692-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a692-107">Remarks</span></span>  
 <span data-ttu-id="4a692-108">Wątek jest uznawany za aktywny po wysłaniu wywołania zwrotnego [ICorDebugManagedCallback:: Onthreading](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) i przed wysłaniem wywołania zwrotnego [ICorDebugManagedCallback:: ExitThread —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4a692-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="4a692-109">Wątek zarządzany nie musi mieć żadnych zarządzanych ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="4a692-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="4a692-110">Wątki można wyliczyć nawet przed wywołaniem zwrotnym [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4a692-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="4a692-111">Wyliczenie będzie w naturalny sposób puste.</span><span class="sxs-lookup"><span data-stu-id="4a692-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a692-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a692-112">Requirements</span></span>  
 <span data-ttu-id="4a692-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a692-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a692-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4a692-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a692-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4a692-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a692-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a692-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a692-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a692-117">See also</span></span>
