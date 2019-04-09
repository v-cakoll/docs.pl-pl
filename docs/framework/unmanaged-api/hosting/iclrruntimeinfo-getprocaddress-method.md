---
title: ICLRRuntimeInfo::GetProcAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a95b6b7e20bbcd86dedf187c932f2cf74d37cdab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199183"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="a2539-102">ICLRRuntimeInfo::GetProcAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2539-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="a2539-103">Pobiera adres określonej funkcji, która została wyeksportowana z środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z tym interfejsem.</span><span class="sxs-lookup"><span data-stu-id="a2539-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="a2539-104">Ta metoda zastępuje [getrealprocaddress —](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="a2539-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2539-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2539-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2539-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2539-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="a2539-107">[in] Nazwa eksportowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a2539-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="a2539-108">[out] Adres eksportowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a2539-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2539-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2539-109">Return Value</span></span>  
 <span data-ttu-id="a2539-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a2539-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a2539-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2539-111">HRESULT</span></span>|<span data-ttu-id="a2539-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a2539-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2539-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2539-113">S_OK</span></span>|<span data-ttu-id="a2539-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a2539-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="a2539-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a2539-115">E_POINTER</span></span>|`pszProcName` <span data-ttu-id="a2539-116">lub `ppProc` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a2539-116">or `ppProc` is null.</span></span>|  
|<span data-ttu-id="a2539-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="a2539-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="a2539-118">Określona funkcja nie jest eksportowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a2539-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2539-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2539-119">Remarks</span></span>  
 <span data-ttu-id="a2539-120">Ta metoda powoduje, że CLR do załadowane, ale nie zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="a2539-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2539-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2539-121">Requirements</span></span>  
 <span data-ttu-id="a2539-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2539-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2539-123">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a2539-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a2539-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2539-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a2539-125">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a2539-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a2539-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2539-126">See also</span></span>

- [<span data-ttu-id="a2539-127">ICLRRuntimeInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a2539-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="a2539-128">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a2539-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a2539-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="a2539-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
