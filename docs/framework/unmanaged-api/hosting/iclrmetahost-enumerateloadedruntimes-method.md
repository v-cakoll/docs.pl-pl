---
title: ICLRMetaHost::EnumerateLoadedRuntimes — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b77a01a6adf40c21e0d56853b860982e39b9b27e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779802"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="3310f-102">ICLRMetaHost::EnumerateLoadedRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="3310f-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="3310f-103">Zwraca wyliczenie, które zawiera prawidłową [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdej wersji programu środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w danym procesie.</span><span class="sxs-lookup"><span data-stu-id="3310f-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="3310f-104">Ta metoda zastępuje [getversionfromprocess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="3310f-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3310f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3310f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3310f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3310f-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="3310f-107">[in] Uchwyt procesu do wglądu dla środowisk uruchomieniowych załadowane.</span><span class="sxs-lookup"><span data-stu-id="3310f-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="3310f-108">[out] <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> Wyliczenie [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsów odpowiadający każdej CLR, który jest ładowany przez proces.</span><span class="sxs-lookup"><span data-stu-id="3310f-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3310f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3310f-109">Return Value</span></span>  
 <span data-ttu-id="3310f-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="3310f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3310f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3310f-111">HRESULT</span></span>|<span data-ttu-id="3310f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3310f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3310f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3310f-113">S_OK</span></span>|<span data-ttu-id="3310f-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3310f-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3310f-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3310f-115">E_POINTER</span></span>|<span data-ttu-id="3310f-116">`ppEnumerator` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="3310f-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3310f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3310f-117">Remarks</span></span>  
 <span data-ttu-id="3310f-118">Ta metoda jest załadowany Wyświetla wszystkie środowiska uruchomieniowe, nawet wtedy, gdy zostały przestarzałe funkcje takie jak załadowane [CorBindToRuntime —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="3310f-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3310f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3310f-119">Requirements</span></span>  
 <span data-ttu-id="3310f-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3310f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3310f-121">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3310f-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3310f-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3310f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3310f-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3310f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3310f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3310f-124">See also</span></span>

- [<span data-ttu-id="3310f-125">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="3310f-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="3310f-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="3310f-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
