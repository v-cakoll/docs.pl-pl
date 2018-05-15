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
ms.openlocfilehash: 54d6535e2b2c4761eb3c67a990c62f2c311cf133
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="f5c2d-102">ICLRDataTarget3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c2d-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="f5c2d-103">Podklasa [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5c2d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f5c2d-104">Methods</span></span>  
  
|<span data-ttu-id="f5c2d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5c2d-105">Method</span></span>|<span data-ttu-id="f5c2d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f5c2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5c2d-107">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="f5c2d-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="f5c2d-108">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="f5c2d-109">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="f5c2d-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="f5c2d-110">Wywoływana przez usługi dostępu do danych CLR w celu pobrania rekordu kontekstu skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="f5c2d-111">GetExceptionThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="f5c2d-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="f5c2d-112">Metoda wywoływana przez usługi dostępu do danych CLR można uzyskać Identyfikatora wątku, który zgłosił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5c2d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5c2d-113">Remarks</span></span>  
 <span data-ttu-id="f5c2d-114">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="f5c2d-115">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="f5c2d-116">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="f5c2d-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c2d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5c2d-117">Requirements</span></span>  
 <span data-ttu-id="f5c2d-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c2d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c2d-119">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f5c2d-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f5c2d-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5c2d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5c2d-121">**Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c2d-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c2d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5c2d-122">See Also</span></span>  
 [<span data-ttu-id="f5c2d-123">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c2d-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="f5c2d-124">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c2d-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="f5c2d-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f5c2d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
