---
title: ICorRuntimeHost::NextDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f8e9c91ddddd0e0b14c79bef86c7665ff4e3dcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723324"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="f0555-102">ICorRuntimeHost::NextDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0555-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="f0555-103">Pobiera wskaźnik interfejsu do następnej domeny w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="f0555-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0555-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0555-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0555-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0555-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f0555-106">[in] Moduł wyliczający, który został uzyskany za pomocą wywołania [enumdomains —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="f0555-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f0555-107">[out] Wskaźnik interfejsu do <xref:System._AppDomain?displayProperty=nameWithType> typ, który reprezentuje następnej domeny w wyliczenia lub wartość null, jeśli istnieje żadnych więcej domen.</span><span class="sxs-lookup"><span data-stu-id="f0555-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0555-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f0555-108">Return Value</span></span>  
  
|<span data-ttu-id="f0555-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0555-109">HRESULT</span></span>|<span data-ttu-id="f0555-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f0555-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0555-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0555-111">S_OK</span></span>|<span data-ttu-id="f0555-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f0555-112">The operation was successful.</span></span>|  
|<span data-ttu-id="f0555-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f0555-113">S_FALSE</span></span>|<span data-ttu-id="f0555-114">Nie można ukończyć operacji, lub nie istnieją więcej domeny w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="f0555-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="f0555-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0555-115">E_FAIL</span></span>|<span data-ttu-id="f0555-116">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="f0555-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="f0555-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="f0555-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="f0555-118">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f0555-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f0555-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0555-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0555-120">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f0555-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0555-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0555-121">Requirements</span></span>  
 <span data-ttu-id="f0555-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0555-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0555-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0555-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0555-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0555-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0555-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f0555-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0555-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0555-126">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="f0555-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0555-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
