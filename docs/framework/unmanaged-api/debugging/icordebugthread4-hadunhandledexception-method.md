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
ms.openlocfilehash: f558a4c94afeb69f58605958ddcb91e4be772c39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791353"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="b640a-102">ICorDebugThread4::HadUnhandledException — Metoda</span><span class="sxs-lookup"><span data-stu-id="b640a-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="b640a-103">Wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b640a-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b640a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b640a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b640a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b640a-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="b640a-106">określoną Wskaźnik na adres uporządkowanego wyliczania struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="b640a-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b640a-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="b640a-107">Return Value</span></span>  
 <span data-ttu-id="b640a-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b640a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b640a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b640a-109">HRESULT</span></span>|<span data-ttu-id="b640a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b640a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b640a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b640a-111">S_OK</span></span>|<span data-ttu-id="b640a-112">Wątek miał nieobsługiwany wyjątek od momentu jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="b640a-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="b640a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b640a-113">S_FALSE</span></span>|<span data-ttu-id="b640a-114">Wątek nigdy nie miał nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b640a-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b640a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b640a-115">Remarks</span></span>  
 <span data-ttu-id="b640a-116">Ta metoda wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b640a-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="b640a-117">Gdy wywołanie zwrotne nieobsłużonego wyjątku zostanie wyzwolone lub natywne dołączanie JIT jest inicjowane, ta metoda jest gwarantowana do zwrócenia S_OK.</span><span class="sxs-lookup"><span data-stu-id="b640a-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="b640a-118">Nie ma gwarancji, że metoda [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) zwróci wyjątek nieobsłużony; Jednak jeśli proces nie był jeszcze kontynuowany po otrzymaniu wywołania zwrotnego nieobsłużonego wyjątku lub po dołączeniu do natywnego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="b640a-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="b640a-119">Ponadto jest możliwe (Chociaż mało prawdopodobne), aby mieć więcej niż jeden wątek z nieobsługiwanym wyjątkiem w czasie, gdy zostanie wyzwolone Natywne Dołączanie JIT.</span><span class="sxs-lookup"><span data-stu-id="b640a-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="b640a-120">W takim przypadku nie ma możliwości ustalenia, który wyjątek wyzwalał dołączenie JIT.</span><span class="sxs-lookup"><span data-stu-id="b640a-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b640a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b640a-121">Requirements</span></span>  
 <span data-ttu-id="b640a-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b640a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b640a-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b640a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b640a-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b640a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b640a-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b640a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b640a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b640a-126">See also</span></span>

- [<span data-ttu-id="b640a-127">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b640a-127">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="b640a-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b640a-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b640a-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b640a-129">Debugging</span></span>](index.md)
