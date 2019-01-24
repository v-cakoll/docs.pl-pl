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
ms.openlocfilehash: 46576552db6e3c9aa06646b260e74cb4b7890d9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559232"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="ee7fe-102">ICLRMetaHostPolicy — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ee7fe-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="ee7fe-103">Udostępnia [getrequestedruntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody, która zwraca wskaźnik do wspólnego interfejsu języka wspólnego (CLR), na podstawie kryteriów zasad, zarządzanego zestawu, wersji i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ee7fe-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee7fe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee7fe-104">Methods</span></span>  
  
|<span data-ttu-id="ee7fe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee7fe-105">Method</span></span>|<span data-ttu-id="ee7fe-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ee7fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee7fe-107">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="ee7fe-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="ee7fe-108">Udostępnia preferowanym interfejsem CLR na podstawie kryteriów zasad, zarządzane pliku zestawu, wersji i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ee7fe-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee7fe-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee7fe-109">Remarks</span></span>  
 <span data-ttu-id="ee7fe-110">Można uzyskać odwołanie do tego interfejsu, wywołując [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ee7fe-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="ee7fe-111">Ten interfejs bez faktycznego obciążenia lub aktywacji środowiska CLR, ale po prostu zwraca, w oparciu o dostępne wersje, które są zainstalowane lub załadować preferowaną wersję środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ee7fe-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="ee7fe-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostującego interfejs API konsoliduje zasady, tak, aby hosty z konkretnych potrzeb może używać podstawową funkcjonalność bez ponoszenia kar niezamierzone.</span><span class="sxs-lookup"><span data-stu-id="ee7fe-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="ee7fe-113">Na przykład wielu eksportów MSCorEE.dll powiąże określonego środowiska CLR, mimo iż metoda może być logicznie wymaga.</span><span class="sxs-lookup"><span data-stu-id="ee7fe-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="ee7fe-114">[Metahost_policy_flags —](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) wyliczenia zawiera zasad powiązań, które są wspólne dla większości hostów.</span><span class="sxs-lookup"><span data-stu-id="ee7fe-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee7fe-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee7fe-115">Requirements</span></span>  
 <span data-ttu-id="ee7fe-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee7fe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee7fe-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ee7fe-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ee7fe-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee7fe-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee7fe-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee7fe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee7fe-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee7fe-120">See also</span></span>
- [<span data-ttu-id="ee7fe-121">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="ee7fe-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="ee7fe-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ee7fe-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ee7fe-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="ee7fe-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
