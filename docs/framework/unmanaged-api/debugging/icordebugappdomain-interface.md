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
ms.openlocfilehash: 19cf38920ed818dfbba9cd83bd64fdc408281e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="efae4-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="efae4-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="efae4-103">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="efae4-104">Ten interfejs jest podklasą klasy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="efae4-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efae4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="efae4-105">Methods</span></span>  
  
|<span data-ttu-id="efae4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-106">Method</span></span>|<span data-ttu-id="efae4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="efae4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efae4-108">Attach — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="efae4-109">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="efae4-110">EnumerateAssemblies — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="efae4-111">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="efae4-112">EnumerateBreakpoints — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="efae4-113">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="efae4-114">EnumerateSteppers — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="efae4-115">Pobiera moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="efae4-116">GetId — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="efae4-117">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="efae4-118">GetModuleFromMetaDataInterface — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="efae4-119">Pobiera obiekt ICorDebugModule z interfejsem określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="efae4-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="efae4-120">GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="efae4-121">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="efae4-122">GetObject — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="efae4-123">Pobiera wskaźnika interfejsu do typowych domeny aplikacji języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="efae4-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="efae4-124">GetProcess — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="efae4-125">Pobiera proces zawierający domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="efae4-126">IsAttached — metoda</span><span class="sxs-lookup"><span data-stu-id="efae4-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="efae4-127">Określa, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efae4-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efae4-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efae4-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efae4-129">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="efae4-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efae4-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efae4-130">Requirements</span></span>  
 <span data-ttu-id="efae4-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efae4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efae4-132">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efae4-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efae4-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efae4-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efae4-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efae4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efae4-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efae4-135">See Also</span></span>  
 [<span data-ttu-id="efae4-136">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="efae4-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
