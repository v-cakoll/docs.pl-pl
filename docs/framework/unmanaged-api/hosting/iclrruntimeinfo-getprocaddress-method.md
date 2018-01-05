---
title: "ICLRRuntimeInfo::GetProcAddress — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetProcAddress
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2878b23a2f848657e1d26b3bfb8395f8897c0632
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="37807-102">ICLRRuntimeInfo::GetProcAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="37807-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="37807-103">Pobiera adresu określonej funkcji, który został wyeksportowany z środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z tym interfejsem.</span><span class="sxs-lookup"><span data-stu-id="37807-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="37807-104">Ta metoda zastępuje [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="37807-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37807-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="37807-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37807-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37807-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="37807-107">[in] Nazwa wyeksportowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="37807-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="37807-108">[out] Adres wyeksportowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="37807-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37807-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37807-109">Return Value</span></span>  
 <span data-ttu-id="37807-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="37807-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="37807-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37807-111">HRESULT</span></span>|<span data-ttu-id="37807-112">Opis</span><span class="sxs-lookup"><span data-stu-id="37807-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37807-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="37807-113">S_OK</span></span>|<span data-ttu-id="37807-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="37807-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="37807-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="37807-115">E_POINTER</span></span>|<span data-ttu-id="37807-116">`pszProcName`lub `ppProc` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="37807-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="37807-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="37807-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="37807-118">Określona funkcja nie jest wyeksportowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="37807-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37807-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37807-119">Remarks</span></span>  
 <span data-ttu-id="37807-120">Ta metoda powoduje, że aparat CLR załadowane, ale nie został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="37807-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37807-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37807-121">Requirements</span></span>  
 <span data-ttu-id="37807-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37807-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37807-123">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="37807-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="37807-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37807-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37807-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37807-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37807-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37807-126">See Also</span></span>  
 [<span data-ttu-id="37807-127">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="37807-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="37807-128">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="37807-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="37807-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="37807-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
