---
title: "GetHistoryFileDirectory — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d0ec18a4f95d0d280a66b3b9d9200c560f5f187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="f72d1-102">GetHistoryFileDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f72d1-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="f72d1-103">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f72d1-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f72d1-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f72d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f72d1-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="f72d1-106">[out] Bufor do przechowywania ścieżkę do katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f72d1-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="f72d1-107">[w, out] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="f72d1-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f72d1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f72d1-108">Return Value</span></span>  
 <span data-ttu-id="f72d1-109">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="f72d1-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="f72d1-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="f72d1-110">Return code</span></span>|<span data-ttu-id="f72d1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f72d1-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f72d1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f72d1-112">S_OK</span></span>|<span data-ttu-id="f72d1-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f72d1-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f72d1-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f72d1-114">E_INVALIDARG</span></span>|<span data-ttu-id="f72d1-115">`wzDir`lub `pdwSize` ma wartość null lub wersja parametry są niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="f72d1-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f72d1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f72d1-116">Remarks</span></span>  
 <span data-ttu-id="f72d1-117">Po pomyślnym ukończeniu `pdwSize` argument ma wartość długości ciągu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f72d1-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f72d1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f72d1-118">Requirements</span></span>  
 <span data-ttu-id="f72d1-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f72d1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f72d1-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f72d1-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f72d1-121">**Biblioteka:** Fusion.dll i Mscorwks.dll.a;a;pierwsza.</span><span class="sxs-lookup"><span data-stu-id="f72d1-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="f72d1-122">Użyj Fusion.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f72d1-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f72d1-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f72d1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72d1-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f72d1-124">See Also</span></span>  
 [<span data-ttu-id="f72d1-125">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="f72d1-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="f72d1-126">NukeDownloadedCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="f72d1-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="f72d1-127">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f72d1-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
