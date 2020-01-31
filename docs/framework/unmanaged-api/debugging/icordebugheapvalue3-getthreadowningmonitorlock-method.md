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
ms.openlocfilehash: 8be7c0e32f6183deb354d8b3936ef55c2520fe9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788622"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="b68d9-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda</span><span class="sxs-lookup"><span data-stu-id="b68d9-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="b68d9-103">Zwraca zarządzany wątek, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b68d9-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b68d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b68d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b68d9-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="b68d9-106">określoną Zarządzany wątek, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b68d9-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="b68d9-107">określoną Liczba przypadków, w których ten wątek będzie musiał zwolnić blokadę, zanim powróci do elementu będącego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="b68d9-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b68d9-108">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="b68d9-108">Return Value</span></span>  
 <span data-ttu-id="b68d9-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b68d9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b68d9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b68d9-110">HRESULT</span></span>|<span data-ttu-id="b68d9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b68d9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b68d9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b68d9-112">S_OK</span></span>|<span data-ttu-id="b68d9-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b68d9-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b68d9-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b68d9-114">S_FALSE</span></span>|<span data-ttu-id="b68d9-115">Żaden zarządzany wątek nie jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b68d9-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b68d9-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="b68d9-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b68d9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b68d9-117">Remarks</span></span>  
 <span data-ttu-id="b68d9-118">Jeśli zarządzany wątek jest właścicielem blokady monitora dla tego obiektu:</span><span class="sxs-lookup"><span data-stu-id="b68d9-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="b68d9-119">Metoda zwraca S_OK.</span><span class="sxs-lookup"><span data-stu-id="b68d9-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="b68d9-120">Obiekt wątku jest prawidłowy do momentu zakończenia wątku.</span><span class="sxs-lookup"><span data-stu-id="b68d9-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="b68d9-121">Jeśli żaden zarządzany wątek nie jest właścicielem blokady monitora dla tego obiektu, `ppThread` i `pAcquisitionCount` są niezmienione, a metoda zwraca S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="b68d9-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="b68d9-122">Jeśli `ppThread` lub `pAcquisitionCount` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="b68d9-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="b68d9-123">Jeśli wystąpi błąd w taki sposób, że nie można ustalić, który z nich jest właścicielem blokady monitora dla tego obiektu, metoda zwraca wartość HRESULT, która wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="b68d9-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68d9-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b68d9-124">Requirements</span></span>  
 <span data-ttu-id="b68d9-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68d9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68d9-126">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b68d9-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b68d9-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b68d9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b68d9-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68d9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68d9-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b68d9-129">See also</span></span>

- [<span data-ttu-id="b68d9-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b68d9-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b68d9-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b68d9-131">Debugging</span></span>](index.md)
