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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74e106e17c0f0e5702927c4599fb143fb3554ce3
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065950"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="ad4ce-102">ICLRDataTarget3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ad4ce-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="ad4ce-103">Podklasa klasy [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ad4ce-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad4ce-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ad4ce-104">Methods</span></span>  
  
|<span data-ttu-id="ad4ce-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ad4ce-105">Method</span></span>|<span data-ttu-id="ad4ce-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ad4ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad4ce-107">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="ad4ce-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="ad4ce-108">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="ad4ce-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="ad4ce-109">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="ad4ce-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="ad4ce-110">Wywoływana przez usługi dostępu do danych CLR w celu pobrania rekordu kontekstu skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="ad4ce-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="ad4ce-111">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="ad4ce-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="ad4ce-112">Metoda wywoływana przez usługi dostępu do danych CLR, aby uzyskać identyfikator wątku, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ad4ce-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad4ce-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad4ce-113">Remarks</span></span>  
 <span data-ttu-id="ad4ce-114">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ad4ce-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="ad4ce-115">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad4ce-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="ad4ce-116">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad4ce-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad4ce-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad4ce-117">Requirements</span></span>  
 <span data-ttu-id="ad4ce-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad4ce-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad4ce-119">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ad4ce-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ad4ce-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad4ce-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad4ce-121">**Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ad4ce-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad4ce-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad4ce-122">See also</span></span>
- [<span data-ttu-id="ad4ce-123">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad4ce-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="ad4ce-124">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad4ce-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="ad4ce-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ad4ce-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
