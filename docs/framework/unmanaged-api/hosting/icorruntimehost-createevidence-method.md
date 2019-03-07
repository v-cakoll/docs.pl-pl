---
title: ICorRuntimeHost::CreateEvidence — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54c21008e5922a5357f503821d87e297f0d00e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499254"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="8394c-102">ICorRuntimeHost::CreateEvidence — Metoda</span><span class="sxs-lookup"><span data-stu-id="8394c-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="8394c-103">Pobiera wskaźnik interfejsu typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, co pozwala hosta utworzyć dowodów zabezpieczeń do przekazania do [createdomain —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [createdomainex —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8394c-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8394c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8394c-104">Syntax</span></span>  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8394c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8394c-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="8394c-106">[out] Wskaźnik interfejsu do <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> wystąpienia użyty do utworzenia dowodów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8394c-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="8394c-107">This, wskaźnik jest wpisane `IUnknown`, więc obiekty wywołujące zwykle powinny wywoływać `QueryInterface` na wskaźnik do tego interfejsu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8394c-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8394c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8394c-108">Return Value</span></span>  
  
|<span data-ttu-id="8394c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8394c-109">HRESULT</span></span>|<span data-ttu-id="8394c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8394c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8394c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8394c-111">S_OK</span></span>|<span data-ttu-id="8394c-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8394c-112">The operation was successful.</span></span>|  
|<span data-ttu-id="8394c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8394c-113">S_FALSE</span></span>|<span data-ttu-id="8394c-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="8394c-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8394c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8394c-115">E_FAIL</span></span>|<span data-ttu-id="8394c-116">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="8394c-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8394c-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="8394c-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8394c-118">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8394c-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8394c-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8394c-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8394c-120">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8394c-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8394c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8394c-121">Remarks</span></span>  
 <span data-ttu-id="8394c-122">Ta metoda zwraca pustą kolekcję, która nie można wypełnić z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="8394c-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="8394c-123">Należy używać <xref:System.Security.Policy.Evidence> metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="8394c-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8394c-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8394c-124">Requirements</span></span>  
 <span data-ttu-id="8394c-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8394c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8394c-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8394c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8394c-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8394c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8394c-128">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8394c-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8394c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8394c-129">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="8394c-130">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="8394c-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
