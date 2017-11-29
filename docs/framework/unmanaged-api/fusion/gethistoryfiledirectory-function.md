---
title: "GetHistoryFileDirectory — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHistoryFileDirectory
api_location: fusion.dll
api_type: DLLExport
f1_keywords: GetHistoryFileDirectory
helpviewer_keywords: GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f01100140e9e1dd05cb42b3cfe586c5f6462444c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="facda-102">GetHistoryFileDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="facda-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="facda-103">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="facda-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="facda-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="facda-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="facda-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="facda-106">[out] Bufor do przechowywania ścieżkę do katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="facda-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="facda-107">[w, out] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="facda-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="facda-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="facda-108">Return Value</span></span>  
 <span data-ttu-id="facda-109">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="facda-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="facda-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="facda-110">Return code</span></span>|<span data-ttu-id="facda-111">Opis</span><span class="sxs-lookup"><span data-stu-id="facda-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="facda-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="facda-112">S_OK</span></span>|<span data-ttu-id="facda-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="facda-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="facda-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="facda-114">E_INVALIDARG</span></span>|<span data-ttu-id="facda-115">`wzDir`lub `pdwSize` ma wartość null lub wersja parametry są niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="facda-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="facda-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="facda-116">Remarks</span></span>  
 <span data-ttu-id="facda-117">Po pomyślnym ukończeniu `pdwSize` argument ma wartość długości ciągu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="facda-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facda-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="facda-118">Requirements</span></span>  
 <span data-ttu-id="facda-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="facda-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facda-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="facda-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="facda-121">**Biblioteka:** Fusion.dll i Mscorwks.dll.a;a;pierwsza.</span><span class="sxs-lookup"><span data-stu-id="facda-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="facda-122">Użyj Fusion.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="facda-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="facda-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facda-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facda-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="facda-124">See Also</span></span>  
 [<span data-ttu-id="facda-125">Createhistoryreader — funkcja</span><span class="sxs-lookup"><span data-stu-id="facda-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="facda-126">Nukedownloadedcache — funkcja</span><span class="sxs-lookup"><span data-stu-id="facda-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="facda-127">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="facda-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
