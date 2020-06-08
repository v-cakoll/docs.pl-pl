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
ms.openlocfilehash: 72caac0aafe7f9c5919057a6ad2565258aec6a50
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504085"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="1eadc-102">ICLRRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1eadc-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="1eadc-103">Zapewnia funkcjonalność podobną do interfejsu [ICorRuntimeHost](icorruntimehost-interface.md) dostępnego w .NET Framework wersja 1 z następującymi zmianami:</span><span class="sxs-lookup"><span data-stu-id="1eadc-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="1eadc-104">Dodanie metody [SetHostControl —](iclrruntimehost-sethostcontrol-method.md) w celu ustawienia interfejsu sterowania hosta.</span><span class="sxs-lookup"><span data-stu-id="1eadc-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="1eadc-105">Pominięcie niektórych metod dostarczonych przez `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="1eadc-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1eadc-106">Metody</span><span class="sxs-lookup"><span data-stu-id="1eadc-106">Methods</span></span>  
  
|<span data-ttu-id="1eadc-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-107">Method</span></span>|<span data-ttu-id="1eadc-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1eadc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1eadc-109">ExecuteApplication, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="1eadc-110">Używany w scenariuszach wdrażania ClickOnce opartych na manifestach, aby określić aplikację, która ma zostać aktywowana w nowej domenie.</span><span class="sxs-lookup"><span data-stu-id="1eadc-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="1eadc-111">ExecuteInAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="1eadc-112">Określa, <xref:System.AppDomain> w którym ma zostać wykonany określony kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="1eadc-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="1eadc-113">ExecuteInDefaultAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="1eadc-114">Wywołuje określoną metodę określonego typu w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1eadc-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="1eadc-115">GetCLRControl, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="1eadc-116">Pobiera wskaźnik interfejsu typu [ICLRControl](iclrcontrol-interface.md) , którego mogą używać hosty do dostosowywania aspektów środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1eadc-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="1eadc-117">GetCurrentAppDomainId, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="1eadc-118">Pobiera liczbowy identyfikator <xref:System.AppDomain> , który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="1eadc-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="1eadc-119">SetHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="1eadc-120">Ustawia interfejs sterowania hosta.</span><span class="sxs-lookup"><span data-stu-id="1eadc-120">Sets the host control interface.</span></span> <span data-ttu-id="1eadc-121">`SetHostControl`Przed wywołaniem należy wywołać metodę `Start` .</span><span class="sxs-lookup"><span data-stu-id="1eadc-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="1eadc-122">Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="1eadc-123">Inicjuje środowisko CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="1eadc-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="1eadc-124">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="1eadc-125">Kończy wykonywanie kodu przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="1eadc-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="1eadc-126">UnloadAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="1eadc-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="1eadc-127">Zwalnia dane <xref:System.AppDomain> odnoszące się do określonego identyfikatora liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1eadc-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eadc-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1eadc-128">Remarks</span></span>  
 <span data-ttu-id="1eadc-129">Rozpoczynając od .NET Framework 4, użyj interfejsu [ICLRMetaHost](iclrmetahost-interface.md) , aby uzyskać wskaźnik do interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , a następnie Wywołaj metodę [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) , aby uzyskać wskaźnik do `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="1eadc-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="1eadc-130">We wcześniejszych wersjach .NET Framework Host Pobiera wskaźnik do `ICLRRuntimeHost` wystąpienia przez wywołanie [CorBindToRuntimeEx](corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="1eadc-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="1eadc-131">Aby zapewnić implementację dowolnej z technologii zapewnianych w .NET Framework w wersji 2,0, należy użyć `ICLRRuntimeHost` zamiast `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="1eadc-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1eadc-132">Nie wywołuj metody [startowej](iclrruntimehost-start-method.md) przed wywołaniem metody [ExecuteApplication —](iclrruntimehost-executeapplication-method.md) w celu aktywowania aplikacji opartej na manifeście.</span><span class="sxs-lookup"><span data-stu-id="1eadc-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="1eadc-133">Jeśli `Start` Metoda jest wywoływana jako pierwsza, `ExecuteApplication` wywołanie metody zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1eadc-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eadc-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1eadc-134">Requirements</span></span>  
 <span data-ttu-id="1eadc-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eadc-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eadc-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1eadc-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1eadc-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1eadc-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1eadc-138">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eadc-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eadc-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1eadc-139">See also</span></span>

- [<span data-ttu-id="1eadc-140">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="1eadc-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="1eadc-141">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="1eadc-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="1eadc-142">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1eadc-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1eadc-143">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1eadc-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="1eadc-144">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1eadc-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="1eadc-145">CLRRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="1eadc-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
