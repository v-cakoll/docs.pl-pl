---
title: "ICorRuntimeHost::GetDefaultDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetDefaultDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa732462fb574f1d55fda12f82d8f97da2654e02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="9d6c5-102">ICorRuntimeHost::GetDefaultDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d6c5-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="9d6c5-103">Pobiera wskaźnika interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domenę domyślną dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d6c5-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d6c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d6c5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9d6c5-106">[out] Wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType> do <xref:System.AppDomain> wystąpienie reprezentującego domyślnej domeny aplikacji dla procesu.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="9d6c5-107">Ten wskaźnik jest typu `IUnknown`, dlatego zazwyczaj powinny wywoływać elementy wywołujące `QueryInterface` uzyskać wskaźnika interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d6c5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d6c5-108">Return Value</span></span>  
  
|<span data-ttu-id="9d6c5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d6c5-109">HRESULT</span></span>|<span data-ttu-id="9d6c5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9d6c5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d6c5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d6c5-111">S_OK</span></span>|<span data-ttu-id="9d6c5-112">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-112">The operation was successful.</span></span>|  
|<span data-ttu-id="9d6c5-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9d6c5-113">S_FALSE</span></span>|<span data-ttu-id="9d6c5-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9d6c5-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d6c5-115">E_FAIL</span></span>|<span data-ttu-id="9d6c5-116">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9d6c5-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9d6c5-118">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d6c5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d6c5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d6c5-120">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9d6c5-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d6c5-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d6c5-121">Requirements</span></span>  
 <span data-ttu-id="9d6c5-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6c5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6c5-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d6c5-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d6c5-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d6c5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d6c5-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9d6c5-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6c5-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d6c5-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="9d6c5-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d6c5-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
