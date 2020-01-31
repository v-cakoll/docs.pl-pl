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
ms.openlocfilehash: 815dc63a2dedecc613506b0f98702f58d6e7bd04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783789"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="ad09a-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad09a-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="ad09a-103">Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="ad09a-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad09a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad09a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad09a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad09a-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="ad09a-106">określoną Wskaźnik do adresu obiektu "ICorDebugThreadEnum", który reprezentuje moduł wyliczający dla wszystkich zarządzanych wątków, które są aktywne w procesie.</span><span class="sxs-lookup"><span data-stu-id="ad09a-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad09a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad09a-107">Remarks</span></span>  
 <span data-ttu-id="ad09a-108">Wątek jest uznawany za aktywny po wysłaniu wywołania zwrotnego [ICorDebugManagedCallback:: Onthreading](icordebugmanagedcallback-createthread-method.md) i przed wysłaniem wywołania zwrotnego [ICorDebugManagedCallback:: ExitThread —](icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ad09a-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="ad09a-109">Wątek zarządzany nie musi mieć żadnych zarządzanych ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="ad09a-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="ad09a-110">Wątki można wyliczyć nawet przed wywołaniem zwrotnym [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ad09a-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="ad09a-111">Wyliczenie będzie w naturalny sposób puste.</span><span class="sxs-lookup"><span data-stu-id="ad09a-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad09a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad09a-112">Requirements</span></span>  
 <span data-ttu-id="ad09a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad09a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad09a-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad09a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad09a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ad09a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad09a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad09a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad09a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad09a-117">See also</span></span>
