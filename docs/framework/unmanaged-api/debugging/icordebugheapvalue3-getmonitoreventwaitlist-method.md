---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="d6b14-102">ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6b14-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="d6b14-103">Udostępnia uporządkowaną listę wątków oczekujących w kolejce na zdarzenie, które jest skojarzone z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="d6b14-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b14-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6b14-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6b14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6b14-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="d6b14-106">[out] Moduł wyliczający ICorDebugThreadEnum, który zawiera listy uporządkowanej wątków.</span><span class="sxs-lookup"><span data-stu-id="d6b14-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6b14-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d6b14-107">Return Value</span></span>  
 <span data-ttu-id="d6b14-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d6b14-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d6b14-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6b14-109">HRESULT</span></span>|<span data-ttu-id="d6b14-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d6b14-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6b14-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6b14-111">S_OK</span></span>|<span data-ttu-id="d6b14-112">Lista nie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="d6b14-112">The list is not empty.</span></span>|  
|<span data-ttu-id="d6b14-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d6b14-113">S_FALSE</span></span>|<span data-ttu-id="d6b14-114">Lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="d6b14-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d6b14-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d6b14-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6b14-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6b14-116">Remarks</span></span>  
 <span data-ttu-id="d6b14-117">Pierwszym wątkiem w liście jest pierwszym wątkiem wydane przez następne wywołanie <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6b14-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d6b14-118">Następny wątek na liście jest wydany następujące wywołanie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d6b14-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="d6b14-119">Jeśli lista nie jest pusty, ta metoda zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="d6b14-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="d6b14-120">Jeśli lista jest pusta, metoda zwraca wartości S_FALSE; w takim przypadku wyliczenie jest nadal ważny, chociaż nie jest pusty.</span><span class="sxs-lookup"><span data-stu-id="d6b14-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="d6b14-121">W obu przypadkach interfejs wyliczenie jest możliwe tylko na czas trwania bieżącego stanu zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="d6b14-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="d6b14-122">Jednak zrezygnować z niej interfejsy wątku są prawidłowe, dopóki kończy działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="d6b14-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="d6b14-123">Jeśli `ppThreadEnum` nie jest wskaźnikiem prawidłowe, wynikiem jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d6b14-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="d6b14-124">W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, które, wątków oczekujących monitora, metoda zwraca HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="d6b14-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6b14-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6b14-125">Requirements</span></span>  
 <span data-ttu-id="d6b14-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6b14-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6b14-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6b14-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6b14-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6b14-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6b14-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6b14-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b14-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6b14-130">See Also</span></span>  
 [<span data-ttu-id="d6b14-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d6b14-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d6b14-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d6b14-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
