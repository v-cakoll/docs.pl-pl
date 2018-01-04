---
title: "GetVersionFromProcess — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetVersionFromProcess
helpviewer_keywords: GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db5054ab9b71eb93005fc0315acba82d807487ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="bd3fa-102">GetVersionFromProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bd3fa-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="bd3fa-103">Pobiera środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z uchwytu procesu określonego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="bd3fa-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd3fa-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd3fa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd3fa-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd3fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd3fa-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="bd3fa-107">[in] Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="bd3fa-108">[out] Bufor, który zawiera ciąg numer wersji po pomyślnym ukończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="bd3fa-109">[in] Długość buforu wersji.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="bd3fa-110">[out] Wskaźnik do długości ciągu numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd3fa-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd3fa-111">Return Value</span></span>  
 <span data-ttu-id="bd3fa-112">Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="bd3fa-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="bd3fa-113">Return code</span></span>|<span data-ttu-id="bd3fa-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bd3fa-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bd3fa-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd3fa-115">S_OK</span></span>|<span data-ttu-id="bd3fa-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="bd3fa-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bd3fa-117">E_INVALIDARG</span></span>|<span data-ttu-id="bd3fa-118">`pVersion`ma wartość null i `cchBuffer` nie ma wartości null, lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="bd3fa-119">—lub—</span><span class="sxs-lookup"><span data-stu-id="bd3fa-119">-or-</span></span><br /><br /> <span data-ttu-id="bd3fa-120">`hProcess`nie jest prawidłowym dojściem do procesu.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="bd3fa-121">—lub—</span><span class="sxs-lookup"><span data-stu-id="bd3fa-121">-or-</span></span><br /><br /> <span data-ttu-id="bd3fa-122">Nie załadowano środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="bd3fa-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="bd3fa-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="bd3fa-124">`cchBuffer`to wartość zerową lub mniejszą niż długość ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="bd3fa-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="bd3fa-125">E_NOTIMPL</span></span>|<span data-ttu-id="bd3fa-126">Ta metoda nie jest dostępna w systemie operacyjnym Microsoft Windows 95, Microsoft Windows 98 lub Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd3fa-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd3fa-127">Requirements</span></span>  
 <span data-ttu-id="bd3fa-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd3fa-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd3fa-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd3fa-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd3fa-130">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd3fa-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd3fa-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd3fa-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd3fa-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd3fa-132">See Also</span></span>  
 [<span data-ttu-id="bd3fa-133">GetRequestedRuntimeInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="bd3fa-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="bd3fa-134">GetRequestedRuntimeVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="bd3fa-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="bd3fa-135">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="bd3fa-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
