---
title: ICLRRuntimeInfo::GetRuntimeDirectory — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c09f57ad805b4ba17b4bdafd3ced533199277a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196687"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="e54fc-102">ICLRRuntimeInfo::GetRuntimeDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="e54fc-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="e54fc-103">Pobiera katalogu instalacji zestawu środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z tym interfejsem.</span><span class="sxs-lookup"><span data-stu-id="e54fc-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="e54fc-104">Ta metoda zastępuje [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) funkcja udostępniana w .NET Framework w wersji 2.0, 3.0 i 3.5.</span><span class="sxs-lookup"><span data-stu-id="e54fc-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e54fc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e54fc-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e54fc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e54fc-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="e54fc-107">[out] Zwraca katalog instalacyjny środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="e54fc-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="e54fc-108">Ścieżka instalacji jest w pełni kwalifikowany; na przykład "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="e54fc-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="e54fc-109">[out w] Określa rozmiar `pwzBuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="e54fc-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="e54fc-110">Jeśli `pwzBuffer` ma wartość null, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="e54fc-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e54fc-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e54fc-111">Return Value</span></span>  
 <span data-ttu-id="e54fc-112">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="e54fc-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e54fc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e54fc-113">HRESULT</span></span>|<span data-ttu-id="e54fc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e54fc-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e54fc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e54fc-115">S_OK</span></span>|<span data-ttu-id="e54fc-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e54fc-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="e54fc-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e54fc-117">E_POINTER</span></span>|`pwzBuffer` <span data-ttu-id="e54fc-118">lub `pchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="e54fc-118">or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e54fc-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e54fc-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e54fc-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e54fc-120">Requirements</span></span>  
 <span data-ttu-id="e54fc-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e54fc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e54fc-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e54fc-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e54fc-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e54fc-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e54fc-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e54fc-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e54fc-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e54fc-125">See also</span></span>

- [<span data-ttu-id="e54fc-126">ICLRRuntimeInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e54fc-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e54fc-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="e54fc-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
