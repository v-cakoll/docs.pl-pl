---
title: ICorDebugAppDomain, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12753ab65f9339e8f6c3049bb72755e87464eb1a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963109"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="f4c9a-102">ICorDebugAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4c9a-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="f4c9a-103">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="f4c9a-104">Ten interfejs jest podklasą elementu ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4c9a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f4c9a-105">Methods</span></span>  
  
|<span data-ttu-id="f4c9a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-106">Method</span></span>|<span data-ttu-id="f4c9a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f4c9a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4c9a-108">Attach, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="f4c9a-109">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-110">EnumerateAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="f4c9a-111">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-112">EnumerateBreakpoints, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="f4c9a-113">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-114">EnumerateSteppers, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="f4c9a-115">Pobiera moduł wyliczający dla wszystkich aktywnych współdziałań w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-116">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="f4c9a-117">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-118">GetModuleFromMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="f4c9a-119">Pobiera obiekt ICorDebugModule z danym interfejsem metadanych.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="f4c9a-120">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="f4c9a-121">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="f4c9a-123">Pobiera wskaźnik interfejsu do domeny aplikacji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f4c9a-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-124">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="f4c9a-125">Pobiera proces zawierający domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="f4c9a-126">IsAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="f4c9a-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="f4c9a-127">Określa, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4c9a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4c9a-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4c9a-129">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="f4c9a-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4c9a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4c9a-130">Requirements</span></span>  
 <span data-ttu-id="f4c9a-131">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4c9a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4c9a-132">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4c9a-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4c9a-133">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4c9a-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4c9a-134">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c9a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c9a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4c9a-135">See also</span></span>

- [<span data-ttu-id="f4c9a-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f4c9a-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
