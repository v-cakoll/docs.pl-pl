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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="1d360-102">ICorDebugThread4::HadUnhandledException — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d360-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="1d360-103">Wskazuje, czy wątek nigdy miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1d360-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d360-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d360-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d360-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d360-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="1d360-106">[out] Wskaźnik do adresu w kolejności wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="1d360-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d360-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d360-107">Return Value</span></span>  
 <span data-ttu-id="1d360-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="1d360-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1d360-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d360-109">HRESULT</span></span>|<span data-ttu-id="1d360-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1d360-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d360-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d360-111">S_OK</span></span>|<span data-ttu-id="1d360-112">Wątek miał nieobsługiwany wyjątek od czasu jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="1d360-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="1d360-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1d360-113">S_FALSE</span></span>|<span data-ttu-id="1d360-114">Wątek nigdy nie miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1d360-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d360-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d360-115">Remarks</span></span>  
 <span data-ttu-id="1d360-116">Ta metoda wskazuje, czy wątek nigdy miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1d360-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="1d360-117">Do czasu wywołania zwrotnego nieobsługiwany wyjątek zostanie wywołany lub natywnego dołączania JIT jest inicjowane, ta metoda jest gwarantowana zwrócić wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="1d360-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="1d360-118">Nie ma żadnych gwarancji, że [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda zwróci nieobsługiwany wyjątek; jednak zostanie Jeśli proces nie jeszcze jest kontynuowane po pierwsze wywołanie zwrotne nieobsługiwany wyjątek lub na natywny dołączania JIT.</span><span class="sxs-lookup"><span data-stu-id="1d360-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="1d360-119">Ponadto istnieje możliwość (chociaż jest mało prawdopodobne) ma więcej niż jeden wątek z nieobsługiwany wyjątek w czasie natywnego dołączania JIT zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="1d360-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="1d360-120">W takim przypadku nie ma nie można określić, który wyjątków wyzwalane dołączania JIT.</span><span class="sxs-lookup"><span data-stu-id="1d360-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d360-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d360-121">Requirements</span></span>  
 <span data-ttu-id="1d360-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d360-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d360-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d360-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d360-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d360-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d360-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d360-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d360-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d360-126">See Also</span></span>  
 [<span data-ttu-id="1d360-127">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d360-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="1d360-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1d360-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1d360-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1d360-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
