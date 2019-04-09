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
ms.openlocfilehash: 40619aa40f9924d94c82541eb8d30790e774a675
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141508"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="5e0da-102">ICorDebugAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e0da-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="5e0da-103">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="5e0da-104">Ten interfejs jest podklasą icordebugcontroller —.</span><span class="sxs-lookup"><span data-stu-id="5e0da-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e0da-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5e0da-105">Methods</span></span>  
  
|<span data-ttu-id="5e0da-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-106">Method</span></span>|<span data-ttu-id="5e0da-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5e0da-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e0da-108">Attach, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="5e0da-109">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="5e0da-110">EnumerateAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="5e0da-111">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="5e0da-112">EnumerateBreakpoints, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="5e0da-113">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="5e0da-114">EnumerateSteppers, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="5e0da-115">Pobiera moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="5e0da-116">GetId, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="5e0da-117">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="5e0da-118">GetModuleFromMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="5e0da-119">Pobiera obiekt icordebugmodule — interfejs określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="5e0da-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="5e0da-120">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="5e0da-121">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="5e0da-122">GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="5e0da-123">Pobiera wskaźnik interfejsu do typowych domeny aplikacji języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5e0da-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="5e0da-124">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="5e0da-125">Pobiera proces zawierający domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="5e0da-126">IsAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="5e0da-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="5e0da-127">Określa, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0da-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e0da-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e0da-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e0da-129">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="5e0da-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e0da-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e0da-130">Requirements</span></span>  
 <span data-ttu-id="5e0da-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e0da-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e0da-132">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e0da-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e0da-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e0da-133">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5e0da-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5e0da-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e0da-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e0da-135">See also</span></span>

- [<span data-ttu-id="5e0da-136">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5e0da-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
