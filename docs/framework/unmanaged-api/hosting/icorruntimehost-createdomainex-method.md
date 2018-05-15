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
ms.openlocfilehash: 2e851cf16e4b23b1f8510c4d96b23c01eb726a77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="fe5c7-102">ICorRuntimeHost::CreateDomainEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe5c7-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="fe5c7-103">Tworzy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-103">Creates an application domain.</span></span> <span data-ttu-id="fe5c7-104">Obiekt wywołujący uzyskuje wskaźnika interfejsu typu <xref:System._AppDomain>, aby wystąpienie typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe5c7-105">Ta metoda umożliwia obiekt wywołujący, aby przekazać wystąpienia IAppDomainSetup Konfigurowanie dodatkowych funkcji zwracana <xref:System._AppDomain> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5c7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe5c7-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe5c7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe5c7-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="fe5c7-108">[in] Parametr opcjonalny używany do nadaj przyjazną nazwę do domeny.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="fe5c7-109">Przyjazna nazwa mogą być wyświetlane w interfejsów użytkownika, takich jak debugera, aby zidentyfikować domenę.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="fe5c7-110">[in] Wskaźnik interfejsu opcjonalne typu `IAppDomainSetup`, uzyskany przez wywołanie do [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="fe5c7-111">[in] Opcjonalne tablicy wskaźników do `IIdentity` wystąpień, które reprezentują dowód mapowany za pomocą zasad zabezpieczeń do ustalenia zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="fe5c7-112">`IIdentity` Obiektu można uzyskać przez wywołanie metody [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="fe5c7-113">[out] Wskaźnik interfejsu typu <xref:System._AppDomain> na wystąpienie <xref:System.AppDomain?displayProperty=nameWithType> można dodatkowo kontrolować domeny.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe5c7-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fe5c7-114">Return Value</span></span>  
  
|<span data-ttu-id="fe5c7-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe5c7-115">HRESULT</span></span>|<span data-ttu-id="fe5c7-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fe5c7-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe5c7-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe5c7-117">S_OK</span></span>|<span data-ttu-id="fe5c7-118">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-118">The operation was successful.</span></span>|  
|<span data-ttu-id="fe5c7-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fe5c7-119">S_FALSE</span></span>|<span data-ttu-id="fe5c7-120">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="fe5c7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe5c7-121">E_FAIL</span></span>|<span data-ttu-id="fe5c7-122">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="fe5c7-123">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="fe5c7-124">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fe5c7-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe5c7-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe5c7-126">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe5c7-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe5c7-127">Remarks</span></span>  
 <span data-ttu-id="fe5c7-128">`CreateDomainEx` Rozszerza możliwości [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) przez obiekt wywołujący, aby przekazać `IAppDomainSetup` wystąpienia o wartości właściwości do konfigurowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe5c7-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe5c7-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe5c7-129">Requirements</span></span>  
 <span data-ttu-id="fe5c7-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5c7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5c7-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe5c7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe5c7-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe5c7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe5c7-133">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="fe5c7-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5c7-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe5c7-134">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="fe5c7-135">CreateDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="fe5c7-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [<span data-ttu-id="fe5c7-136">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe5c7-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
