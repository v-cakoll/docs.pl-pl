---
title: ICLRMetaHostPolicy — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9a70cf0812f84908630f109ef06aafa4b4f7525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434425"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="d78ec-102">ICLRMetaHostPolicy — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d78ec-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="d78ec-103">Udostępnia [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodę, która zwraca wskaźnik do wspólny interfejs środowiska uruchomieniowego (języka wspólnego CLR) języka na podstawie kryteriów zasad, zarządzane zestawu, wersję i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d78ec-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d78ec-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d78ec-104">Methods</span></span>  
  
|<span data-ttu-id="d78ec-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d78ec-105">Method</span></span>|<span data-ttu-id="d78ec-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d78ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d78ec-107">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="d78ec-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="d78ec-108">Dostarcza wybranego interfejsu CLR na podstawie kryteriów zasad, zarządzanych plików zestawu, wersję i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d78ec-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d78ec-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d78ec-109">Remarks</span></span>  
 <span data-ttu-id="d78ec-110">Odwołanie do danego interfejsu można uzyskać przez wywołanie metody [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) działać zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="d78ec-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="d78ec-111">Ten interfejs nie faktycznie obciążenie lub aktywować CLR, ale po prostu zwraca preferowany wersji środowiska CLR oparte na dostępne wersje, które są zainstalowane lub załadować.</span><span class="sxs-lookup"><span data-stu-id="d78ec-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="d78ec-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostingu API konsoliduje zasady, tak aby hostów z określonych potrzeb może używać podstawowych funkcji bez ponoszenia kar niezamierzone.</span><span class="sxs-lookup"><span data-stu-id="d78ec-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="d78ec-113">Na przykład wiele eksportu biblioteki MSCorEE.dll powiąże do określonego środowiska CLR, mimo że metody mogą nie logicznie wymagać go.</span><span class="sxs-lookup"><span data-stu-id="d78ec-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="d78ec-114">[Metahost_policy_flags —](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) wyliczenie zawiera zasady powiązania, które są wspólne dla większości hostów.</span><span class="sxs-lookup"><span data-stu-id="d78ec-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d78ec-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d78ec-115">Requirements</span></span>  
 <span data-ttu-id="d78ec-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d78ec-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d78ec-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d78ec-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d78ec-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d78ec-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d78ec-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d78ec-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78ec-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d78ec-120">See Also</span></span>  
 [<span data-ttu-id="d78ec-121">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="d78ec-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="d78ec-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d78ec-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d78ec-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="d78ec-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
