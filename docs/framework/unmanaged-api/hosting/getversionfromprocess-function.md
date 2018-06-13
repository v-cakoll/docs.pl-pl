---
title: GetVersionFromProcess — Funkcja
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b57d04a8a49371872c679a331b5ae9c45dce797
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433076"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="62ed9-102">GetVersionFromProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="62ed9-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="62ed9-103">Pobiera środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z uchwytu procesu określonego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="62ed9-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="62ed9-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="62ed9-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ed9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="62ed9-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62ed9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62ed9-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="62ed9-107">[in] Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="62ed9-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="62ed9-108">[out] Bufor, który zawiera ciąg numer wersji po pomyślnym ukończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="62ed9-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="62ed9-109">[in] Długość buforu wersji.</span><span class="sxs-lookup"><span data-stu-id="62ed9-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="62ed9-110">[out] Wskaźnik do długości ciągu numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="62ed9-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62ed9-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62ed9-111">Return Value</span></span>  
 <span data-ttu-id="62ed9-112">Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="62ed9-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="62ed9-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="62ed9-113">Return code</span></span>|<span data-ttu-id="62ed9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="62ed9-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="62ed9-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="62ed9-115">S_OK</span></span>|<span data-ttu-id="62ed9-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="62ed9-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="62ed9-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="62ed9-117">E_INVALIDARG</span></span>|<span data-ttu-id="62ed9-118">`pVersion` ma wartość null i `cchBuffer` nie ma wartości null, lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="62ed9-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="62ed9-119">—lub—</span><span class="sxs-lookup"><span data-stu-id="62ed9-119">-or-</span></span><br /><br /> <span data-ttu-id="62ed9-120">`hProcess` nie jest prawidłowym dojściem do procesu.</span><span class="sxs-lookup"><span data-stu-id="62ed9-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="62ed9-121">—lub—</span><span class="sxs-lookup"><span data-stu-id="62ed9-121">-or-</span></span><br /><br /> <span data-ttu-id="62ed9-122">Nie załadowano środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="62ed9-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="62ed9-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="62ed9-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="62ed9-124">`cchBuffer` to wartość zerową lub mniejszą niż długość ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="62ed9-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="62ed9-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="62ed9-125">E_NOTIMPL</span></span>|<span data-ttu-id="62ed9-126">Ta metoda nie jest dostępna w systemie operacyjnym Microsoft Windows 95, Microsoft Windows 98 lub Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="62ed9-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62ed9-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62ed9-127">Requirements</span></span>  
 <span data-ttu-id="62ed9-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ed9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ed9-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62ed9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62ed9-130">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62ed9-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62ed9-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ed9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ed9-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62ed9-132">See Also</span></span>  
 [<span data-ttu-id="62ed9-133">GetRequestedRuntimeInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="62ed9-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="62ed9-134">GetRequestedRuntimeVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="62ed9-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="62ed9-135">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="62ed9-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
