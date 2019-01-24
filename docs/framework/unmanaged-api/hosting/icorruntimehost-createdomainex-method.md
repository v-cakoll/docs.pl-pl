---
title: ICorRuntimeHost::CreateDomainEx — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf8cb9382b2bbf10d02cf564ee51db626d81c6a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650629"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="88c11-102">ICorRuntimeHost::CreateDomainEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="88c11-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="88c11-103">Tworzy domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88c11-103">Creates an application domain.</span></span> <span data-ttu-id="88c11-104">Obiekt wywołujący odbierze wskaźnika interfejsu typu <xref:System._AppDomain>, do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88c11-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="88c11-105">Ta metoda umożliwia obiektowi wywołującemu Przekaż wystąpienie iappdomainsetup — Aby skonfigurować dodatkowe funkcje zwracanego <xref:System._AppDomain> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="88c11-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c11-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="88c11-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88c11-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="88c11-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="88c11-108">[in] Opcjonalny parametr umożliwia oferowanie przyjazną nazwę domeny.</span><span class="sxs-lookup"><span data-stu-id="88c11-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="88c11-109">Ta przyjazna nazwa może wyświetlana w interfejsie użytkownika, takich jak debugery do identyfikowania domeny.</span><span class="sxs-lookup"><span data-stu-id="88c11-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="88c11-110">[in] Opcjonalny interfejs wskaźnika typu `IAppDomainSetup`uzyskanej przez wywołanie [icorruntimehost::createdomainsetup —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="88c11-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="88c11-111">[in] Opcjonalną tablicę wskaźników do `IIdentity` wystąpień, które reprezentują dowód mapowany za pomocą zasad zabezpieczeń, aby ustanowić zestaw uprawnień.</span><span class="sxs-lookup"><span data-stu-id="88c11-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="88c11-112">`IIdentity` Obiektu można uzyskać przez wywołanie metody [createevidence —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="88c11-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="88c11-113">[out] Wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia <xref:System.AppDomain?displayProperty=nameWithType> można jeszcze bardziej kontrolować domeny.</span><span class="sxs-lookup"><span data-stu-id="88c11-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88c11-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="88c11-114">Return Value</span></span>  
  
|<span data-ttu-id="88c11-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88c11-115">HRESULT</span></span>|<span data-ttu-id="88c11-116">Opis</span><span class="sxs-lookup"><span data-stu-id="88c11-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88c11-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="88c11-117">S_OK</span></span>|<span data-ttu-id="88c11-118">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="88c11-118">The operation was successful.</span></span>|  
|<span data-ttu-id="88c11-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="88c11-119">S_FALSE</span></span>|<span data-ttu-id="88c11-120">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="88c11-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="88c11-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88c11-121">E_FAIL</span></span>|<span data-ttu-id="88c11-122">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="88c11-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="88c11-123">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="88c11-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="88c11-124">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="88c11-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="88c11-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88c11-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88c11-126">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="88c11-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88c11-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88c11-127">Remarks</span></span>  
 <span data-ttu-id="88c11-128">`CreateDomainEx` Rozszerza możliwości [createdomain —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) , umożliwiając obiekt wywołujący, aby przekazać `IAppDomainSetup` wystąpienie o wartości właściwości — konfigurowanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88c11-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88c11-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88c11-129">Requirements</span></span>  
 <span data-ttu-id="88c11-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88c11-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88c11-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88c11-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88c11-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88c11-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88c11-133">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="88c11-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c11-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88c11-134">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="88c11-135">CreateDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="88c11-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="88c11-136">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="88c11-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
