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
ms.openlocfilehash: 1aabfad14ee2eb35916bbf115631602276cd1fc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109893"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="78e28-102">GetHistoryFileDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="78e28-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="78e28-103">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78e28-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78e28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78e28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78e28-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="78e28-106">określoną Bufor służący do przechowywania ścieżki do katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78e28-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="78e28-107">[in. out] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="78e28-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78e28-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="78e28-108">Return Value</span></span>  
 <span data-ttu-id="78e28-109">Ta metoda zwraca kody błędów standardowego modelu COM, jak zdefiniowano w pliku WinError. h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="78e28-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="78e28-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="78e28-110">Return code</span></span>|<span data-ttu-id="78e28-111">Opis</span><span class="sxs-lookup"><span data-stu-id="78e28-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="78e28-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="78e28-112">S_OK</span></span>|<span data-ttu-id="78e28-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="78e28-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="78e28-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="78e28-114">E_INVALIDARG</span></span>|<span data-ttu-id="78e28-115">`wzDir` lub `pdwSize` ma wartość null lub ciąg wersji jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="78e28-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e28-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78e28-116">Remarks</span></span>  
 <span data-ttu-id="78e28-117">Po pomyślnym zakończeniu wartość argumentu `pdwSize` jest ustawiana na długość ciągu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="78e28-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78e28-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78e28-118">Requirements</span></span>  
 <span data-ttu-id="78e28-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78e28-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e28-120">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="78e28-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="78e28-121">**Biblioteka:** Fusion. dll i mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="78e28-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="78e28-122">Aby upewnić się, że docelowa wersja .NET Framework, należy użyć pliku Fusion. dll zamiast Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="78e28-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="78e28-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e28-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e28-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78e28-124">See also</span></span>

- [<span data-ttu-id="78e28-125">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="78e28-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="78e28-126">NukeDownloadedCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="78e28-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="78e28-127">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="78e28-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
