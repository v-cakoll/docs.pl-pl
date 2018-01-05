---
title: "ICorRuntimeHost::NextDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.NextDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e539cd4071fe9713ed53f66c2f67b24b787d259
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="b6690-102">ICorRuntimeHost::NextDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6690-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="b6690-103">Pobiera wskaźnika interfejsu do następnej domeny w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="b6690-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6690-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6690-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6690-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6690-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b6690-106">[in] Moduł wyliczający, który został uzyskany przez wywołanie [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="b6690-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b6690-107">[out] Wskaźnik interfejsu do <xref:System._AppDomain?displayProperty=nameWithType> typ, który reprezentuje dalej domeny w wyliczenia lub wartość null, jeśli nie istnieją żadne więcej domen.</span><span class="sxs-lookup"><span data-stu-id="b6690-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6690-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b6690-108">Return Value</span></span>  
  
|<span data-ttu-id="b6690-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6690-109">HRESULT</span></span>|<span data-ttu-id="b6690-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b6690-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6690-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6690-111">S_OK</span></span>|<span data-ttu-id="b6690-112">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="b6690-112">The operation was successful.</span></span>|  
|<span data-ttu-id="b6690-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b6690-113">S_FALSE</span></span>|<span data-ttu-id="b6690-114">Nie można ukończyć operacji, lub w wyliczeniu nie istnieją domeny więcej.</span><span class="sxs-lookup"><span data-stu-id="b6690-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="b6690-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6690-115">E_FAIL</span></span>|<span data-ttu-id="b6690-116">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="b6690-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b6690-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="b6690-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b6690-118">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b6690-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b6690-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6690-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6690-120">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b6690-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6690-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6690-121">Requirements</span></span>  
 <span data-ttu-id="b6690-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6690-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6690-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6690-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6690-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6690-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6690-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b6690-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6690-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6690-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="b6690-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6690-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
