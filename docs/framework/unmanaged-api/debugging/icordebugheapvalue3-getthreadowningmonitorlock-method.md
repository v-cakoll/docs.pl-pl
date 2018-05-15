---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ba09991e9452a86c6b7a1cbb08a38a71ba2aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="ede54-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda</span><span class="sxs-lookup"><span data-stu-id="ede54-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="ede54-103">Zwraca zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="ede54-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ede54-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ede54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ede54-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="ede54-106">[out] Zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="ede54-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="ede54-107">[out] Ile razy ten wątek musi zwolnić blokady przed zwróceniem do trwa bez właściciela.</span><span class="sxs-lookup"><span data-stu-id="ede54-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ede54-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ede54-108">Return Value</span></span>  
 <span data-ttu-id="ede54-109">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="ede54-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ede54-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ede54-110">HRESULT</span></span>|<span data-ttu-id="ede54-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ede54-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ede54-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ede54-112">S_OK</span></span>|<span data-ttu-id="ede54-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ede54-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="ede54-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ede54-114">S_FALSE</span></span>|<span data-ttu-id="ede54-115">Nie zarządzanego wątku jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="ede54-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ede54-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ede54-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ede54-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ede54-117">Remarks</span></span>  
 <span data-ttu-id="ede54-118">Jeśli zarządzanego wątku jest właścicielem blokady monitora dla tego obiektu:</span><span class="sxs-lookup"><span data-stu-id="ede54-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="ede54-119">Metoda zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="ede54-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="ede54-120">Obiekt wątku jest prawidłowy, dopóki kończy działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="ede54-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="ede54-121">Jeśli nie zarządzanego wątku jest właścicielem blokady monitora w tym obiekcie `ppThread` i `pAcquisitionCount` nie uległy zmianie, a metoda zwraca wartości S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="ede54-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="ede54-122">Jeśli `ppThread` lub `pAcquisitionCount` nie jest wskaźnikiem prawidłowe, wynikiem jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="ede54-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="ede54-123">W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, które, wątek jest właścicielem blokady monitora w tym obiekcie metoda zwraca HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="ede54-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede54-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ede54-124">Requirements</span></span>  
 <span data-ttu-id="ede54-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede54-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede54-126">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ede54-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ede54-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ede54-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ede54-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede54-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede54-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ede54-129">See Also</span></span>  
 [<span data-ttu-id="ede54-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ede54-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ede54-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ede54-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
