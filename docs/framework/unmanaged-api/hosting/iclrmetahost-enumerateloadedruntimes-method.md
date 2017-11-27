---
title: "ICLRMetaHost::EnumerateLoadedRuntimes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateLoadedRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0724bf44eaf82b39262876ea4a44509b6c7d576
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="eb0c0-102">ICLRMetaHost::EnumerateLoadedRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb0c0-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="eb0c0-103">Zwraca wyliczenie zawiera prawidłowy [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdej wersji środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w danym procesie.</span><span class="sxs-lookup"><span data-stu-id="eb0c0-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="eb0c0-104">Ta metoda zastępuje [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="eb0c0-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb0c0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb0c0-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb0c0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb0c0-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="eb0c0-107">[in] Dojście procesu do sprawdzenia pod kątem załadować środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="eb0c0-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="eb0c0-108">[out] <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` Wyliczenie [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsy odpowiadający każdej CLR, która jest ładowana przez proces.</span><span class="sxs-lookup"><span data-stu-id="eb0c0-108">[out] An <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb0c0-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb0c0-109">Return Value</span></span>  
 <span data-ttu-id="eb0c0-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="eb0c0-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="eb0c0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb0c0-111">HRESULT</span></span>|<span data-ttu-id="eb0c0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="eb0c0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb0c0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb0c0-113">S_OK</span></span>|<span data-ttu-id="eb0c0-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="eb0c0-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="eb0c0-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="eb0c0-115">E_POINTER</span></span>|<span data-ttu-id="eb0c0-116">`ppEnumerator`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="eb0c0-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb0c0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb0c0-117">Remarks</span></span>  
 <span data-ttu-id="eb0c0-118">Ta metoda jest środowisk uruchomieniowych Wyświetla wszystkie załadowane, nawet jeśli były przestarzałe funkcje takie jak załadować [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="eb0c0-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb0c0-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb0c0-119">Requirements</span></span>  
 <span data-ttu-id="eb0c0-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb0c0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb0c0-121">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="eb0c0-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eb0c0-122">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb0c0-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb0c0-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0c0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb0c0-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb0c0-124">See Also</span></span>  
 [<span data-ttu-id="eb0c0-125">ICLRMetaHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="eb0c0-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="eb0c0-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="eb0c0-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
