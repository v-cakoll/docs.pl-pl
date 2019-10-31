---
title: ICLRRuntimeInfo::LoadLibrary — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 8c72f58bb65bd862b0625bfa0398b26bad0197e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192085"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="d6458-102">ICLRRuntimeInfo::LoadLibrary — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6458-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="d6458-103">Ładuje bibliotekę .NET Framework z aparatu plików wykonywalnych języka wspólnego (CLR) reprezentowanego przez interfejs [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d6458-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="d6458-104">Ta metoda zastępuje funkcję [LoadLibraryShim —](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d6458-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6458-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6458-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6458-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6458-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="d6458-107">podczas Nazwa zestawu, który ma zostać załadowany.</span><span class="sxs-lookup"><span data-stu-id="d6458-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="d6458-108">określoną Dojście do ładowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d6458-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6458-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d6458-109">Return Value</span></span>  
 <span data-ttu-id="d6458-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d6458-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d6458-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6458-111">HRESULT</span></span>|<span data-ttu-id="d6458-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d6458-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6458-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6458-113">S_OK</span></span>|<span data-ttu-id="d6458-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d6458-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d6458-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d6458-115">E_POINTER</span></span>|<span data-ttu-id="d6458-116">`pwzDllName` lub `phndModule` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d6458-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="d6458-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d6458-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d6458-118">Za mało dostępnej pamięci, aby obsłużyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="d6458-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6458-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6458-119">Remarks</span></span>  
 <span data-ttu-id="d6458-120">Ta metoda ładuje tylko biblioteki dll zawarte w pakiecie redystrybucyjnym .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6458-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="d6458-121">Nie można załadować zestawów wygenerowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d6458-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6458-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6458-122">Requirements</span></span>  
 <span data-ttu-id="d6458-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6458-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6458-124">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="d6458-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d6458-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6458-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6458-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6458-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6458-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6458-127">See also</span></span>

- [<span data-ttu-id="d6458-128">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6458-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d6458-129">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d6458-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d6458-130">Hosting</span><span class="sxs-lookup"><span data-stu-id="d6458-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
