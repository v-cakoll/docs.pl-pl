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
ms.openlocfilehash: 0ce822533b0699f3467dc08044aa4dab59285a77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120314"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="327a6-102">ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="327a6-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="327a6-103">Pobiera flagi uruchamiania i plik konfiguracji hosta, który zostanie użyty do uruchomienia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="327a6-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="327a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="327a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="327a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="327a6-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="327a6-106">określoną Wskaźnik do ustawionych obecnie flag uruchamiania hosta.</span><span class="sxs-lookup"><span data-stu-id="327a6-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="327a6-107">określoną Wskaźnik do ścieżki katalogu bieżącego pliku konfiguracji hosta.</span><span class="sxs-lookup"><span data-stu-id="327a6-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="327a6-108">[in. out] Na wejściu rozmiar `pwzHostConfigFile`, aby uniknąć przekroczeń buforu.</span><span class="sxs-lookup"><span data-stu-id="327a6-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="327a6-109">Jeśli `pwzHostConfigFile` ma wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` do wstępnego przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="327a6-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="327a6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="327a6-110">Return Value</span></span>  
 <span data-ttu-id="327a6-111">Ta metoda zwraca następujące określone wartości HRESULT, a także błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="327a6-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="327a6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="327a6-112">HRESULT</span></span>|<span data-ttu-id="327a6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="327a6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="327a6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="327a6-114">S_OK</span></span>|<span data-ttu-id="327a6-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="327a6-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="327a6-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="327a6-116">Remarks</span></span>  
 <span data-ttu-id="327a6-117">Ta metoda zwraca wartości domyślnych flag (`STARTUP_CONCURRENT_GC` i `NULL`) albo wartości dostarczonych przez poprzednie wywołanie [metody ICLRRuntimeInfo:: SetDefaultStartupFlags —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)lub wartości ustawionych przy użyciu dowolnej metody `CorBind*`, jeśli są one powiązane z tym środowiskiem uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="327a6-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="327a6-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="327a6-118">Requirements</span></span>  
 <span data-ttu-id="327a6-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="327a6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="327a6-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="327a6-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="327a6-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="327a6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="327a6-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="327a6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="327a6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="327a6-123">See also</span></span>

- [<span data-ttu-id="327a6-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="327a6-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="327a6-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="327a6-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="327a6-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="327a6-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
