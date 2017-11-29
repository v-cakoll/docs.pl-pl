---
title: "ICorRuntimeHost::EnumDomains — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.EnumDomains
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c63e4345815a073fe6aa422018b6fadf45bd5370
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="95b7b-102">ICorRuntimeHost::EnumDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="95b7b-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="95b7b-103">Pobiera moduł wyliczający dla domen w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="95b7b-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95b7b-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95b7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95b7b-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="95b7b-106">[out] Moduł wyliczający dla domen.</span><span class="sxs-lookup"><span data-stu-id="95b7b-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95b7b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="95b7b-107">Return Value</span></span>  
  
|<span data-ttu-id="95b7b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95b7b-108">HRESULT</span></span>|<span data-ttu-id="95b7b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="95b7b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95b7b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="95b7b-110">S_OK</span></span>|<span data-ttu-id="95b7b-111">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="95b7b-111">The operation was successful.</span></span>|  
|<span data-ttu-id="95b7b-112">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="95b7b-112">S_FALSE</span></span>|<span data-ttu-id="95b7b-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="95b7b-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="95b7b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95b7b-114">E_FAIL</span></span>|<span data-ttu-id="95b7b-115">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="95b7b-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="95b7b-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="95b7b-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="95b7b-117">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="95b7b-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95b7b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95b7b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95b7b-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="95b7b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95b7b-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95b7b-120">Requirements</span></span>  
 <span data-ttu-id="95b7b-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95b7b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b7b-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95b7b-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95b7b-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95b7b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95b7b-124">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="95b7b-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b7b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95b7b-125">See Also</span></span>  
 [<span data-ttu-id="95b7b-126">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="95b7b-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
