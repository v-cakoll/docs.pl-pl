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
ms.openlocfilehash: 69fcc862e98e305105a6f17ca49940bd10cef39c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937062"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="56fb4-102">ICorRuntimeHost::EnumDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="56fb4-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="56fb4-103">Pobiera moduł wyliczający dla domen w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="56fb4-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fb4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56fb4-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56fb4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="56fb4-106">[out] Moduł wyliczający dla domen.</span><span class="sxs-lookup"><span data-stu-id="56fb4-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56fb4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56fb4-107">Return Value</span></span>  
  
|<span data-ttu-id="56fb4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56fb4-108">HRESULT</span></span>|<span data-ttu-id="56fb4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="56fb4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56fb4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="56fb4-110">S_OK</span></span>|<span data-ttu-id="56fb4-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="56fb4-111">The operation was successful.</span></span>|  
|<span data-ttu-id="56fb4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="56fb4-112">S_FALSE</span></span>|<span data-ttu-id="56fb4-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="56fb4-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="56fb4-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56fb4-114">E_FAIL</span></span>|<span data-ttu-id="56fb4-115">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="56fb4-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="56fb4-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="56fb4-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="56fb4-117">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="56fb4-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="56fb4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56fb4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56fb4-119">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="56fb4-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56fb4-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56fb4-120">Requirements</span></span>  
 <span data-ttu-id="56fb4-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fb4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fb4-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56fb4-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56fb4-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56fb4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56fb4-124">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="56fb4-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fb4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56fb4-125">See also</span></span>

- [<span data-ttu-id="56fb4-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="56fb4-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
