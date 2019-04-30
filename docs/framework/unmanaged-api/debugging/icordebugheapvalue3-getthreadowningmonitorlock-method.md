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
ms.openlocfilehash: 1678f1de7c23387f028348dadbc7b61e2cdc035c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701024"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="4e210-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e210-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="4e210-103">Zwraca wątków zarządzanych, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e210-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e210-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e210-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e210-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e210-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="4e210-106">[out] Wątków zarządzanych, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e210-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="4e210-107">[out] Ile razy ten wątek musi zwolnić blokadę przed zwróceniem jest bez właściciela.</span><span class="sxs-lookup"><span data-stu-id="4e210-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e210-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4e210-108">Return Value</span></span>  
 <span data-ttu-id="4e210-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="4e210-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4e210-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e210-110">HRESULT</span></span>|<span data-ttu-id="4e210-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4e210-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4e210-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4e210-112">S_OK</span></span>|<span data-ttu-id="4e210-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4e210-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="4e210-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4e210-114">S_FALSE</span></span>|<span data-ttu-id="4e210-115">Nie wątków zarządzanych jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e210-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4e210-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="4e210-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e210-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e210-117">Remarks</span></span>  
 <span data-ttu-id="4e210-118">Jeśli wątek jest właścicielem blokady monitora dla tego obiektu:</span><span class="sxs-lookup"><span data-stu-id="4e210-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="4e210-119">Metoda zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="4e210-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="4e210-120">Obiekt wątku jest prawidłowy, aż wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="4e210-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="4e210-121">Jeśli nie wątków zarządzanych jest właścicielem blokady monitora dla tego obiektu `ppThread` i `pAcquisitionCount` ulegną zmianie, a metoda zwraca wartość S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="4e210-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="4e210-122">Jeśli `ppThread` lub `pAcquisitionCount` nie jest prawidłową wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="4e210-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="4e210-123">W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, który, wątek jest właścicielem blokady monitora dla tego obiektu, metoda zwraca wartość HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="4e210-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e210-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e210-124">Requirements</span></span>  
 <span data-ttu-id="4e210-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e210-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e210-126">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e210-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e210-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e210-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e210-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e210-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e210-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e210-129">See also</span></span>

- [<span data-ttu-id="4e210-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4e210-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4e210-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4e210-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
