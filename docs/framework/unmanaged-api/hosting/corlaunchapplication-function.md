---
title: "CorLaunchApplication — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type: COM
f1_keywords: CorLaunchApplication
helpviewer_keywords: CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6246ab600438e2237dcbe531d9d7641c0897d81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="98b39-102">CorLaunchApplication — Funkcja</span><span class="sxs-lookup"><span data-stu-id="98b39-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="98b39-103">Uruchamia aplikację w ścieżce określonej sieci przy użyciu określonego manifestów i innych danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98b39-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="98b39-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98b39-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98b39-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="98b39-105">Syntax</span></span>  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98b39-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="98b39-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="98b39-107">[in] Wartość [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) wyliczenie określający typ hosta, który jest uruchomienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98b39-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="98b39-108">[in] Pełna nazwa aplikacji, w której jest on uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="98b39-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="98b39-109">[in] Liczba ścieżek manifestu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98b39-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="98b39-110">[in] Tablica ciągów, z których każdy określa ścieżkę do manifestu dla aplikacji, która jest jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="98b39-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="98b39-111">[in] Liczba elementów danych aktywacji dla aplikacji, która jest jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="98b39-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="98b39-112">[in] Tablica ciągów, z których każdy jest element danych aktywacji dla aplikacji, która jest jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="98b39-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="98b39-113">[out] Wskaźnik do informacji na temat procesu, w którym został załadowany w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98b39-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98b39-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98b39-114">Requirements</span></span>  
 <span data-ttu-id="98b39-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98b39-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98b39-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="98b39-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98b39-117">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98b39-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98b39-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98b39-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b39-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98b39-119">See Also</span></span>  
 [<span data-ttu-id="98b39-120">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="98b39-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
