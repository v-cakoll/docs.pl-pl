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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fe1f93c621fd567471b9a49e4aa75cb90e6e0e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161164"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="c0aee-102">ICLRRuntimeInfo::LoadLibrary — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0aee-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="c0aee-103">Ładuje bibliotekę .NET Framework z środowisko uruchomieniowe języka wspólnego (CLR) reprezentowany przez [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c0aee-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="c0aee-104">Ta metoda zastępuje [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="c0aee-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0aee-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0aee-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0aee-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0aee-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="c0aee-107">[in] Nazwa zestawu do załadowania.</span><span class="sxs-lookup"><span data-stu-id="c0aee-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="c0aee-108">[out] Dojście do załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c0aee-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0aee-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c0aee-109">Return Value</span></span>  
 <span data-ttu-id="c0aee-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="c0aee-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c0aee-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0aee-111">HRESULT</span></span>|<span data-ttu-id="c0aee-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c0aee-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0aee-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0aee-113">S_OK</span></span>|<span data-ttu-id="c0aee-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c0aee-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="c0aee-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c0aee-115">E_POINTER</span></span>|`pwzDllName` <span data-ttu-id="c0aee-116">lub `phndModule` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="c0aee-116">or `phndModule` is null.</span></span>|  
|<span data-ttu-id="c0aee-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c0aee-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c0aee-118">Nie ma wystarczającej ilości pamięci dostępnej może obsłużyć żądania.</span><span class="sxs-lookup"><span data-stu-id="c0aee-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0aee-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0aee-119">Remarks</span></span>  
 <span data-ttu-id="c0aee-120">Ta metoda ładuje tylko pliki dll zawarte w pakiet redystrybucyjny programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0aee-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="c0aee-121">Nie można załadować zestawów generowanych przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="c0aee-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0aee-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0aee-122">Requirements</span></span>  
 <span data-ttu-id="c0aee-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0aee-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0aee-124">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c0aee-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c0aee-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0aee-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c0aee-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c0aee-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0aee-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0aee-127">See also</span></span>

- [<span data-ttu-id="c0aee-128">ICLRRuntimeInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c0aee-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c0aee-129">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c0aee-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="c0aee-130">Hosting</span><span class="sxs-lookup"><span data-stu-id="c0aee-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
