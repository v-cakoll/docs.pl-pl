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
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177979"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="95c23-102">LoadStringRCEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="95c23-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="95c23-103">Tłumaczy wartość HRESULT do odpowiedniego komunikatu o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="95c23-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="95c23-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="95c23-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c23-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="95c23-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95c23-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="95c23-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="95c23-107">[w] Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="95c23-107">[in] A culture identifier.</span></span> <span data-ttu-id="95c23-108">Przekaż -1, `lcid` aby użyć kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="95c23-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="95c23-109">[w] An HRESULT.</span><span class="sxs-lookup"><span data-stu-id="95c23-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="95c23-110">[na zewnątrz] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="95c23-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="95c23-111">[w] Rozmiar buforu komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="95c23-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="95c23-112">[w] Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="95c23-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="95c23-113">[na zewnątrz] Wskaźnik do długości komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="95c23-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95c23-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="95c23-114">Return Value</span></span>  
 <span data-ttu-id="95c23-115">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w winError.h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="95c23-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="95c23-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="95c23-116">Return code</span></span>|<span data-ttu-id="95c23-117">Opis</span><span class="sxs-lookup"><span data-stu-id="95c23-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="95c23-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="95c23-118">S_OK</span></span>|<span data-ttu-id="95c23-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="95c23-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="95c23-120">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="95c23-120">E_INVALIDARG</span></span>|<span data-ttu-id="95c23-121">`szBuffer`jest null `iMax` lub wynosi zero (0).</span><span class="sxs-lookup"><span data-stu-id="95c23-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95c23-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95c23-122">Remarks</span></span>  
 <span data-ttu-id="95c23-123">Jeśli metoda nie zostanie `szBuffer` ukończona pomyślnie, zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="95c23-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c23-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95c23-124">Requirements</span></span>  
 <span data-ttu-id="95c23-125">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c23-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c23-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95c23-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95c23-127">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="95c23-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95c23-128">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c23-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c23-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95c23-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="95c23-130">LoadStringRC, funkcja</span><span class="sxs-lookup"><span data-stu-id="95c23-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="95c23-131">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="95c23-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
