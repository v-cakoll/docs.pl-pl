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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e020b65966dc03bf326220ab0bab26bc61155c0c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485489"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="a3585-102">LoadStringRC — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a3585-102">LoadStringRC Function</span></span>
<span data-ttu-id="a3585-103">Tłumaczy wartość HRESULT na komunikat o błędzie przy użyciu domyślnej kultury bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="a3585-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="a3585-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3585-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3585-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3585-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3585-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3585-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="a3585-107">[in] Wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a3585-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="a3585-108">[out] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="a3585-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="a3585-109">[in] Rozmiar buforu komunikatu błędu.</span><span class="sxs-lookup"><span data-stu-id="a3585-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="a3585-110">[in] Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a3585-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3585-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3585-111">Return Value</span></span>  
 <span data-ttu-id="a3585-112">Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="a3585-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a3585-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="a3585-113">Return code</span></span>|<span data-ttu-id="a3585-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a3585-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a3585-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3585-115">S_OK</span></span>|<span data-ttu-id="a3585-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a3585-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a3585-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a3585-117">E_INVALIDARG</span></span>|<span data-ttu-id="a3585-118">`szBuffer` ma wartość null lub `iMax` wynosi zero (0).</span><span class="sxs-lookup"><span data-stu-id="a3585-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3585-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3585-119">Remarks</span></span>  
 <span data-ttu-id="a3585-120">Jeśli metoda nie została zakończona pomyślnie, `szBuffer` zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="a3585-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3585-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3585-121">Requirements</span></span>  
 <span data-ttu-id="a3585-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3585-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3585-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3585-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3585-124">**Biblioteka:** MSCorEE.dll i Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="a3585-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="a3585-125">Użyj MSCorEE.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3585-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a3585-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3585-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3585-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3585-127">See also</span></span>
- [<span data-ttu-id="a3585-128">LoadStringRCEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="a3585-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="a3585-129">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a3585-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
