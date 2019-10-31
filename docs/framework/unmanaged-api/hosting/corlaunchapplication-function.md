---
title: CorLaunchApplication — Funkcja
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: e01698d2d8491b2496bb664c13dca97964cd1481
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136944"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="efe13-102">CorLaunchApplication — Funkcja</span><span class="sxs-lookup"><span data-stu-id="efe13-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="efe13-103">Uruchamia aplikację pod określoną ścieżką sieciową przy użyciu określonych manifestów i innych danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efe13-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="efe13-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="efe13-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe13-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="efe13-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="efe13-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="efe13-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="efe13-107">podczas Wartość wyliczenia [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) , która określa typ hosta, który uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="efe13-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="efe13-108">podczas Pełna nazwa aplikacji, która jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="efe13-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="efe13-109">podczas Liczba ścieżek manifestu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efe13-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="efe13-110">podczas Tablica ciągów, z których każdy określa ścieżkę do manifestu dla aplikacji, która jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="efe13-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="efe13-111">podczas Liczba elementów danych aktywacji dla aplikacji, która jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="efe13-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="efe13-112">podczas Tablica ciągów, z których każdy jest elementem danych aktywacji dla aplikacji, która jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="efe13-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="efe13-113">określoną Wskaźnik do informacji o procesie, w którym aplikacja została załadowana.</span><span class="sxs-lookup"><span data-stu-id="efe13-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe13-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efe13-114">Requirements</span></span>  
 <span data-ttu-id="efe13-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efe13-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efe13-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="efe13-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efe13-117">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efe13-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efe13-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efe13-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe13-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efe13-119">See also</span></span>

- [<span data-ttu-id="efe13-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="efe13-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
