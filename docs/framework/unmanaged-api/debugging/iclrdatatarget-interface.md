---
title: "ICLRDataTarget — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a40276b28f3d20428f0d7eb0556a762fdb56801
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="b4e00-102">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b4e00-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="b4e00-103">Udostępnia metody do interakcji z elementem docelowym o środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b4e00-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4e00-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b4e00-104">Methods</span></span>  
  
|<span data-ttu-id="b4e00-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-105">Method</span></span>|<span data-ttu-id="b4e00-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b4e00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4e00-107">GetCurrentThreadID — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="b4e00-108">Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="b4e00-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="b4e00-109">GetImageBase — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="b4e00-110">Pobiera adres podstawowy pamięci dla określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="b4e00-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="b4e00-111">GetMachineType — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="b4e00-112">Pobiera identyfikator dla rodzaju zestaw instrukcji, który używa procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b4e00-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="b4e00-113">GetPointerSize — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="b4e00-114">Pobiera rozmiar w bajtach wskaźnik do bieżącą lokalizację docelową.</span><span class="sxs-lookup"><span data-stu-id="b4e00-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="b4e00-115">GetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="b4e00-116">Pobiera wskaźnik w kontekście wątku o podanym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="b4e00-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="b4e00-117">GetTLSValue — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="b4e00-118">Pobiera wartość w lokalny magazyn wątków (TLS) w określonym indeksie dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="b4e00-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="b4e00-119">ReadVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="b4e00-120">Odczytuje dane z adresów pamięci wirtualnej określony w buforze określona.</span><span class="sxs-lookup"><span data-stu-id="b4e00-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="b4e00-121">Request — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="b4e00-122">Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi do żądania operacji zdefiniowanej przez implementację.</span><span class="sxs-lookup"><span data-stu-id="b4e00-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="b4e00-123">SetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="b4e00-124">Ustawia bieżący kontekst określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b4e00-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="b4e00-125">SetTLSValue — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="b4e00-126">Ustawia wartość w lokalny magazyn wątków (TLS) z określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b4e00-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="b4e00-127">WriteVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="b4e00-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="b4e00-128">Zapisuje dane z określonego bufora na adres określony pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="b4e00-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4e00-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4e00-129">Remarks</span></span>  
 <span data-ttu-id="b4e00-130">Klienta interfejsu API (debuger) musi implementować ten interfejs na potrzeby elementu określonego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b4e00-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="b4e00-131">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="b4e00-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4e00-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4e00-132">Requirements</span></span>  
 <span data-ttu-id="b4e00-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4e00-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4e00-134">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b4e00-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b4e00-135">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4e00-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4e00-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4e00-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e00-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4e00-137">See Also</span></span>  
 [<span data-ttu-id="b4e00-138">ICLRDataTarget2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b4e00-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="b4e00-139">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="b4e00-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
