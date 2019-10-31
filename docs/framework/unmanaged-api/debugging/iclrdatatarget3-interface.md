---
title: ICLRDataTarget3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: a6591f7d7b632bcdbdabb1633f7431d79da7ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111813"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="bc74d-102">ICLRDataTarget3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bc74d-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="bc74d-103">Podklasa elementu [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , która zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="bc74d-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc74d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bc74d-104">Methods</span></span>  
  
|<span data-ttu-id="bc74d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bc74d-105">Method</span></span>|<span data-ttu-id="bc74d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bc74d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc74d-107">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="bc74d-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="bc74d-108">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="bc74d-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="bc74d-109">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="bc74d-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="bc74d-110">Wywoływana przez usługi dostępu do danych CLR w celu pobrania rekordu kontekstu skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="bc74d-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="bc74d-111">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="bc74d-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="bc74d-112">Wywoływane przez usługi dostępu do danych środowiska CLR w celu uzyskania identyfikatora wątku, który wywołał wyjątek.</span><span class="sxs-lookup"><span data-stu-id="bc74d-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc74d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc74d-113">Remarks</span></span>  
 <span data-ttu-id="bc74d-114">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="bc74d-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="bc74d-115">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="bc74d-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="bc74d-116">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="bc74d-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc74d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc74d-117">Requirements</span></span>  
 <span data-ttu-id="bc74d-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc74d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc74d-119">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="bc74d-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bc74d-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc74d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc74d-121">**Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bc74d-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc74d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc74d-122">See also</span></span>

- [<span data-ttu-id="bc74d-123">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc74d-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="bc74d-124">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc74d-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="bc74d-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc74d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
