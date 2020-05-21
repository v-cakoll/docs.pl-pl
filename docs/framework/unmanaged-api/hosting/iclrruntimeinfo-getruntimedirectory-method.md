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
ms.openlocfilehash: d744abf5c502e9b9510cf9fd6479149b6c2177cc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762217"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="7a83c-102">ICLRRuntimeInfo::GetRuntimeDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a83c-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="7a83c-103">Pobiera katalog instalacyjny środowiska uruchomieniowego języka wspólnego (CLR) skojarzonego z tym interfejsem.</span><span class="sxs-lookup"><span data-stu-id="7a83c-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="7a83c-104">Ta metoda zastępuje funkcję [GetCORSystemDirectory —](getcorsystemdirectory-function.md) w .NET Framework wersje 2,0, 3,0 i 3,5.</span><span class="sxs-lookup"><span data-stu-id="7a83c-104">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a83c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a83c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a83c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a83c-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="7a83c-107">określoną Zwraca katalog instalacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7a83c-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="7a83c-108">Ścieżka instalacji jest w pełni kwalifikowana; na przykład "c:\Windows\Microsoft.NET\Framework\v1.0.3705 \\ ".</span><span class="sxs-lookup"><span data-stu-id="7a83c-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="7a83c-109">[in. out] Określa rozmiar, `pwzBuffer` Aby zapobiec przekroczeniu buforu.</span><span class="sxs-lookup"><span data-stu-id="7a83c-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="7a83c-110">Jeśli `pwzBuffer` ma wartość null, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="7a83c-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a83c-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7a83c-111">Return Value</span></span>  
 <span data-ttu-id="7a83c-112">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="7a83c-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7a83c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a83c-113">HRESULT</span></span>|<span data-ttu-id="7a83c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7a83c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a83c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a83c-115">S_OK</span></span>|<span data-ttu-id="7a83c-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7a83c-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="7a83c-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7a83c-117">E_POINTER</span></span>|<span data-ttu-id="7a83c-118">`pwzBuffer`lub `pchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="7a83c-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a83c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a83c-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a83c-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a83c-120">Requirements</span></span>  
 <span data-ttu-id="7a83c-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a83c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a83c-122">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="7a83c-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7a83c-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7a83c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a83c-124">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a83c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a83c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a83c-125">See also</span></span>

- [<span data-ttu-id="7a83c-126">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a83c-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7a83c-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="7a83c-127">Hosting</span></span>](index.md)
