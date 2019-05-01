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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771751"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="4b3d2-102">ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b3d2-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="4b3d2-103">Pobiera flagi uruchamiania i pliku konfiguracyjnego hosta, która będzie służyć do uruchomienia w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b3d2-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b3d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b3d2-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="4b3d2-106">[out] Wskaźnik flagi uruchamiania hosta, które są ustawione.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="4b3d2-107">[out] Wskaźnik do ścieżkę katalogu bieżącego pliku konfiguracji hosta.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="4b3d2-108">[out w] W danych wejściowych, rozmiar `pwzHostConfigFile`, aby uniknąć przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="4b3d2-109">Jeśli `pwzHostConfigFile` jest wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` wstępnej alokacji.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b3d2-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4b3d2-110">Return Value</span></span>  
 <span data-ttu-id="4b3d2-111">Ta metoda zwraca następujące HRESULT określonych oraz błędów HRESULT, wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4b3d2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b3d2-112">HRESULT</span></span>|<span data-ttu-id="4b3d2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4b3d2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b3d2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b3d2-114">S_OK</span></span>|<span data-ttu-id="4b3d2-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b3d2-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b3d2-116">Remarks</span></span>  
 <span data-ttu-id="4b3d2-117">Ta metoda zwraca wartości domyślne flagi (`STARTUP_CONCURRENT_GC` i `NULL`), lub wartości, dostarczone przez poprzednie wywołanie [iclrruntimeinfo::setdefaultstartupflags — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), lub wartości ustawione przez żaden z `CorBind*` metody, jeśli są one powiązane z tym środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="4b3d2-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b3d2-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b3d2-118">Requirements</span></span>  
 <span data-ttu-id="4b3d2-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b3d2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b3d2-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4b3d2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4b3d2-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b3d2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b3d2-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b3d2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3d2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b3d2-123">See also</span></span>

- [<span data-ttu-id="4b3d2-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b3d2-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4b3d2-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4b3d2-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4b3d2-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="4b3d2-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
