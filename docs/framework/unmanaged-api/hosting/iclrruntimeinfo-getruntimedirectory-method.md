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
ms.openlocfilehash: b0a2e5f259fe1ee566f9cc25152b2d2a1f740bea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120341"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="50c8f-102">ICLRRuntimeInfo::GetRuntimeDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="50c8f-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="50c8f-103">Pobiera katalog instalacyjny środowiska uruchomieniowego języka wspólnego (CLR) skojarzonego z tym interfejsem.</span><span class="sxs-lookup"><span data-stu-id="50c8f-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="50c8f-104">Ta metoda zastępuje funkcję [GetCORSystemDirectory —](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) w .NET Framework wersje 2,0, 3,0 i 3,5.</span><span class="sxs-lookup"><span data-stu-id="50c8f-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c8f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="50c8f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50c8f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="50c8f-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="50c8f-107">określoną Zwraca katalog instalacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="50c8f-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="50c8f-108">Ścieżka instalacji jest w pełni kwalifikowana; na przykład "c:\Windows\Microsoft.NET\Framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="50c8f-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="50c8f-109">[in. out] Określa rozmiar `pwzBuffer`, aby uniknąć przekroczeń buforu.</span><span class="sxs-lookup"><span data-stu-id="50c8f-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="50c8f-110">Jeśli `pwzBuffer` ma wartość null, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="50c8f-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50c8f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50c8f-111">Return Value</span></span>  
 <span data-ttu-id="50c8f-112">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="50c8f-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="50c8f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50c8f-113">HRESULT</span></span>|<span data-ttu-id="50c8f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="50c8f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50c8f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="50c8f-115">S_OK</span></span>|<span data-ttu-id="50c8f-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="50c8f-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="50c8f-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="50c8f-117">E_POINTER</span></span>|<span data-ttu-id="50c8f-118">`pwzBuffer` lub `pchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="50c8f-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50c8f-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50c8f-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50c8f-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50c8f-120">Requirements</span></span>  
 <span data-ttu-id="50c8f-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50c8f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c8f-122">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="50c8f-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="50c8f-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="50c8f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50c8f-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c8f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c8f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50c8f-125">See also</span></span>

- [<span data-ttu-id="50c8f-126">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="50c8f-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="50c8f-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="50c8f-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
