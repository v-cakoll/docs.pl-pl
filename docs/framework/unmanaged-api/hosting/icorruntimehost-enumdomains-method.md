---
title: ICorRuntimeHost::EnumDomains — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 545af69e06e7ea4262450025e9cb0d6529f99ad4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780060"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="a197a-102">ICorRuntimeHost::EnumDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="a197a-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="a197a-103">Pobiera moduł wyliczający dla domen w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="a197a-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a197a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a197a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a197a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a197a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="a197a-106">[out] Moduł wyliczający dla domen.</span><span class="sxs-lookup"><span data-stu-id="a197a-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a197a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a197a-107">Return Value</span></span>  
  
|<span data-ttu-id="a197a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a197a-108">HRESULT</span></span>|<span data-ttu-id="a197a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a197a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a197a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a197a-110">S_OK</span></span>|<span data-ttu-id="a197a-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a197a-111">The operation was successful.</span></span>|  
|<span data-ttu-id="a197a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a197a-112">S_FALSE</span></span>|<span data-ttu-id="a197a-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="a197a-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a197a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a197a-114">E_FAIL</span></span>|<span data-ttu-id="a197a-115">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="a197a-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a197a-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="a197a-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a197a-117">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a197a-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a197a-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a197a-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a197a-119">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a197a-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a197a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a197a-120">Requirements</span></span>  
 <span data-ttu-id="a197a-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a197a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a197a-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a197a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a197a-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a197a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a197a-124">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a197a-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a197a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a197a-125">See also</span></span>

- [<span data-ttu-id="a197a-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a197a-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
