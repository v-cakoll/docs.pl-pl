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
ms.openlocfilehash: a06d57348cfbdfb8bb57580a48e54e298e27e166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="05a4d-102">ICorRuntimeHost::CreateEvidence — Metoda</span><span class="sxs-lookup"><span data-stu-id="05a4d-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="05a4d-103">Pobiera wskaźnika interfejsu typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, dzięki czemu hosta utworzyć dowodów zabezpieczeń do przekazania do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="05a4d-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a4d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05a4d-104">Syntax</span></span>  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05a4d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05a4d-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="05a4d-106">[out] Wskaźnik interfejsu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> wystąpienia używany do tworzenia dowodów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="05a4d-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="05a4d-107">Ten wskaźnik jest typu `IUnknown`, dlatego zazwyczaj powinny wywoływać elementy wywołujące `QueryInterface` w tym interfejsie uzyskać wskaźnik do <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05a4d-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05a4d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="05a4d-108">Return Value</span></span>  
  
|<span data-ttu-id="05a4d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05a4d-109">HRESULT</span></span>|<span data-ttu-id="05a4d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="05a4d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05a4d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="05a4d-111">S_OK</span></span>|<span data-ttu-id="05a4d-112">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="05a4d-112">The operation was successful.</span></span>|  
|<span data-ttu-id="05a4d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="05a4d-113">S_FALSE</span></span>|<span data-ttu-id="05a4d-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="05a4d-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="05a4d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05a4d-115">E_FAIL</span></span>|<span data-ttu-id="05a4d-116">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="05a4d-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="05a4d-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="05a4d-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="05a4d-118">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="05a4d-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="05a4d-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05a4d-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05a4d-120">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="05a4d-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05a4d-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05a4d-121">Remarks</span></span>  
 <span data-ttu-id="05a4d-122">Ta metoda zwraca pustą kolekcję, która nie można wypełnić z kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="05a4d-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="05a4d-123">Należy używać <xref:System.Security.Policy.Evidence> metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="05a4d-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05a4d-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05a4d-124">Requirements</span></span>  
 <span data-ttu-id="05a4d-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a4d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a4d-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05a4d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05a4d-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05a4d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05a4d-128">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="05a4d-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a4d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05a4d-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="05a4d-130">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="05a4d-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
