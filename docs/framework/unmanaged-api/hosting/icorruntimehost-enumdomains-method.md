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
ms.openlocfilehash: e5a1642f968228c5815732ecd470cb8f02a0eb83
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139581"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="65628-102">ICorRuntimeHost::EnumDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="65628-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="65628-103">Pobiera moduł wyliczający dla domen w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="65628-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65628-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65628-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65628-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65628-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="65628-106">określoną Moduł wyliczający dla domen.</span><span class="sxs-lookup"><span data-stu-id="65628-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65628-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65628-107">Return Value</span></span>  
  
|<span data-ttu-id="65628-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65628-108">HRESULT</span></span>|<span data-ttu-id="65628-109">Opis</span><span class="sxs-lookup"><span data-stu-id="65628-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65628-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="65628-110">S_OK</span></span>|<span data-ttu-id="65628-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="65628-111">The operation was successful.</span></span>|  
|<span data-ttu-id="65628-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="65628-112">S_FALSE</span></span>|<span data-ttu-id="65628-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="65628-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="65628-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65628-114">E_FAIL</span></span>|<span data-ttu-id="65628-115">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="65628-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="65628-116">Jeśli metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="65628-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="65628-117">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65628-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="65628-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65628-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65628-119">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="65628-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65628-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65628-120">Requirements</span></span>  
 <span data-ttu-id="65628-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65628-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65628-122">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65628-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65628-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65628-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65628-124">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="65628-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65628-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65628-125">See also</span></span>

- [<span data-ttu-id="65628-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="65628-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
