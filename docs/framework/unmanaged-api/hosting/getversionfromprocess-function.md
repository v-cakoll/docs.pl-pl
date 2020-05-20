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
ms.openlocfilehash: fbaf45da0902ded8a2f7bf0d470aaed3b5f531aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617129"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="2ebb1-102">GetVersionFromProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2ebb1-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="2ebb1-103">Pobiera numer wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest skojarzony z określonym dojściem do procesu.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="2ebb1-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ebb1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ebb1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ebb1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ebb1-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="2ebb1-107">podczas Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="2ebb1-108">określoną Bufor zawierający ciąg numeru wersji po pomyślnym zakończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2ebb1-109">podczas Długość buforu wersji.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="2ebb1-110">określoną Wskaźnik do długości ciągu numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ebb1-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ebb1-111">Return Value</span></span>  
 <span data-ttu-id="2ebb1-112">Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="2ebb1-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="2ebb1-113">Return code</span></span>|<span data-ttu-id="2ebb1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2ebb1-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2ebb1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ebb1-115">S_OK</span></span>|<span data-ttu-id="2ebb1-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="2ebb1-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2ebb1-117">E_INVALIDARG</span></span>|<span data-ttu-id="2ebb1-118">`pVersion`ma wartość null i `cchBuffer` nie ma wartości null lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="2ebb1-119">-lub-</span><span class="sxs-lookup"><span data-stu-id="2ebb1-119">-or-</span></span><br /><br /> <span data-ttu-id="2ebb1-120">`hProcess`nie jest prawidłowym dojściem do procesu.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="2ebb1-121">-lub-</span><span class="sxs-lookup"><span data-stu-id="2ebb1-121">-or-</span></span><br /><br /> <span data-ttu-id="2ebb1-122">Środowisko CLR nie jest załadowane.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="2ebb1-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2ebb1-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2ebb1-124">`cchBuffer`ma wartość null lub jest mniejsza niż długość ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="2ebb1-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2ebb1-125">E_NOTIMPL</span></span>|<span data-ttu-id="2ebb1-126">Ta metoda nie jest dostępna w systemie operacyjnym Microsoft Windows 95, Microsoft Windows 98 lub Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="2ebb1-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ebb1-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ebb1-127">Requirements</span></span>  
 <span data-ttu-id="2ebb1-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ebb1-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ebb1-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2ebb1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ebb1-130">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2ebb1-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ebb1-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ebb1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ebb1-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ebb1-132">See also</span></span>

- [<span data-ttu-id="2ebb1-133">GetRequestedRuntimeInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="2ebb1-133">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="2ebb1-134">GetRequestedRuntimeVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2ebb1-134">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="2ebb1-135">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2ebb1-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
