---
title: "ICorRuntimeHost — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1280c49c2eea6a06eca10ebd8896b0722e321547
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="32a6d-102">ICorRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="32a6d-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="32a6d-103">Udostępnia metody umożliwiające hosta go uruchamiać i zatrzymywać środowisko uruchomieniowe języka wspólnego (CLR) jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkie domeny uruchomionych w procesie.</span><span class="sxs-lookup"><span data-stu-id="32a6d-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="32a6d-104">W programie .NET Framework w wersji 2.0, ten interfejs jest zastąpiona [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).</span><span class="sxs-lookup"><span data-stu-id="32a6d-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32a6d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="32a6d-105">Methods</span></span>  
  
|<span data-ttu-id="32a6d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-106">Method</span></span>|<span data-ttu-id="32a6d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="32a6d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32a6d-108">CloseEnum, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-108">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|<span data-ttu-id="32a6d-109">Resetuje wyliczający domeny na początku listy domen.</span><span class="sxs-lookup"><span data-stu-id="32a6d-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="32a6d-110">CreateDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-110">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|<span data-ttu-id="32a6d-111">Tworzy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32a6d-111">Creates an application domain.</span></span> <span data-ttu-id="32a6d-112">Obiekt wywołujący uzyskuje wskaźnika interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="32a6d-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="32a6d-113">CreateDomainEx, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-113">CreateDomainEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|<span data-ttu-id="32a6d-114">Tworzy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32a6d-114">Creates an application domain.</span></span> <span data-ttu-id="32a6d-115">Ta metoda umożliwia obiekt wywołujący, aby przekazać wystąpienia IAppDomainSetup Konfigurowanie dodatkowych funkcji zwracana <xref:System._AppDomain> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="32a6d-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="32a6d-116">CreateDomainSetup, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-116">CreateDomainSetup Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="32a6d-117">Pobiera wskaźnika interfejsu typu `IAppDomainSetup` do <xref:System.AppDomainSetup> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="32a6d-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="32a6d-118">`IAppDomainSetup`udostępnia metody, aby skonfigurować aspektów domeny aplikacji, zanim zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="32a6d-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="32a6d-119">CreateEvidence, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-119">CreateEvidence Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|<span data-ttu-id="32a6d-120">Pobiera wskaźnika interfejsu typu <xref:System.Security.Principal.IIdentity>, dzięki czemu hosta utworzyć dowodów zabezpieczeń do przekazania do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).</span><span class="sxs-lookup"><span data-stu-id="32a6d-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="32a6d-121">CreateLogicalThreadState, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-121">CreateLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="32a6d-122">Nie używać.</span><span class="sxs-lookup"><span data-stu-id="32a6d-122">Do not use.</span></span>|  
|[<span data-ttu-id="32a6d-123">CurrentDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-123">CurrentDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|<span data-ttu-id="32a6d-124">Pobiera wskaźnika interfejsu typu <xref:System._AppDomain> reprezentujący domeny załadowany w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="32a6d-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="32a6d-125">DeleteLogicalThreadState, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-125">DeleteLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="32a6d-126">Nie używać.</span><span class="sxs-lookup"><span data-stu-id="32a6d-126">Do not use.</span></span>|  
|[<span data-ttu-id="32a6d-127">EnumDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-127">EnumDomains Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|<span data-ttu-id="32a6d-128">Pobiera moduł wyliczający dla domen w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="32a6d-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="32a6d-129">GetConfiguration, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-129">GetConfiguration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="32a6d-130">Pobiera obiekt, który umożliwia hosta do określenia konfiguracji wywołanie zwrotne środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="32a6d-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="32a6d-131">GetDefaultDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-131">GetDefaultDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="32a6d-132">Pobiera wskaźnika interfejsu typu <xref:System._AppDomain> reprezentujący domenę domyślną dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="32a6d-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="32a6d-133">LocksHeldByLogicalThread, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-133">LocksHeldByLogicalThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="32a6d-134">Nie używać.</span><span class="sxs-lookup"><span data-stu-id="32a6d-134">Do not use.</span></span>|  
|[<span data-ttu-id="32a6d-135">MapFile, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-135">MapFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|<span data-ttu-id="32a6d-136">Mapuje określony plik do pamięci.</span><span class="sxs-lookup"><span data-stu-id="32a6d-136">Maps the specified file into memory.</span></span> <span data-ttu-id="32a6d-137">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="32a6d-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="32a6d-138">NextDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-138">NextDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|<span data-ttu-id="32a6d-139">Pobiera wskaźnika interfejsu do następnej domeny w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="32a6d-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="32a6d-140">Start, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-140">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|<span data-ttu-id="32a6d-141">Uruchamia środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="32a6d-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="32a6d-142">Stop, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-142">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|<span data-ttu-id="32a6d-143">Zatrzymuje wykonywanie kodu w czasie wykonywania dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="32a6d-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="32a6d-144">SwitchInLogicalThreadState, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-144">SwitchInLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="32a6d-145">Nie używać.</span><span class="sxs-lookup"><span data-stu-id="32a6d-145">Do not use.</span></span>|  
|[<span data-ttu-id="32a6d-146">SwitchOutLogicalThreadState, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-146">SwitchOutLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="32a6d-147">Nie używać.</span><span class="sxs-lookup"><span data-stu-id="32a6d-147">Do not use.</span></span>|  
|[<span data-ttu-id="32a6d-148">UnloadDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="32a6d-148">UnloadDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="32a6d-149">Zwalnia domeny określonej aplikacji w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="32a6d-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32a6d-150">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32a6d-150">Requirements</span></span>  
 <span data-ttu-id="32a6d-151">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a6d-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a6d-152">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32a6d-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32a6d-153">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32a6d-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32a6d-154">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="32a6d-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a6d-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32a6d-155">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="32a6d-156">Hosting</span><span class="sxs-lookup"><span data-stu-id="32a6d-156">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="32a6d-157">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="32a6d-157">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="32a6d-158">Hosty w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="32a6d-158">Runtime Hosts</span></span>](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [<span data-ttu-id="32a6d-159">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="32a6d-159">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="32a6d-160">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="32a6d-160">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
