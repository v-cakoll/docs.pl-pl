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
ms.openlocfilehash: ec265525d01dab0669939569501fce91b500a900
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127489"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="6a0c2-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a0c2-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="6a0c2-103">Zwraca zarządzany wątek, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a0c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a0c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a0c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a0c2-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="6a0c2-106">określoną Zarządzany wątek, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="6a0c2-107">określoną Liczba przypadków, w których ten wątek będzie musiał zwolnić blokadę, zanim powróci do elementu będącego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a0c2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6a0c2-108">Return Value</span></span>  
 <span data-ttu-id="6a0c2-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6a0c2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a0c2-110">HRESULT</span></span>|<span data-ttu-id="6a0c2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6a0c2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a0c2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a0c2-112">S_OK</span></span>|<span data-ttu-id="6a0c2-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="6a0c2-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6a0c2-114">S_FALSE</span></span>|<span data-ttu-id="6a0c2-115">Żaden zarządzany wątek nie jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6a0c2-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="6a0c2-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a0c2-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a0c2-117">Remarks</span></span>  
 <span data-ttu-id="6a0c2-118">Jeśli zarządzany wątek jest właścicielem blokady monitora dla tego obiektu:</span><span class="sxs-lookup"><span data-stu-id="6a0c2-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="6a0c2-119">Metoda zwraca S_OK.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="6a0c2-120">Obiekt wątku jest prawidłowy do momentu zakończenia wątku.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="6a0c2-121">Jeśli żaden zarządzany wątek nie jest właścicielem blokady monitora dla tego obiektu, `ppThread` i `pAcquisitionCount` są niezmienione, a metoda zwraca S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="6a0c2-122">Jeśli `ppThread` lub `pAcquisitionCount` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="6a0c2-123">Jeśli wystąpi błąd w taki sposób, że nie można ustalić, który z nich jest właścicielem blokady monitora dla tego obiektu, metoda zwraca wartość HRESULT, która wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="6a0c2-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a0c2-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a0c2-124">Requirements</span></span>  
 <span data-ttu-id="6a0c2-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a0c2-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a0c2-126">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a0c2-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a0c2-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a0c2-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a0c2-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a0c2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0c2-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a0c2-129">See also</span></span>

- [<span data-ttu-id="6a0c2-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6a0c2-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6a0c2-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6a0c2-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
