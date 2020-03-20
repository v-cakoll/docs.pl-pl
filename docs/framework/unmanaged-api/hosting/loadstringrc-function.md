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
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176243"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="156cb-102">LoadStringRC — Funkcja</span><span class="sxs-lookup"><span data-stu-id="156cb-102">LoadStringRC Function</span></span>
<span data-ttu-id="156cb-103">Tłumaczy wartość HRESULT na komunikat o błędzie przy użyciu domyślnej kultury bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="156cb-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="156cb-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="156cb-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156cb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="156cb-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="156cb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="156cb-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="156cb-107">[w] An HRESULT.</span><span class="sxs-lookup"><span data-stu-id="156cb-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="156cb-108">[na zewnątrz] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="156cb-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="156cb-109">[w] Rozmiar buforu komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="156cb-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="156cb-110">[w] Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="156cb-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="156cb-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="156cb-111">Return Value</span></span>  
 <span data-ttu-id="156cb-112">Ta metoda zwraca standardowe kody błędów modelu com (Component Object Model), zgodnie z definicją w pliku WinError.h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="156cb-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="156cb-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="156cb-113">Return code</span></span>|<span data-ttu-id="156cb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="156cb-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="156cb-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="156cb-115">S_OK</span></span>|<span data-ttu-id="156cb-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="156cb-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="156cb-117">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="156cb-117">E_INVALIDARG</span></span>|<span data-ttu-id="156cb-118">`szBuffer`jest zerowa lub `iMax` wynosi zero (0).</span><span class="sxs-lookup"><span data-stu-id="156cb-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="156cb-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="156cb-119">Remarks</span></span>  
 <span data-ttu-id="156cb-120">Jeśli metoda nie zostanie `szBuffer` ukończona pomyślnie, zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="156cb-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="156cb-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="156cb-121">Requirements</span></span>  
 <span data-ttu-id="156cb-122">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="156cb-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="156cb-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="156cb-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="156cb-124">**Biblioteka:** plik MSCorEE.dll i Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="156cb-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="156cb-125">Użyj pliku MSCorEE.dll zamiast pliku Mscorwks.dll, aby upewnić się, że jest to właściwa wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="156cb-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="156cb-126">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="156cb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156cb-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="156cb-127">See also</span></span>

- [<span data-ttu-id="156cb-128">LoadStringRCEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="156cb-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="156cb-129">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="156cb-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
