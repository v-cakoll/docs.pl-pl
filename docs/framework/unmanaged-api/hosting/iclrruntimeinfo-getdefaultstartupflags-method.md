---
title: "ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b278a791c7e5418322a80bc6478f75791a35af8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="319d1-102">ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="319d1-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="319d1-103">Pobiera flagi uruchamiania i pliku konfiguracji hosta, który będzie używany do uruchomienia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="319d1-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="319d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="319d1-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="319d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="319d1-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="319d1-106">[out] Wskaźnik do aktualnie ustawionych flag uruchomienia hosta.</span><span class="sxs-lookup"><span data-stu-id="319d1-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="319d1-107">[out] Wskaźnik do ścieżki katalogu bieżącego pliku konfiguracji hosta.</span><span class="sxs-lookup"><span data-stu-id="319d1-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="319d1-108">[w, out] W danych wejściowych, rozmiar `pwzHostConfigFile`, aby uniknąć przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="319d1-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="319d1-109">Jeśli `pwzHostConfigFile` jest wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` wstępnej alokacji.</span><span class="sxs-lookup"><span data-stu-id="319d1-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="319d1-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="319d1-110">Return Value</span></span>  
 <span data-ttu-id="319d1-111">Ta metoda zwraca następujące HRESULT określonych oraz HRESULT błędów, które wskazuje niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="319d1-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="319d1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="319d1-112">HRESULT</span></span>|<span data-ttu-id="319d1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="319d1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="319d1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="319d1-114">S_OK</span></span>|<span data-ttu-id="319d1-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="319d1-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="319d1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="319d1-116">Remarks</span></span>  
 <span data-ttu-id="319d1-117">Ta metoda zwraca domyślne wartości flag (`STARTUP_CONCURRENT_GC` i `NULL`), lub wartości podane przez poprzednie wywołanie [ICLRRuntimeInfo::SetDefaultStartupFlags — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), i wartościami ustawionymi przez `CorBind*` metody, jeśli są one powiązane z tego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="319d1-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="319d1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="319d1-118">Requirements</span></span>  
 <span data-ttu-id="319d1-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="319d1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="319d1-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="319d1-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="319d1-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="319d1-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="319d1-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="319d1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319d1-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="319d1-123">See Also</span></span>  
 [<span data-ttu-id="319d1-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="319d1-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="319d1-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="319d1-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="319d1-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="319d1-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
