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
ms.openlocfilehash: ba02373aae33baf77b72323fabf1f6ca1fe4eecf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490244"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="40348-102">ICLRRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40348-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="40348-103">Oferuje funkcje podobne do tego elementu [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interfejsu podany w .NET Framework w wersji 1, z następującymi zmianami:</span><span class="sxs-lookup"><span data-stu-id="40348-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="40348-104">Dodanie [sethostcontrol —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) metodę, aby ustawić interfejs kontrolki hosta.</span><span class="sxs-lookup"><span data-stu-id="40348-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="40348-105">Pominięcie niektórych metod dostarczonych przez `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="40348-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40348-106">Metody</span><span class="sxs-lookup"><span data-stu-id="40348-106">Methods</span></span>  
  
|<span data-ttu-id="40348-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="40348-107">Method</span></span>|<span data-ttu-id="40348-108">Opis</span><span class="sxs-lookup"><span data-stu-id="40348-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40348-109">ExecuteApplication, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="40348-110">Używane w oparte na manifeście scenariusze wdrażania technologii ClickOnce do określenia aplikacji zostanie uaktywniony w nowej domenie.</span><span class="sxs-lookup"><span data-stu-id="40348-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="40348-111">ExecuteInAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="40348-112">Określa <xref:System.AppDomain> w którym można wykonać określonego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="40348-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="40348-113">ExecuteInDefaultAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="40348-114">Wywołuje określoną metodę określonego typu w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="40348-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="40348-115">GetCLRControl, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="40348-116">Pobiera wskaźnik interfejsu typu [iclrcontrol —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) czy hostów można użyć do dostosowania aspektów środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="40348-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="40348-117">GetCurrentAppDomainId, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="40348-118">Pobiera identyfikator liczbowy z <xref:System.AppDomain> obecnie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="40348-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="40348-119">SetHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="40348-120">Ustawia interfejs kontrolki hosta.</span><span class="sxs-lookup"><span data-stu-id="40348-120">Sets the host control interface.</span></span> <span data-ttu-id="40348-121">Należy wywołać `SetHostControl` przed wywołaniem `Start`.</span><span class="sxs-lookup"><span data-stu-id="40348-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="40348-122">Start, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="40348-123">Inicjuje środowisko CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="40348-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="40348-124">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="40348-125">Zatrzymuje wykonywanie kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40348-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="40348-126">UnloadAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="40348-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="40348-127">Zwalnia <xref:System.AppDomain> , który odpowiada określony identyfikator liczbowy.</span><span class="sxs-lookup"><span data-stu-id="40348-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40348-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40348-128">Remarks</span></span>  
 <span data-ttu-id="40348-129">Począwszy od programu .NET Framework 4, użyj [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interfejsu, aby uzyskać wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu, a następnie wywołaj [iclrruntimeinfo::getinterface —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)metodę, aby uzyskać wskaźnik do `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="40348-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="40348-130">We wcześniejszych wersjach programu .NET Framework, host pobiera wskaźnik do `ICLRRuntimeHost` wystąpienia, wywołując [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="40348-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="40348-131">Aby zapewnić implementacje technologii dostarczanych w .NET Framework w wersji 2.0, należy użyć `ICLRRuntimeHost` zamiast `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="40348-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="40348-132">Nie wywołuj [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda przed wywołaniem [executeapplication —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metodę, aby aktywować manifestu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40348-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="40348-133">Jeśli `Start` najpierw jest wywoływana metoda `ExecuteApplication` wywołania metody zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="40348-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40348-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40348-134">Requirements</span></span>  
 <span data-ttu-id="40348-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40348-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40348-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40348-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40348-137">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40348-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40348-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40348-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40348-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40348-139">See also</span></span>

- [<span data-ttu-id="40348-140">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="40348-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="40348-141">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="40348-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="40348-142">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="40348-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="40348-143">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="40348-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="40348-144">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="40348-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="40348-145">CLRRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="40348-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
