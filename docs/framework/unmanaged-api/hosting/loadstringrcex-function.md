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
ms.openlocfilehash: 4a0cac77d7bf7611acf6042298bfe6814d8f4352
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768451"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="8b8e4-102">LoadStringRCEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8b8e4-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="8b8e4-103">Tłumaczy wartość HRESULT do odpowiedniego komunikatu o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="8b8e4-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b8e4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b8e4-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8b8e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b8e4-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="8b8e4-107">[in] Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-107">[in] A culture identifier.</span></span> <span data-ttu-id="8b8e4-108">Przekaż wartość -1 `lcid` używać domyślnej kultury.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="8b8e4-109">[in] Wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="8b8e4-110">[out] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="8b8e4-111">[in] Rozmiar buforu komunikatu błędu.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="8b8e4-112">[in] Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="8b8e4-113">[out] Wskaźnik do długości komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b8e4-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b8e4-114">Return Value</span></span>  
 <span data-ttu-id="8b8e4-115">Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="8b8e4-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="8b8e4-116">Return code</span></span>|<span data-ttu-id="8b8e4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8b8e4-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8b8e4-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b8e4-118">S_OK</span></span>|<span data-ttu-id="8b8e4-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="8b8e4-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8b8e4-120">E_INVALIDARG</span></span>|<span data-ttu-id="8b8e4-121">`szBuffer` ma wartość null, lub `iMax` wynosi zero (0).</span><span class="sxs-lookup"><span data-stu-id="8b8e4-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b8e4-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b8e4-122">Remarks</span></span>  
 <span data-ttu-id="8b8e4-123">Jeśli metoda nie została zakończona pomyślnie, `szBuffer` zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="8b8e4-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b8e4-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b8e4-124">Requirements</span></span>  
 <span data-ttu-id="8b8e4-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b8e4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b8e4-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8b8e4-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b8e4-127">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b8e4-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b8e4-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b8e4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8e4-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b8e4-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8b8e4-130">LoadStringRC, funkcja</span><span class="sxs-lookup"><span data-stu-id="8b8e4-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="8b8e4-131">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="8b8e4-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
