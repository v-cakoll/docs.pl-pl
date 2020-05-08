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
ms.openlocfilehash: 4d69f13d4716b43c815148ff0fe4aa087b57c6e5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892756"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="c2959-102">ICorDebugController::EnumerateThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2959-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="c2959-103">Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.</span><span class="sxs-lookup"><span data-stu-id="c2959-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2959-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2959-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2959-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2959-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="c2959-106">określoną Wskaźnik do adresu obiektu "ICorDebugThreadEnum", który reprezentuje moduł wyliczający dla wszystkich zarządzanych wątków, które są aktywne w procesie.</span><span class="sxs-lookup"><span data-stu-id="c2959-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2959-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2959-107">Remarks</span></span>  
 <span data-ttu-id="c2959-108">Wątek jest uznawany za aktywny po wysłaniu wywołania zwrotnego [ICorDebugManagedCallback:: Onthreading](icordebugmanagedcallback-createthread-method.md) i przed wysłaniem wywołania zwrotnego [ICorDebugManagedCallback:: ExitThread —](icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c2959-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="c2959-109">Wątek zarządzany nie musi mieć żadnych zarządzanych ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="c2959-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="c2959-110">Wątki można wyliczyć nawet przed wywołaniem zwrotnym [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c2959-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="c2959-111">Wyliczenie będzie w naturalny sposób puste.</span><span class="sxs-lookup"><span data-stu-id="c2959-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2959-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2959-112">Requirements</span></span>  
 <span data-ttu-id="c2959-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2959-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2959-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2959-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2959-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2959-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2959-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2959-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2959-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2959-117">See also</span></span>
