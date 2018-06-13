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
ms.openlocfilehash: 463bcf451574700d02f933d024ea5c24cedd259d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441818"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="61d64-102">LoadStringRC — Funkcja</span><span class="sxs-lookup"><span data-stu-id="61d64-102">LoadStringRC Function</span></span>
<span data-ttu-id="61d64-103">Tłumaczy wartość HRESULT na komunikat o błędzie, za pomocą domyślną kulturę bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="61d64-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="61d64-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61d64-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61d64-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="61d64-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61d64-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="61d64-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="61d64-107">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="61d64-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="61d64-108">[out] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="61d64-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="61d64-109">[in] Rozmiar buforu komunikatu błędu.</span><span class="sxs-lookup"><span data-stu-id="61d64-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="61d64-110">[in] Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="61d64-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61d64-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61d64-111">Return Value</span></span>  
 <span data-ttu-id="61d64-112">Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="61d64-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="61d64-113">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="61d64-113">Return code</span></span>|<span data-ttu-id="61d64-114">Opis</span><span class="sxs-lookup"><span data-stu-id="61d64-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="61d64-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="61d64-115">S_OK</span></span>|<span data-ttu-id="61d64-116">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="61d64-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="61d64-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="61d64-117">E_INVALIDARG</span></span>|<span data-ttu-id="61d64-118">`szBuffer` ma wartość null lub `iMax` wynosi zero (0).</span><span class="sxs-lookup"><span data-stu-id="61d64-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61d64-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61d64-119">Remarks</span></span>  
 <span data-ttu-id="61d64-120">Jeśli metoda nie została zakończona pomyślnie, `szBuffer` zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="61d64-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61d64-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61d64-121">Requirements</span></span>  
 <span data-ttu-id="61d64-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61d64-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61d64-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61d64-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61d64-124">**Biblioteka:** biblioteki MSCorEE.dll i Mscorwks.dll.a;a;pierwsza.</span><span class="sxs-lookup"><span data-stu-id="61d64-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="61d64-125">Użyj biblioteki MSCorEE.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61d64-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="61d64-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61d64-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d64-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61d64-127">See Also</span></span>  
 [<span data-ttu-id="61d64-128">LoadStringRCEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="61d64-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [<span data-ttu-id="61d64-129">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="61d64-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
