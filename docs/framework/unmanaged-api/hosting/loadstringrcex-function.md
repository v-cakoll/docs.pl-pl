---
title: LoadStringRCEx — Funkcja
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38c942b9a94c83f5a3316cf3ae3ccbbad2b0ec69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="6b3ec-102">LoadStringRCEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6b3ec-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="6b3ec-103">Tłumaczy wartość HRESULT odpowiedni komunikat o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="6b3ec-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b3ec-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b3ec-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b3ec-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b3ec-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b3ec-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="6b3ec-107">[in] Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-107">[in] A culture identifier.</span></span> <span data-ttu-id="6b3ec-108">Podaj wartość -1 dla `lcid` do użycia domyślną kulturę.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="6b3ec-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="6b3ec-110">[out] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="6b3ec-111">[in] Rozmiar buforu komunikatu błędu.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="6b3ec-112">[in] Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="6b3ec-113">[out] Wskaźnik do długości komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b3ec-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b3ec-114">Return Value</span></span>  
 <span data-ttu-id="6b3ec-115">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="6b3ec-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="6b3ec-116">Return code</span></span>|<span data-ttu-id="6b3ec-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6b3ec-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6b3ec-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b3ec-118">S_OK</span></span>|<span data-ttu-id="6b3ec-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="6b3ec-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6b3ec-120">E_INVALIDARG</span></span>|<span data-ttu-id="6b3ec-121">`szBuffer` ma wartość null, lub `iMax` wynosi zero (0).</span><span class="sxs-lookup"><span data-stu-id="6b3ec-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b3ec-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b3ec-122">Remarks</span></span>  
 <span data-ttu-id="6b3ec-123">Jeśli metoda nie została zakończona pomyślnie, `szBuffer` zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="6b3ec-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b3ec-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b3ec-124">Requirements</span></span>  
 <span data-ttu-id="6b3ec-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b3ec-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b3ec-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b3ec-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b3ec-127">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b3ec-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b3ec-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b3ec-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3ec-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b3ec-129">See Also</span></span>  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="6b3ec-130">LoadStringRC, funkcja</span><span class="sxs-lookup"><span data-stu-id="6b3ec-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [<span data-ttu-id="6b3ec-131">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="6b3ec-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
