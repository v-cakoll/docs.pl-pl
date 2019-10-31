---
title: ICorDebugThread4::HadUnhandledException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: d9f0eff35dbe0058398d2d1c851ef85effa9cd28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122423"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="89b78-102">ICorDebugThread4::HadUnhandledException — Metoda</span><span class="sxs-lookup"><span data-stu-id="89b78-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="89b78-103">Wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="89b78-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b78-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89b78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="89b78-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89b78-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="89b78-106">określoną Wskaźnik na adres uporządkowanego wyliczania struktur [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="89b78-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89b78-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="89b78-107">Return Value</span></span>  
 <span data-ttu-id="89b78-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="89b78-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89b78-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89b78-109">HRESULT</span></span>|<span data-ttu-id="89b78-110">Opis</span><span class="sxs-lookup"><span data-stu-id="89b78-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89b78-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="89b78-111">S_OK</span></span>|<span data-ttu-id="89b78-112">Wątek miał nieobsługiwany wyjątek od momentu jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="89b78-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="89b78-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="89b78-113">S_FALSE</span></span>|<span data-ttu-id="89b78-114">Wątek nigdy nie miał nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="89b78-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89b78-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89b78-115">Remarks</span></span>  
 <span data-ttu-id="89b78-116">Ta metoda wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="89b78-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="89b78-117">Gdy wywołanie zwrotne nieobsłużonego wyjątku zostanie wyzwolone lub natywne dołączanie JIT jest inicjowane, ta metoda jest gwarantowana do zwrócenia S_OK.</span><span class="sxs-lookup"><span data-stu-id="89b78-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="89b78-118">Nie ma gwarancji, że metoda [ICorDebugThread. GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) zwróci wyjątek nieobsłużony; Jednak jeśli proces nie był jeszcze kontynuowany po otrzymaniu wywołania zwrotnego nieobsłużonego wyjątku lub po dołączeniu do natywnego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="89b78-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="89b78-119">Ponadto jest możliwe (Chociaż mało prawdopodobne), aby mieć więcej niż jeden wątek z nieobsługiwanym wyjątkiem w czasie, gdy zostanie wyzwolone Natywne Dołączanie JIT.</span><span class="sxs-lookup"><span data-stu-id="89b78-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="89b78-120">W takim przypadku nie ma możliwości ustalenia, który wyjątek wyzwalał dołączenie JIT.</span><span class="sxs-lookup"><span data-stu-id="89b78-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89b78-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89b78-121">Requirements</span></span>  
 <span data-ttu-id="89b78-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89b78-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89b78-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="89b78-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89b78-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89b78-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89b78-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89b78-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b78-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89b78-126">See also</span></span>

- [<span data-ttu-id="89b78-127">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="89b78-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="89b78-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="89b78-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="89b78-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="89b78-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
