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
ms.openlocfilehash: 15900fab59d172ada67d8aefeab698e1b44f808e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794392"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="67427-102">ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda</span><span class="sxs-lookup"><span data-stu-id="67427-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="67427-103">Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce dla zdarzenia, które jest skojarzone z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="67427-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67427-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67427-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67427-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="67427-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="67427-106">określoną Moduł wyliczający ICorDebugThreadEnum, który dostarcza uporządkowaną listę wątków.</span><span class="sxs-lookup"><span data-stu-id="67427-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67427-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="67427-107">Return Value</span></span>  
 <span data-ttu-id="67427-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="67427-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="67427-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67427-109">HRESULT</span></span>|<span data-ttu-id="67427-110">Opis</span><span class="sxs-lookup"><span data-stu-id="67427-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67427-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="67427-111">S_OK</span></span>|<span data-ttu-id="67427-112">Lista nie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="67427-112">The list is not empty.</span></span>|  
|<span data-ttu-id="67427-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="67427-113">S_FALSE</span></span>|<span data-ttu-id="67427-114">Lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="67427-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="67427-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="67427-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67427-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67427-116">Remarks</span></span>  
 <span data-ttu-id="67427-117">Pierwszy wątek na liście to pierwszy wątek, który jest wydawany przez następne wywołanie do <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67427-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67427-118">Następny wątek na liście jest publikowany w następującym wywołaniu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="67427-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="67427-119">Jeśli lista nie jest pusta, metoda zwraca S_OK.</span><span class="sxs-lookup"><span data-stu-id="67427-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="67427-120">Jeśli lista jest pusta, metoda zwraca S_FALSE; w takim przypadku Wyliczenie jest nadal ważne, chociaż jest puste.</span><span class="sxs-lookup"><span data-stu-id="67427-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="67427-121">W obu przypadkach interfejs wyliczenia jest używany tylko na czas trwania bieżącego zsynchronizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="67427-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="67427-122">Jednak interfejsy wątku są od niego ważne do momentu zakończenia wątku.</span><span class="sxs-lookup"><span data-stu-id="67427-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="67427-123">Jeśli `ppThreadEnum` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="67427-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="67427-124">Jeśli wystąpi błąd, aby nie można było ustalić, który, jeśli istnieje, wątki oczekują na monitor, metoda zwraca wartość HRESULT, która wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="67427-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67427-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67427-125">Requirements</span></span>  
 <span data-ttu-id="67427-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67427-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67427-127">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="67427-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67427-128">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="67427-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67427-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67427-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67427-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67427-130">See also</span></span>

- [<span data-ttu-id="67427-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="67427-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="67427-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="67427-132">Debugging</span></span>](index.md)
