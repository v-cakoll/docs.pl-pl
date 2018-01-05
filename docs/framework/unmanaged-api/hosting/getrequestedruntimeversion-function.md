---
title: "GetRequestedRuntimeVersion — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersion
helpviewer_keywords: GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13309a7362f468d3711176db2adc7a82e3b949d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="3f258-102">GetRequestedRuntimeVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="3f258-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="3f258-103">Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR) wymagane przez określoną aplikacją.</span><span class="sxs-lookup"><span data-stu-id="3f258-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="3f258-104">Jeśli ta wersja nie jest zainstalowany, otrzymuje najnowszą wersję, która została zainstalowana przed żądanej wersji.</span><span class="sxs-lookup"><span data-stu-id="3f258-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="3f258-105">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f258-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f258-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f258-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f258-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f258-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="3f258-108">[in] Nazwa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f258-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="3f258-109">[out] Buforu, który zawiera ciąg numer wersji na pomyślne zakończenie.</span><span class="sxs-lookup"><span data-stu-id="3f258-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="3f258-110">[in] Długość buforu wersji.</span><span class="sxs-lookup"><span data-stu-id="3f258-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="3f258-111">[out] Wskaźnik do długości ciągu numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="3f258-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f258-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3f258-112">Return Value</span></span>  
 <span data-ttu-id="3f258-113">Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="3f258-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="3f258-114">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="3f258-114">Return code</span></span>|<span data-ttu-id="3f258-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3f258-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3f258-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f258-116">S_OK</span></span>|<span data-ttu-id="3f258-117">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3f258-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="3f258-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3f258-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3f258-119">Bufor wersji nie jest wystarczająco duży, aby zapisać ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="3f258-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="3f258-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3f258-120">E_POINTER</span></span>|<span data-ttu-id="3f258-121">`pdwLength`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="3f258-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f258-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f258-122">Requirements</span></span>  
 <span data-ttu-id="3f258-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f258-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f258-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f258-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f258-125">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f258-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f258-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f258-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f258-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f258-127">See Also</span></span>  
 [<span data-ttu-id="3f258-128">GetRequestedRuntimeInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="3f258-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="3f258-129">GetVersionFromProcess, funkcja</span><span class="sxs-lookup"><span data-stu-id="3f258-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="3f258-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="3f258-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
