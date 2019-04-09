---
title: CLRCreateInstance — Funkcja
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3571e2698b980b12b89a5b689efb868a34a3ef71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167664"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="7dae4-102">CLRCreateInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7dae4-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="7dae4-103">Zawiera jeden z trzech interfejsów: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), lub [iclrdebugging —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7dae4-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dae4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dae4-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dae4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dae4-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="7dae4-106">[in] Jeden z trzech identyfikatorów klasy: Argumentami CLSID_CLRMetaHost CLSID_CLRMetaHostPolicy lub CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="7dae4-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="7dae4-107">[in] Jeden z trzech identyfikatorów interfejsu (IID): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy lub IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="7dae4-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="7dae4-108">[out] Jeden z trzech interfejsów: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), lub [iclrdebugging —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7dae4-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dae4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7dae4-109">Return Value</span></span>  
 <span data-ttu-id="7dae4-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="7dae4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7dae4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7dae4-111">HRESULT</span></span>|<span data-ttu-id="7dae4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7dae4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7dae4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7dae4-113">S_OK</span></span>|<span data-ttu-id="7dae4-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7dae4-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7dae4-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7dae4-115">E_POINTER</span></span>|`ppInterface` <span data-ttu-id="7dae4-116">ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="7dae4-116">is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dae4-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7dae4-117">Remarks</span></span>  
 <span data-ttu-id="7dae4-118">W poniższej tabeli przedstawiono obsługiwane kombinacje w celach `clsid` i `riid`.</span><span class="sxs-lookup"><span data-stu-id="7dae4-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="7dae4-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="7dae4-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="7dae4-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="7dae4-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="7dae4-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="7dae4-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="7dae4-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="7dae4-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="7dae4-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="7dae4-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="7dae4-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="7dae4-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="7dae4-125">Poniższy kod przedstawia sposób użycia `CLRCreateInstance` można pobrać wszystkich trzech interfejsów:</span><span class="sxs-lookup"><span data-stu-id="7dae4-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7dae4-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7dae4-126">Requirements</span></span>  
 <span data-ttu-id="7dae4-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dae4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dae4-128">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7dae4-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7dae4-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7dae4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7dae4-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7dae4-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7dae4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dae4-131">See also</span></span>

- [<span data-ttu-id="7dae4-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="7dae4-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
