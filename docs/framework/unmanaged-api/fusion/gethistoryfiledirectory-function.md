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
ms.openlocfilehash: b60dde31707175a27d2dc6c50484d6089adaeaa6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229630"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="9a168-102">GetHistoryFileDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a168-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="9a168-103">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a168-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a168-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a168-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a168-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a168-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="9a168-106">[out] Bufor do przechowywania ścieżkę do katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a168-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="9a168-107">[out w] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="9a168-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a168-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9a168-108">Return Value</span></span>  
 <span data-ttu-id="9a168-109">Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="9a168-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="9a168-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="9a168-110">Return code</span></span>|<span data-ttu-id="9a168-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9a168-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9a168-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a168-112">S_OK</span></span>|<span data-ttu-id="9a168-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9a168-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="9a168-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9a168-114">E_INVALIDARG</span></span>|`wzDir` <span data-ttu-id="9a168-115">lub `pdwSize` ma wartość null lub wersji ciąg jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="9a168-115">or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a168-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a168-116">Remarks</span></span>  
 <span data-ttu-id="9a168-117">Po pomyślnym zakończeniu `pdwSize` argument jest równa długości ciągu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="9a168-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a168-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a168-118">Requirements</span></span>  
 <span data-ttu-id="9a168-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a168-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a168-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9a168-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9a168-121">**Biblioteka:** Fusion.dll i Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="9a168-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="9a168-122">Użyj Fusion.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a168-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 **<span data-ttu-id="9a168-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9a168-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a168-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a168-124">See also</span></span>

- [<span data-ttu-id="9a168-125">CreateHistoryReader — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a168-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="9a168-126">NukeDownloadedCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a168-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="9a168-127">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="9a168-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
