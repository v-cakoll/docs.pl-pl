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
ms.openlocfilehash: 4a91f57126c0cf2074bd086ddb2fb4cd9e0716d4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762321"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="7fe6d-102">ICorRuntimeHost::CreateEvidence — Metoda</span><span class="sxs-lookup"><span data-stu-id="7fe6d-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="7fe6d-103">Pobiera wskaźnik interfejsu typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , który umożliwia hostowi tworzenie dowodu bezpieczeństwa do przekazania do metody [ondomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [CreateDomainEx —](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7fe6d-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fe6d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fe6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fe6d-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="7fe6d-106">określoną Wskaźnik interfejsu do <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> wystąpienia użytego do utworzenia dowodu bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="7fe6d-107">Ten wskaźnik jest wpisywany `IUnknown` , dlatego obiekty wywołujące powinny zwykle wywołać `QueryInterface` na tym interfejsie, aby uzyskać wskaźnik do <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7fe6d-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fe6d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7fe6d-108">Return Value</span></span>  
  
|<span data-ttu-id="7fe6d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fe6d-109">HRESULT</span></span>|<span data-ttu-id="7fe6d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7fe6d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fe6d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fe6d-111">S_OK</span></span>|<span data-ttu-id="7fe6d-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-112">The operation was successful.</span></span>|  
|<span data-ttu-id="7fe6d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7fe6d-113">S_FALSE</span></span>|<span data-ttu-id="7fe6d-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="7fe6d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7fe6d-115">E_FAIL</span></span>|<span data-ttu-id="7fe6d-116">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="7fe6d-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="7fe6d-118">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7fe6d-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7fe6d-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7fe6d-120">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe6d-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fe6d-121">Remarks</span></span>  
 <span data-ttu-id="7fe6d-122">Ta metoda zwraca pustą kolekcję, której nie można wypełnić z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="7fe6d-123">Zamiast tego należy użyć <xref:System.Security.Policy.Evidence> metody.</span><span class="sxs-lookup"><span data-stu-id="7fe6d-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fe6d-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fe6d-124">Requirements</span></span>  
 <span data-ttu-id="7fe6d-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fe6d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe6d-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7fe6d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fe6d-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7fe6d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fe6d-128">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="7fe6d-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe6d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fe6d-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="7fe6d-130">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="7fe6d-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
