---
title: ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c39ad4638c7db45c481bd3dfccb0a82759397aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072586"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="7c7cd-102">ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c7cd-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="7c7cd-103">Pobiera flagi uruchamiania i pliku konfiguracyjnego hosta, która będzie służyć do uruchomienia w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c7cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c7cd-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c7cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c7cd-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="7c7cd-106">[out] Wskaźnik flagi uruchamiania hosta, które są ustawione.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="7c7cd-107">[out] Wskaźnik do ścieżkę katalogu bieżącego pliku konfiguracji hosta.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="7c7cd-108">[out w] W danych wejściowych, rozmiar `pwzHostConfigFile`, aby uniknąć przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="7c7cd-109">Jeśli `pwzHostConfigFile` jest wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` wstępnej alokacji.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c7cd-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c7cd-110">Return Value</span></span>  
 <span data-ttu-id="7c7cd-111">Ta metoda zwraca następujące HRESULT określonych oraz błędów HRESULT, wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7c7cd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c7cd-112">HRESULT</span></span>|<span data-ttu-id="7c7cd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7c7cd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c7cd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c7cd-114">S_OK</span></span>|<span data-ttu-id="7c7cd-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c7cd-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c7cd-116">Remarks</span></span>  
 <span data-ttu-id="7c7cd-117">Ta metoda zwraca wartości domyślne flagi (`STARTUP_CONCURRENT_GC` i `NULL`), lub wartości, dostarczone przez poprzednie wywołanie [iclrruntimeinfo::setdefaultstartupflags — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), lub wartości ustawione przez żaden z `CorBind*` metody, jeśli są one powiązane z tym środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c7cd-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c7cd-118">Requirements</span></span>  
 <span data-ttu-id="7c7cd-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c7cd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c7cd-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7c7cd-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7c7cd-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c7cd-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7c7cd-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7c7cd-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7c7cd-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c7cd-123">See also</span></span>

- [<span data-ttu-id="7c7cd-124">ICLRRuntimeInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7c7cd-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7c7cd-125">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7c7cd-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7c7cd-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="7c7cd-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
