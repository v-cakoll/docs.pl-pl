---
title: ICLRDataTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0a5abe8877c8414443fadc00e223df240721132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410445"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="28144-102">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="28144-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="28144-103">Udostępnia metody do interakcji z elementem docelowym o środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="28144-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28144-104">Metody</span><span class="sxs-lookup"><span data-stu-id="28144-104">Methods</span></span>  
  
|<span data-ttu-id="28144-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="28144-105">Method</span></span>|<span data-ttu-id="28144-106">Opis</span><span class="sxs-lookup"><span data-stu-id="28144-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28144-107">GetCurrentThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="28144-108">Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="28144-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="28144-109">GetImageBase, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="28144-110">Pobiera adres podstawowy pamięci dla określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="28144-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="28144-111">GetMachineType, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="28144-112">Pobiera identyfikator dla rodzaju zestaw instrukcji, który używa procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="28144-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="28144-113">GetPointerSize, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="28144-114">Pobiera rozmiar w bajtach wskaźnik do bieżącą lokalizację docelową.</span><span class="sxs-lookup"><span data-stu-id="28144-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="28144-115">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="28144-116">Pobiera wskaźnik w kontekście wątku o podanym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="28144-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="28144-117">GetTLSValue, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="28144-118">Pobiera wartość w lokalny magazyn wątków (TLS) w określonym indeksie dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="28144-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="28144-119">ReadVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="28144-120">Odczytuje dane z adresów pamięci wirtualnej określony w buforze określona.</span><span class="sxs-lookup"><span data-stu-id="28144-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="28144-121">Request, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="28144-122">Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi do żądania operacji zdefiniowanej przez implementację.</span><span class="sxs-lookup"><span data-stu-id="28144-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="28144-123">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="28144-124">Ustawia bieżący kontekst określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="28144-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="28144-125">SetTLSValue, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="28144-126">Ustawia wartość w lokalny magazyn wątków (TLS) z określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="28144-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="28144-127">WriteVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="28144-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="28144-128">Zapisuje dane z określonego bufora na adres określony pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="28144-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28144-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28144-129">Remarks</span></span>  
 <span data-ttu-id="28144-130">Klienta interfejsu API (debuger) musi implementować ten interfejs na potrzeby elementu określonego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="28144-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="28144-131">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="28144-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28144-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28144-132">Requirements</span></span>  
 <span data-ttu-id="28144-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28144-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28144-134">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="28144-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="28144-135">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28144-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28144-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28144-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28144-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28144-137">See Also</span></span>  
 [<span data-ttu-id="28144-138">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="28144-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="28144-139">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="28144-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
