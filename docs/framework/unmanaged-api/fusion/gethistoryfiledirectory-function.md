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
ms.openlocfilehash: bba40acf7bfd20897ece4de285fe7a9175be83e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431766"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="b6615-102">GetHistoryFileDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b6615-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="b6615-103">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6615-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6615-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6615-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6615-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6615-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="b6615-106">[out] Bufor do przechowywania ścieżkę do katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6615-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="b6615-107">[w, out] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="b6615-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6615-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b6615-108">Return Value</span></span>  
 <span data-ttu-id="b6615-109">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="b6615-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="b6615-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="b6615-110">Return code</span></span>|<span data-ttu-id="b6615-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b6615-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b6615-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6615-112">S_OK</span></span>|<span data-ttu-id="b6615-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b6615-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b6615-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b6615-114">E_INVALIDARG</span></span>|<span data-ttu-id="b6615-115">`wzDir` lub `pdwSize` ma wartość null lub wersja parametry są niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="b6615-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6615-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6615-116">Remarks</span></span>  
 <span data-ttu-id="b6615-117">Po pomyślnym ukończeniu `pdwSize` argument ma wartość długości ciągu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b6615-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6615-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6615-118">Requirements</span></span>  
 <span data-ttu-id="b6615-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6615-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6615-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b6615-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b6615-121">**Biblioteka:** Fusion.dll i Mscorwks.dll.a;a;pierwsza.</span><span class="sxs-lookup"><span data-stu-id="b6615-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="b6615-122">Użyj Fusion.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6615-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b6615-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6615-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6615-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6615-124">See Also</span></span>  
 [<span data-ttu-id="b6615-125">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="b6615-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="b6615-126">NukeDownloadedCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="b6615-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="b6615-127">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b6615-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
