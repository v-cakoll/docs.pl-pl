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
ms.openlocfilehash: 688e7a0fa32650aa0f626ddf40283f73ceb57156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437794"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="dc8f2-102">ICorRuntimeHost::EnumDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc8f2-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="dc8f2-103">Pobiera moduł wyliczający dla domen w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc8f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc8f2-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc8f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc8f2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="dc8f2-106">[out] Moduł wyliczający dla domen.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc8f2-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dc8f2-107">Return Value</span></span>  
  
|<span data-ttu-id="dc8f2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc8f2-108">HRESULT</span></span>|<span data-ttu-id="dc8f2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dc8f2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc8f2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc8f2-110">S_OK</span></span>|<span data-ttu-id="dc8f2-111">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-111">The operation was successful.</span></span>|  
|<span data-ttu-id="dc8f2-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dc8f2-112">S_FALSE</span></span>|<span data-ttu-id="dc8f2-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="dc8f2-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc8f2-114">E_FAIL</span></span>|<span data-ttu-id="dc8f2-115">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="dc8f2-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="dc8f2-117">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dc8f2-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc8f2-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc8f2-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dc8f2-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc8f2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc8f2-120">Requirements</span></span>  
 <span data-ttu-id="dc8f2-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc8f2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc8f2-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc8f2-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc8f2-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc8f2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc8f2-124">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="dc8f2-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8f2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc8f2-125">See Also</span></span>  
 [<span data-ttu-id="dc8f2-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc8f2-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
