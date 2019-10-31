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
ms.openlocfilehash: 36eacedfb83c1248fc252091872bcfeecdbcd874
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139519"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="517fa-102">ICorRuntimeHost::NextDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="517fa-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="517fa-103">Pobiera wskaźnik interfejsu do następnej domeny w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="517fa-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="517fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="517fa-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="517fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="517fa-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="517fa-106">podczas Moduł wyliczający uzyskany za pomocą wywołania do [EnumDomains —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="517fa-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="517fa-107">określoną Wskaźnik interfejsu do typu <xref:System._AppDomain?displayProperty=nameWithType>, który reprezentuje następną domenę w wyliczeniu, lub wartość null, jeśli nie ma więcej domen.</span><span class="sxs-lookup"><span data-stu-id="517fa-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="517fa-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="517fa-108">Return Value</span></span>  
  
|<span data-ttu-id="517fa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="517fa-109">HRESULT</span></span>|<span data-ttu-id="517fa-110">Opis</span><span class="sxs-lookup"><span data-stu-id="517fa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="517fa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="517fa-111">S_OK</span></span>|<span data-ttu-id="517fa-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="517fa-112">The operation was successful.</span></span>|  
|<span data-ttu-id="517fa-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="517fa-113">S_FALSE</span></span>|<span data-ttu-id="517fa-114">Nie można ukończyć operacji lub w wyliczeniu nie ma więcej domen.</span><span class="sxs-lookup"><span data-stu-id="517fa-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="517fa-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="517fa-115">E_FAIL</span></span>|<span data-ttu-id="517fa-116">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="517fa-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="517fa-117">Jeśli metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="517fa-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="517fa-118">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="517fa-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="517fa-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="517fa-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="517fa-120">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="517fa-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="517fa-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="517fa-121">Requirements</span></span>  
 <span data-ttu-id="517fa-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="517fa-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="517fa-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="517fa-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="517fa-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="517fa-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="517fa-125">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="517fa-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517fa-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="517fa-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="517fa-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="517fa-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
