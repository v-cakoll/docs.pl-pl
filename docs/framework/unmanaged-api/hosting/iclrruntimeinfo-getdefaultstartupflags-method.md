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
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703886"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="e1d36-102">ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1d36-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="e1d36-103">Pobiera flagi uruchamiania i plik konfiguracji hosta, który zostanie użyty do uruchomienia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e1d36-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1d36-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1d36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1d36-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="e1d36-106">określoną Wskaźnik do ustawionych obecnie flag uruchamiania hosta.</span><span class="sxs-lookup"><span data-stu-id="e1d36-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="e1d36-107">określoną Wskaźnik do ścieżki katalogu bieżącego pliku konfiguracji hosta.</span><span class="sxs-lookup"><span data-stu-id="e1d36-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="e1d36-108">[in. out] Na wejściu, rozmiar `pwzHostConfigFile` , aby uniknąć przekroczeń buforu.</span><span class="sxs-lookup"><span data-stu-id="e1d36-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="e1d36-109">Jeśli `pwzHostConfigFile` ma wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` dla wstępnej alokacji.</span><span class="sxs-lookup"><span data-stu-id="e1d36-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1d36-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e1d36-110">Return Value</span></span>  
 <span data-ttu-id="e1d36-111">Ta metoda zwraca następujące określone wartości HRESULT, a także błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="e1d36-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e1d36-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1d36-112">HRESULT</span></span>|<span data-ttu-id="e1d36-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e1d36-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1d36-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1d36-114">S_OK</span></span>|<span data-ttu-id="e1d36-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1d36-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1d36-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1d36-116">Remarks</span></span>  
 <span data-ttu-id="e1d36-117">Ta metoda zwraca wartości domyślnych flag ( `STARTUP_CONCURRENT_GC` i `NULL` ) lub wartości dostarczonych przez poprzednie wywołanie [metody ICLRRuntimeInfo:: SetDefaultStartupFlags —](iclrruntimeinfo-setdefaultstartupflags-method.md)lub wartości ustawionych przy użyciu dowolnej `CorBind*` metody, jeśli są one powiązane z tym środowiskiem uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="e1d36-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1d36-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1d36-118">Requirements</span></span>  
 <span data-ttu-id="e1d36-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1d36-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1d36-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="e1d36-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e1d36-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e1d36-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1d36-122">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d36-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d36-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1d36-123">See also</span></span>

- [<span data-ttu-id="e1d36-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1d36-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e1d36-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e1d36-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e1d36-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="e1d36-126">Hosting</span></span>](index.md)
