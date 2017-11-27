---
title: "ICorRuntimeHost::CreateDomainSetup — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca09788ea403e2a60d6de0cb6834fdc90261b770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="3386a-102">ICorRuntimeHost::CreateDomainSetup — Metoda</span><span class="sxs-lookup"><span data-stu-id="3386a-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="3386a-103">Pobiera typ wskaźnika interfejsu z IAppDomainSetup do <xref:System.AppDomainSetup?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3386a-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="3386a-104">`IAppDomainSetup`udostępnia metody, aby skonfigurować aspektów domeny aplikacji, zanim zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="3386a-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3386a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3386a-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3386a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3386a-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="3386a-107">[out] Wskaźnik interfejsu do <xref:System.AppDomainSetup?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3386a-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="3386a-108">Ten parametr jest typu `IUnknown`, dlatego zazwyczaj powinny wywoływać elementy wywołujące `QueryInterface` na wskaźnik do uzyskania wskaźnika interfejsu typu `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="3386a-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3386a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3386a-109">Return Value</span></span>  
  
|<span data-ttu-id="3386a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3386a-110">HRESULT</span></span>|<span data-ttu-id="3386a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3386a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3386a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3386a-112">S_OK</span></span>|<span data-ttu-id="3386a-113">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="3386a-113">The operation was successful.</span></span>|  
|<span data-ttu-id="3386a-114">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3386a-114">S_FALSE</span></span>|<span data-ttu-id="3386a-115">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="3386a-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="3386a-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3386a-116">E_FAIL</span></span>|<span data-ttu-id="3386a-117">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="3386a-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3386a-118">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="3386a-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="3386a-119">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3386a-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3386a-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3386a-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3386a-121">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3386a-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3386a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3386a-122">Remarks</span></span>  
 <span data-ttu-id="3386a-123">Wskaźnik zwracane z tej metody jest zwykle przekazywana jako parametr [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3386a-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3386a-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3386a-124">Requirements</span></span>  
 <span data-ttu-id="3386a-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3386a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3386a-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3386a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3386a-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3386a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3386a-128">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="3386a-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3386a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3386a-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="3386a-130">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="3386a-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
