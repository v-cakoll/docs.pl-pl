---
title: "ICLRRuntimeHost — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost
helpviewer_keywords: ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type: apiref
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 332db2680ca23f34893a6c50c5311d73838bc1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="93b88-102">ICLRRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93b88-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="93b88-103">Zapewnia funkcje podobne do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interfejs dostarczony w programie .NET Framework w wersji 1, z następującymi zmianami:</span><span class="sxs-lookup"><span data-stu-id="93b88-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
-   <span data-ttu-id="93b88-104">Dodanie [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) metodę, aby ustawić interfejsu kontroli hosta.</span><span class="sxs-lookup"><span data-stu-id="93b88-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
-   <span data-ttu-id="93b88-105">Pominięcie niektórych metod dostarczonych przez `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="93b88-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93b88-106">Metody</span><span class="sxs-lookup"><span data-stu-id="93b88-106">Methods</span></span>  
  
|<span data-ttu-id="93b88-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-107">Method</span></span>|<span data-ttu-id="93b88-108">Opis</span><span class="sxs-lookup"><span data-stu-id="93b88-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93b88-109">ExecuteApplication — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="93b88-110">Używane w na podstawie manifestu scenariuszy wdrażania ClickOnce do określenia aplikacji do aktywacji w nowej domenie.</span><span class="sxs-lookup"><span data-stu-id="93b88-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="93b88-111">ExecuteInAppDomain — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="93b88-112">Określa <xref:System.AppDomain> polegający na wykonanie określonego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="93b88-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="93b88-113">ExecuteInDefaultAppDomain — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="93b88-114">Wywołuje określoną metodę określonego typu w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="93b88-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="93b88-115">GetCLRControl — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="93b88-116">Pobiera wskaźnika interfejsu typu [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) hostów może być dostosowanie właściwości środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="93b88-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="93b88-117">GetCurrentAppDomainId — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="93b88-118">Pobiera identyfikator numeryczny z <xref:System.AppDomain> który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="93b88-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="93b88-119">SetHostControl — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="93b88-120">Ustawia interfejs kontroli hosta.</span><span class="sxs-lookup"><span data-stu-id="93b88-120">Sets the host control interface.</span></span> <span data-ttu-id="93b88-121">Należy wywołać `SetHostControl` przed wywołaniem `Start`.</span><span class="sxs-lookup"><span data-stu-id="93b88-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="93b88-122">Start — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="93b88-123">Inicjuje środowisko CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="93b88-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="93b88-124">Stop — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="93b88-125">Zatrzymuje wykonywanie kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="93b88-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="93b88-126">UnloadAppDomain — metoda</span><span class="sxs-lookup"><span data-stu-id="93b88-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="93b88-127">Zwalnia <xref:System.AppDomain> odpowiadający określony identyfikator numeryczny.</span><span class="sxs-lookup"><span data-stu-id="93b88-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93b88-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93b88-128">Remarks</span></span>  
 <span data-ttu-id="93b88-129">Począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], użyj [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interfejsu otrzymywać wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, a następnie wywołać [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodę, aby otrzymywać wskaźnik do `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="93b88-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="93b88-130">We wcześniejszych wersjach programu .NET Framework, host pobiera wskaźnik do `ICLRRuntimeHost` wystąpienia przez wywołanie metody [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="93b88-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="93b88-131">Aby zapewnić wdrożeń technologii w .NET Framework w wersji 2.0, należy użyć `ICLRRuntimeHost` zamiast `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="93b88-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93b88-132">Nie wywołuj [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda przed wywołaniem [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metodę, aby aktywować manifest aplikacji.</span><span class="sxs-lookup"><span data-stu-id="93b88-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="93b88-133">Jeśli `Start` metoda jest wywoływana po pierwsze, `ExecuteApplication` wywołanie metody zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="93b88-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b88-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93b88-134">Requirements</span></span>  
 <span data-ttu-id="93b88-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93b88-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b88-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93b88-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93b88-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93b88-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93b88-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b88-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b88-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93b88-139">See Also</span></span>  
 [<span data-ttu-id="93b88-140">CorBindToCurrentRuntime — funkcja</span><span class="sxs-lookup"><span data-stu-id="93b88-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="93b88-141">CorBindToRuntimeEx — funkcja</span><span class="sxs-lookup"><span data-stu-id="93b88-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="93b88-142">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="93b88-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="93b88-143">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="93b88-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="93b88-144">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="93b88-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="93b88-145">CLRRuntimeHost — klasa Coclass</span><span class="sxs-lookup"><span data-stu-id="93b88-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
