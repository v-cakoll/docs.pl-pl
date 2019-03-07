---
title: GetHistoryFileDirectory — Funkcja
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21742881c5aef7384be318297aa3432411c3d57c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479289"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="7bbcb-102">GetHistoryFileDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7bbcb-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="7bbcb-103">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bbcb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bbcb-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bbcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bbcb-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="7bbcb-106">[out] Bufor do przechowywania ścieżkę do katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="7bbcb-107">[out w] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bbcb-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7bbcb-108">Return Value</span></span>  
 <span data-ttu-id="7bbcb-109">Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="7bbcb-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="7bbcb-110">Return code</span></span>|<span data-ttu-id="7bbcb-111">Opis</span><span class="sxs-lookup"><span data-stu-id="7bbcb-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7bbcb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bbcb-112">S_OK</span></span>|<span data-ttu-id="7bbcb-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="7bbcb-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7bbcb-114">E_INVALIDARG</span></span>|<span data-ttu-id="7bbcb-115">`wzDir` lub `pdwSize` ma wartość null lub wersji ciąg jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bbcb-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bbcb-116">Remarks</span></span>  
 <span data-ttu-id="7bbcb-117">Po pomyślnym zakończeniu `pdwSize` argument jest równa długości ciągu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bbcb-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bbcb-118">Requirements</span></span>  
 <span data-ttu-id="7bbcb-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bbcb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bbcb-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7bbcb-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7bbcb-121">**Biblioteka:** Fusion.dll i Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="7bbcb-122">Użyj Fusion.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7bbcb-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="7bbcb-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bbcb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bbcb-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bbcb-124">See also</span></span>
- [<span data-ttu-id="7bbcb-125">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="7bbcb-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="7bbcb-126">NukeDownloadedCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="7bbcb-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="7bbcb-127">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="7bbcb-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
