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
ms.openlocfilehash: 2758deaabf9db1cbc5465eb9b5976add534e87b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469668"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="9d785-102">ICorRuntimeHost::CreateDomainSetup — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d785-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="9d785-103">Pobiera typ wskaźnika interfejsu iappdomainsetup — aby <xref:System.AppDomainSetup?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9d785-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="9d785-104">`IAppDomainSetup` udostępnia metody umożliwiające konfigurowanie aspektów domeny aplikacji, zanim zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="9d785-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d785-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d785-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d785-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d785-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="9d785-107">[out] Wskaźnik interfejsu do <xref:System.AppDomainSetup?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9d785-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="9d785-108">Ten parametr jest wpisana jako `IUnknown`, więc obiekty wywołujące zwykle powinny wywoływać `QueryInterface` tego wskaźnika można uzyskać wskaźnika interfejsu typu `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="9d785-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d785-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d785-109">Return Value</span></span>  
  
|<span data-ttu-id="9d785-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d785-110">HRESULT</span></span>|<span data-ttu-id="9d785-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9d785-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d785-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d785-112">S_OK</span></span>|<span data-ttu-id="9d785-113">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9d785-113">The operation was successful.</span></span>|  
|<span data-ttu-id="9d785-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9d785-114">S_FALSE</span></span>|<span data-ttu-id="9d785-115">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="9d785-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9d785-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d785-116">E_FAIL</span></span>|<span data-ttu-id="9d785-117">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="9d785-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9d785-118">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="9d785-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9d785-119">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d785-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d785-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d785-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d785-121">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9d785-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d785-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d785-122">Remarks</span></span>  
 <span data-ttu-id="9d785-123">Wskaźnik zwrócone w wyniku tej metody zwykle jest przekazywany jako parametr do [createdomainex —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9d785-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d785-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d785-124">Requirements</span></span>  
 <span data-ttu-id="9d785-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d785-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d785-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d785-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d785-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d785-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d785-128">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9d785-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d785-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d785-129">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="9d785-130">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d785-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
