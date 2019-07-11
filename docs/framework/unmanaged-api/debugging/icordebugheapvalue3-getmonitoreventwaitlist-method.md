---
title: ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db34d56fd4d074551ca4823681bc5d94e76df758
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756618"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="75f1d-102">ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda</span><span class="sxs-lookup"><span data-stu-id="75f1d-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="75f1d-103">Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce na zdarzenia skojarzonego z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="75f1d-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75f1d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75f1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75f1d-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="75f1d-106">[out] Icordebugthreadenum — moduł wyliczający, który zawiera uporządkowaną listę wątków.</span><span class="sxs-lookup"><span data-stu-id="75f1d-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75f1d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75f1d-107">Return Value</span></span>  
 <span data-ttu-id="75f1d-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="75f1d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="75f1d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75f1d-109">HRESULT</span></span>|<span data-ttu-id="75f1d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="75f1d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75f1d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="75f1d-111">S_OK</span></span>|<span data-ttu-id="75f1d-112">Lista nie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="75f1d-112">The list is not empty.</span></span>|  
|<span data-ttu-id="75f1d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="75f1d-113">S_FALSE</span></span>|<span data-ttu-id="75f1d-114">Lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="75f1d-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="75f1d-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="75f1d-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75f1d-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75f1d-116">Remarks</span></span>  
 <span data-ttu-id="75f1d-117">Pierwszym wątku na liście jest pierwszym wątkiem, który jest wydane przez następne wywołanie <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75f1d-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75f1d-118">Następny wątek na liście jest wydawane w następujące wywołanie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="75f1d-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="75f1d-119">Jeśli lista nie jest pusty, ta metoda zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="75f1d-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="75f1d-120">Jeśli lista jest pusta, metoda zwraca wartość S_FALSE; w tym przypadku wyliczenia jest nadal ważny, mimo że jest on pusty.</span><span class="sxs-lookup"><span data-stu-id="75f1d-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="75f1d-121">W obu przypadkach interfejs wyliczenia jest można używać tylko na czas trwania bieżącego stanu zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="75f1d-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="75f1d-122">Jednak interfejsów wątku zrezygnować z niego są prawidłowe, aż wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="75f1d-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="75f1d-123">Jeśli `ppThreadEnum` nie jest prawidłową wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="75f1d-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="75f1d-124">W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, który, wątki oczekują na monitorze, metoda zwraca wartość HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="75f1d-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f1d-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75f1d-125">Requirements</span></span>  
 <span data-ttu-id="75f1d-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f1d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f1d-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75f1d-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75f1d-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75f1d-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75f1d-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f1d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f1d-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75f1d-130">See also</span></span>

- [<span data-ttu-id="75f1d-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="75f1d-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="75f1d-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="75f1d-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
