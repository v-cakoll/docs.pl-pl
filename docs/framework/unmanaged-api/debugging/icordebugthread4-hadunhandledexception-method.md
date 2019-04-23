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
ms.openlocfilehash: 12433786f353212c1ffbd57e9bf526c3ecc60e9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163634"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="9cdaf-102">ICorDebugThread4::HadUnhandledException — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cdaf-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="9cdaf-103">Wskazuje, czy wątek nigdy nie miała nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cdaf-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cdaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cdaf-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="9cdaf-106">[out] Wskaźnik do adresu uporządkowane wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cdaf-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9cdaf-107">Return Value</span></span>  
 <span data-ttu-id="9cdaf-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9cdaf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cdaf-109">HRESULT</span></span>|<span data-ttu-id="9cdaf-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9cdaf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cdaf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cdaf-111">S_OK</span></span>|<span data-ttu-id="9cdaf-112">Wątek miała nieobsługiwany wyjątek od jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="9cdaf-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9cdaf-113">S_FALSE</span></span>|<span data-ttu-id="9cdaf-114">Wątek nigdy nie miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cdaf-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cdaf-115">Remarks</span></span>  
 <span data-ttu-id="9cdaf-116">Ta metoda wskazuje, czy wątek nigdy nie miała nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="9cdaf-117">Do czasu jest wyzwalana wywołania zwrotnego nieobsługiwany wyjątek lub natywnych dołączania JIT jest inicjowane, ta metoda gwarancję zwracania S_OK.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="9cdaf-118">Nie ma żadnej gwarancji, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda zwróci nieobsługiwany wyjątek; jednak będzie Jeśli proces nie jeszcze jest kontynuowane po otrzymaniu wywołania zwrotnego nieobsługiwanego wyjątku lub w natywne dołączania JIT.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="9cdaf-119">Ponadto istnieje możliwość (chociaż to mało prawdopodobne) mieć więcej niż jeden wątek za pomocą nieobsługiwany wyjątek w czasie natywnych dołączania JIT jest wyzwalane.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="9cdaf-120">W takim przypadku nie ma możliwości do określenia, który wyjątek wyzwalane dołączania JIT.</span><span class="sxs-lookup"><span data-stu-id="9cdaf-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cdaf-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cdaf-121">Requirements</span></span>  
 <span data-ttu-id="9cdaf-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cdaf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cdaf-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cdaf-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cdaf-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cdaf-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cdaf-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cdaf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdaf-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cdaf-126">See also</span></span>

- [<span data-ttu-id="9cdaf-127">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cdaf-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="9cdaf-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9cdaf-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9cdaf-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9cdaf-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
