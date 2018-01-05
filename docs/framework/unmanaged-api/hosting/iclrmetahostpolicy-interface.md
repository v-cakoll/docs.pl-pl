---
title: "ICLRMetaHostPolicy — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd9b8d6aef2289833a0bd192b838e6f70ea8c0ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="7847f-102">ICLRMetaHostPolicy — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7847f-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="7847f-103">Udostępnia [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodę, która zwraca wskaźnik do wspólny interfejs środowiska uruchomieniowego (języka wspólnego CLR) języka na podstawie kryteriów zasad, zarządzane zestawu, wersję i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7847f-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7847f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7847f-104">Methods</span></span>  
  
|<span data-ttu-id="7847f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7847f-105">Method</span></span>|<span data-ttu-id="7847f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7847f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7847f-107">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="7847f-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="7847f-108">Dostarcza wybranego interfejsu CLR na podstawie kryteriów zasad, zarządzanych plików zestawu, wersję i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7847f-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7847f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7847f-109">Remarks</span></span>  
 <span data-ttu-id="7847f-110">Odwołanie do danego interfejsu można uzyskać przez wywołanie metody [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) działać zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="7847f-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="7847f-111">Ten interfejs nie faktycznie obciążenie lub aktywować CLR, ale po prostu zwraca preferowany wersji środowiska CLR oparte na dostępne wersje, które są zainstalowane lub załadować.</span><span class="sxs-lookup"><span data-stu-id="7847f-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="7847f-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostingu API konsoliduje zasady, tak aby hostów z określonych potrzeb może używać podstawowych funkcji bez ponoszenia kar niezamierzone.</span><span class="sxs-lookup"><span data-stu-id="7847f-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="7847f-113">Na przykład wiele eksportu biblioteki MSCorEE.dll powiąże do określonego środowiska CLR, mimo że metody mogą nie logicznie wymagać go.</span><span class="sxs-lookup"><span data-stu-id="7847f-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="7847f-114">[Metahost_policy_flags —](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) wyliczenie zawiera zasady powiązania, które są wspólne dla większości hostów.</span><span class="sxs-lookup"><span data-stu-id="7847f-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7847f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7847f-115">Requirements</span></span>  
 <span data-ttu-id="7847f-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7847f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7847f-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7847f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7847f-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7847f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7847f-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7847f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7847f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7847f-120">See Also</span></span>  
 [<span data-ttu-id="7847f-121">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="7847f-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="7847f-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7847f-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="7847f-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="7847f-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
