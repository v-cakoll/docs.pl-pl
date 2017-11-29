---
title: "ICLRRuntimeInfo::GetRuntimeDirectory — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetRuntimeDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddaca8232f0b262377c7915852da89cecec09993
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="89c53-102">ICLRRuntimeInfo::GetRuntimeDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="89c53-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="89c53-103">Pobiera katalog instalacyjny programu środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z tym interfejsem.</span><span class="sxs-lookup"><span data-stu-id="89c53-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="89c53-104">Ta metoda zastępuje [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) funkcji dostępnych w wersji systemu .NET Framework 2.0, 3.0 i 3.5.</span><span class="sxs-lookup"><span data-stu-id="89c53-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c53-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="89c53-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89c53-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89c53-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="89c53-107">[out] Zwraca katalog instalacyjny środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="89c53-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="89c53-108">Ścieżka instalacji jest w pełni kwalifikowana; na przykład "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="89c53-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="89c53-109">[w, out] Określa rozmiar `pwzBuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="89c53-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="89c53-110">Jeśli `pwzBuffer` ma wartość null, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="89c53-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89c53-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="89c53-111">Return Value</span></span>  
 <span data-ttu-id="89c53-112">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="89c53-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89c53-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89c53-113">HRESULT</span></span>|<span data-ttu-id="89c53-114">Opis</span><span class="sxs-lookup"><span data-stu-id="89c53-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89c53-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="89c53-115">S_OK</span></span>|<span data-ttu-id="89c53-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="89c53-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="89c53-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="89c53-117">E_POINTER</span></span>|<span data-ttu-id="89c53-118">`pwzBuffer`lub `pchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="89c53-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89c53-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89c53-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89c53-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89c53-120">Requirements</span></span>  
 <span data-ttu-id="89c53-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89c53-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89c53-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="89c53-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="89c53-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89c53-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89c53-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89c53-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89c53-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89c53-125">See Also</span></span>  
 [<span data-ttu-id="89c53-126">ICLRRuntimeInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="89c53-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="89c53-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="89c53-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
