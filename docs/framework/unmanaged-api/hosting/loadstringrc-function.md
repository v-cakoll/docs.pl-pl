---
title: LoadStringRC — Funkcja
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 66d4c14234c7929af443922f86098b46a4aa6eb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122015"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="dd421-102">LoadStringRC — Funkcja</span><span class="sxs-lookup"><span data-stu-id="dd421-102">LoadStringRC Function</span></span>
<span data-ttu-id="dd421-103">Tłumaczy wartość HRESULT na komunikat o błędzie przy użyciu domyślnej kultury bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="dd421-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="dd421-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dd421-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd421-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd421-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd421-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd421-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="dd421-107">podczas WYNIK HRESULT.</span><span class="sxs-lookup"><span data-stu-id="dd421-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="dd421-108">określoną Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="dd421-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="dd421-109">podczas Rozmiar buforu komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="dd421-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="dd421-110">podczas Ignoruj.</span><span class="sxs-lookup"><span data-stu-id="dd421-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd421-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd421-111">Return Value</span></span>  
 <span data-ttu-id="dd421-112">Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="dd421-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="dd421-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="dd421-113">Return code</span></span>|<span data-ttu-id="dd421-114">Opis</span><span class="sxs-lookup"><span data-stu-id="dd421-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="dd421-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd421-115">S_OK</span></span>|<span data-ttu-id="dd421-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dd421-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="dd421-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dd421-117">E_INVALIDARG</span></span>|<span data-ttu-id="dd421-118">`szBuffer` ma wartość null lub `iMax` wynosi zero (0).</span><span class="sxs-lookup"><span data-stu-id="dd421-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd421-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd421-119">Remarks</span></span>  
 <span data-ttu-id="dd421-120">Jeśli metoda nie zakończy się pomyślnie, `szBuffer` zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="dd421-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd421-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd421-121">Requirements</span></span>  
 <span data-ttu-id="dd421-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd421-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd421-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd421-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd421-124">**Biblioteka:** MSCorEE. dll i mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="dd421-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="dd421-125">Użyj biblioteki MSCorEE. dll zamiast Mscorwks. dll, aby upewnić się, że docelowa jest poprawna wersja .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd421-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="dd421-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd421-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd421-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd421-127">See also</span></span>

- [<span data-ttu-id="dd421-128">LoadStringRCEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="dd421-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="dd421-129">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dd421-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
