---
title: ICorDebugAppDomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aab18cb1d29931a58e64561f23d91ee4eb3a4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="f0817-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="f0817-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="f0817-103">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="f0817-104">Ten interfejs jest podklasą klasy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="f0817-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0817-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f0817-105">Methods</span></span>  
  
|<span data-ttu-id="f0817-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-106">Method</span></span>|<span data-ttu-id="f0817-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f0817-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0817-108">Attach, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="f0817-109">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="f0817-110">EnumerateAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="f0817-111">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="f0817-112">EnumerateBreakpoints, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="f0817-113">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="f0817-114">EnumerateSteppers, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="f0817-115">Pobiera moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="f0817-116">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="f0817-117">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="f0817-118">GetModuleFromMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="f0817-119">Pobiera obiekt ICorDebugModule z interfejsem określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="f0817-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="f0817-120">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="f0817-121">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="f0817-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="f0817-123">Pobiera wskaźnika interfejsu do typowych domeny aplikacji języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f0817-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="f0817-124">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="f0817-125">Pobiera proces zawierający domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="f0817-126">IsAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="f0817-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="f0817-127">Określa, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0817-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0817-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0817-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0817-129">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="f0817-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0817-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0817-130">Requirements</span></span>  
 <span data-ttu-id="f0817-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0817-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0817-132">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0817-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0817-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0817-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0817-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0817-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0817-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0817-135">See Also</span></span>  
 [<span data-ttu-id="f0817-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0817-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
