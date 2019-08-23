---
title: ICLRRuntimeHost — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f159c0b57f2087b608fac8cbc9b9c64ceb063a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965992"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="41b28-102">ICLRRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41b28-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="41b28-103">Zapewnia funkcjonalność podobną do interfejsu [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) dostępnego w .NET Framework wersja 1 z następującymi zmianami:</span><span class="sxs-lookup"><span data-stu-id="41b28-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="41b28-104">Dodanie metody [SetHostControl —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) w celu ustawienia interfejsu sterowania hosta.</span><span class="sxs-lookup"><span data-stu-id="41b28-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="41b28-105">Pominięcie niektórych metod dostarczonych przez `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="41b28-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41b28-106">Metody</span><span class="sxs-lookup"><span data-stu-id="41b28-106">Methods</span></span>  
  
|<span data-ttu-id="41b28-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-107">Method</span></span>|<span data-ttu-id="41b28-108">Opis</span><span class="sxs-lookup"><span data-stu-id="41b28-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41b28-109">ExecuteApplication, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="41b28-110">Używany w scenariuszach wdrażania ClickOnce opartych na manifestach, aby określić aplikację, która ma zostać aktywowana w nowej domenie.</span><span class="sxs-lookup"><span data-stu-id="41b28-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="41b28-111">ExecuteInAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="41b28-112">Określa, <xref:System.AppDomain> w którym ma zostać wykonany określony kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="41b28-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="41b28-113">ExecuteInDefaultAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="41b28-114">Wywołuje określoną metodę określonego typu w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="41b28-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="41b28-115">GetCLRControl, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="41b28-116">Pobiera wskaźnik interfejsu typu [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , którego mogą używać hosty do dostosowywania aspektów środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="41b28-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="41b28-117">GetCurrentAppDomainId, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="41b28-118">Pobiera liczbowy identyfikator <xref:System.AppDomain> , który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="41b28-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="41b28-119">SetHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="41b28-120">Ustawia interfejs sterowania hosta.</span><span class="sxs-lookup"><span data-stu-id="41b28-120">Sets the host control interface.</span></span> <span data-ttu-id="41b28-121">Przed wywołaniem `SetHostControl` `Start`należy wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="41b28-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="41b28-122">Start, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="41b28-123">Inicjuje środowisko CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="41b28-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="41b28-124">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="41b28-125">Kończy wykonywanie kodu przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="41b28-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="41b28-126">UnloadAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="41b28-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="41b28-127">Zwalnia <xref:System.AppDomain> dane odnoszące się do określonego identyfikatora liczbowego.</span><span class="sxs-lookup"><span data-stu-id="41b28-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41b28-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41b28-128">Remarks</span></span>  
 <span data-ttu-id="41b28-129">Rozpoczynając od .NET Framework 4, użyj interfejsu [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) , aby uzyskać wskaźnik do interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , a następnie Wywołaj metodę [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) , aby uzyskać wskaźnik do `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="41b28-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="41b28-130">We wcześniejszych wersjach .NET Framework Host Pobiera wskaźnik do `ICLRRuntimeHost` wystąpienia przez wywołanie [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="41b28-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="41b28-131">Aby zapewnić implementację dowolnej z technologii zapewnianych w .NET Framework w wersji 2,0, należy użyć `ICLRRuntimeHost` `ICorRuntimeHost`zamiast.</span><span class="sxs-lookup"><span data-stu-id="41b28-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="41b28-132">Nie wywołuj metody [startowej](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) przed wywołaniem metody [ExecuteApplication —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) w celu aktywowania aplikacji opartej na manifeście.</span><span class="sxs-lookup"><span data-stu-id="41b28-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="41b28-133">Jeśli metoda jest wywoływana jako pierwsza `ExecuteApplication` , wywołanie metody zakończy się niepowodzeniem. `Start`</span><span class="sxs-lookup"><span data-stu-id="41b28-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b28-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41b28-134">Requirements</span></span>  
 <span data-ttu-id="41b28-135">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41b28-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b28-136">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41b28-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41b28-137">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41b28-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41b28-138">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41b28-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b28-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b28-139">See also</span></span>

- [<span data-ttu-id="41b28-140">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="41b28-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="41b28-141">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="41b28-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="41b28-142">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="41b28-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="41b28-143">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="41b28-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="41b28-144">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="41b28-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="41b28-145">CLRRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="41b28-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
