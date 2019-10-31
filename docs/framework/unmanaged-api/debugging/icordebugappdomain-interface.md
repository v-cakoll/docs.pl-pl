---
title: ICorDebugAppDomain — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 9abcb765357a0f305ae5acae77a4a13b07a003a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134685"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="67ead-102">ICorDebugAppDomain — Interfejs</span><span class="sxs-lookup"><span data-stu-id="67ead-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="67ead-103">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="67ead-104">Ten interfejs jest podklasą elementu ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="67ead-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67ead-105">Metody</span><span class="sxs-lookup"><span data-stu-id="67ead-105">Methods</span></span>  
  
|<span data-ttu-id="67ead-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-106">Method</span></span>|<span data-ttu-id="67ead-107">Opis</span><span class="sxs-lookup"><span data-stu-id="67ead-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67ead-108">Attach, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="67ead-109">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="67ead-110">EnumerateAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="67ead-111">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="67ead-112">EnumerateBreakpoints, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="67ead-113">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="67ead-114">EnumerateSteppers, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="67ead-115">Pobiera moduł wyliczający dla wszystkich aktywnych współdziałań w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="67ead-116">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="67ead-117">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="67ead-118">GetModuleFromMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="67ead-119">Pobiera obiekt ICorDebugModule z danym interfejsem metadanych.</span><span class="sxs-lookup"><span data-stu-id="67ead-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="67ead-120">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="67ead-121">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="67ead-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="67ead-123">Pobiera wskaźnik interfejsu do domeny aplikacji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="67ead-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="67ead-124">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="67ead-125">Pobiera proces zawierający domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="67ead-126">IsAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="67ead-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="67ead-127">Określa, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67ead-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ead-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67ead-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67ead-129">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="67ead-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ead-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67ead-130">Requirements</span></span>  
 <span data-ttu-id="67ead-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ead-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ead-132">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="67ead-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67ead-133">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="67ead-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67ead-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67ead-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ead-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67ead-135">See also</span></span>

- [<span data-ttu-id="67ead-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="67ead-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
