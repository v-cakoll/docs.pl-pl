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
ms.openlocfilehash: a05cbe985c2cfebb67756fdfb54398b36e87f441
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008520"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="6ed63-102">LoadStringRCEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6ed63-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="6ed63-103">Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="6ed63-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="6ed63-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6ed63-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed63-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ed63-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6ed63-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ed63-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="6ed63-107">podczas Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="6ed63-107">[in] A culture identifier.</span></span> <span data-ttu-id="6ed63-108">Przekaż `lcid` wartość 1, aby użyć domyślnej kultury.</span><span class="sxs-lookup"><span data-stu-id="6ed63-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="6ed63-109">podczas WYNIK HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6ed63-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="6ed63-110">określoną Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6ed63-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="6ed63-111">podczas Rozmiar buforu komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="6ed63-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="6ed63-112">podczas Ignoruj.</span><span class="sxs-lookup"><span data-stu-id="6ed63-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="6ed63-113">określoną Wskaźnik do długości komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="6ed63-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ed63-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ed63-114">Return Value</span></span>  
 <span data-ttu-id="6ed63-115">Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="6ed63-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="6ed63-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="6ed63-116">Return code</span></span>|<span data-ttu-id="6ed63-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6ed63-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6ed63-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ed63-118">S_OK</span></span>|<span data-ttu-id="6ed63-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6ed63-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="6ed63-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6ed63-120">E_INVALIDARG</span></span>|<span data-ttu-id="6ed63-121">`szBuffer`ma wartość null lub `iMax` jest równa zero (0).</span><span class="sxs-lookup"><span data-stu-id="6ed63-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ed63-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ed63-122">Remarks</span></span>  
 <span data-ttu-id="6ed63-123">Jeśli metoda nie zakończy się pomyślnie, `szBuffer` zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="6ed63-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed63-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ed63-124">Requirements</span></span>  
 <span data-ttu-id="6ed63-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed63-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed63-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ed63-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ed63-127">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ed63-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ed63-128">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed63-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed63-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ed63-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6ed63-130">LoadStringRC, funkcja</span><span class="sxs-lookup"><span data-stu-id="6ed63-130">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="6ed63-131">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="6ed63-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
