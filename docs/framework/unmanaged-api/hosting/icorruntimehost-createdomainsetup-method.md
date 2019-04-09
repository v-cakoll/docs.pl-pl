---
title: ICorRuntimeHost::CreateDomainSetup — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f5de9882f8a029769d0ccbdac21aec541582a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157368"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="b4895-102">ICorRuntimeHost::CreateDomainSetup — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4895-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="b4895-103">Pobiera typ wskaźnika interfejsu iappdomainsetup — aby <xref:System.AppDomainSetup?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b4895-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> `IAppDomainSetup` <span data-ttu-id="b4895-104">udostępnia metody umożliwiające konfigurowanie aspektów domeny aplikacji, zanim zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="b4895-104">provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4895-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4895-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4895-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4895-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="b4895-107">[out] Wskaźnik interfejsu do <xref:System.AppDomainSetup?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b4895-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="b4895-108">Ten parametr jest wpisana jako `IUnknown`, więc obiekty wywołujące zwykle powinny wywoływać `QueryInterface` tego wskaźnika można uzyskać wskaźnika interfejsu typu `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="b4895-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4895-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b4895-109">Return Value</span></span>  
  
|<span data-ttu-id="b4895-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4895-110">HRESULT</span></span>|<span data-ttu-id="b4895-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b4895-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4895-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4895-112">S_OK</span></span>|<span data-ttu-id="b4895-113">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b4895-113">The operation was successful.</span></span>|  
|<span data-ttu-id="b4895-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b4895-114">S_FALSE</span></span>|<span data-ttu-id="b4895-115">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="b4895-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b4895-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4895-116">E_FAIL</span></span>|<span data-ttu-id="b4895-117">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="b4895-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b4895-118">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="b4895-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b4895-119">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b4895-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b4895-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4895-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4895-121">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b4895-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4895-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4895-122">Remarks</span></span>  
 <span data-ttu-id="b4895-123">Wskaźnik zwrócone w wyniku tej metody zwykle jest przekazywany jako parametr do [createdomainex —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b4895-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4895-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4895-124">Requirements</span></span>  
 <span data-ttu-id="b4895-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4895-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4895-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4895-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4895-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4895-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4895-128">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b4895-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4895-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4895-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="b4895-130">ICorRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b4895-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
