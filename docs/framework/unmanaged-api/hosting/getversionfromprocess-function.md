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
ms.openlocfilehash: 843236243563ce3dff82726aaab05845fa295b9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518140"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="e8266-102">GetVersionFromProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e8266-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="e8266-103">Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z określonym dojściem do procesu.</span><span class="sxs-lookup"><span data-stu-id="e8266-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="e8266-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8266-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8266-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8266-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8266-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8266-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="e8266-107">[in] Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="e8266-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="e8266-108">[out] Bufor, który zawiera ciąg numeru wersji, po pomyślnym zakończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="e8266-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e8266-109">[in] Długość buforu wersji.</span><span class="sxs-lookup"><span data-stu-id="e8266-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="e8266-110">[out] Wskaźnik do długości ciągu numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="e8266-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8266-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e8266-111">Return Value</span></span>  
 <span data-ttu-id="e8266-112">Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="e8266-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="e8266-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="e8266-113">Return code</span></span>|<span data-ttu-id="e8266-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e8266-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e8266-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8266-115">S_OK</span></span>|<span data-ttu-id="e8266-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e8266-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="e8266-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e8266-117">E_INVALIDARG</span></span>|<span data-ttu-id="e8266-118">`pVersion` ma wartość null i `cchBuffer` nie ma wartości null, lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="e8266-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="e8266-119">—lub—</span><span class="sxs-lookup"><span data-stu-id="e8266-119">-or-</span></span><br /><br /> <span data-ttu-id="e8266-120">`hProcess` nie jest prawidłowym dojściem do procesu.</span><span class="sxs-lookup"><span data-stu-id="e8266-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="e8266-121">—lub—</span><span class="sxs-lookup"><span data-stu-id="e8266-121">-or-</span></span><br /><br /> <span data-ttu-id="e8266-122">Środowisko CLR nie został załadowany.</span><span class="sxs-lookup"><span data-stu-id="e8266-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="e8266-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e8266-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e8266-124">`cchBuffer` jest wartość null lub jest mniejsza niż długość ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="e8266-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="e8266-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e8266-125">E_NOTIMPL</span></span>|<span data-ttu-id="e8266-126">Ta metoda nie jest dostępna w systemie operacyjnym Microsoft Windows 95, Microsoft Windows 98 lub Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="e8266-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8266-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8266-127">Requirements</span></span>  
 <span data-ttu-id="e8266-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8266-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8266-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8266-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8266-130">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8266-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8266-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8266-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8266-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8266-132">See also</span></span>
- [<span data-ttu-id="e8266-133">GetRequestedRuntimeInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="e8266-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="e8266-134">GetRequestedRuntimeVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="e8266-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="e8266-135">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="e8266-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
