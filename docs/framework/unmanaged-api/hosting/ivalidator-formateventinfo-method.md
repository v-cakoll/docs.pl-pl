---
title: "IValidator::FormatEventInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0775bf5a2370d9d05899af5bc414caf08b3401fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="33046-102">IValidator::FormatEventInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="33046-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="33046-103">Pobiera odpowiadający błąd sprawdzania poprawności określony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="33046-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33046-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33046-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33046-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33046-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="33046-106">[in] Wartość HRESULT, która została przekazana do obsługi błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="33046-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="33046-107">[in] A `VEContext` wystąpienia, które zawiera informacje o kontekście o błędzie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="33046-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="33046-108">[w, out] Ciąg, który zawiera komunikat zwrócony kod błędu.</span><span class="sxs-lookup"><span data-stu-id="33046-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="33046-109">[in] Maksymalna długość komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="33046-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="33046-110">[in] Bezpieczne tablica, która zawiera dodatkowe parametry opisujące błąd.</span><span class="sxs-lookup"><span data-stu-id="33046-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33046-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33046-111">Requirements</span></span>  
 <span data-ttu-id="33046-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33046-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33046-113">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="33046-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="33046-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33046-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33046-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33046-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33046-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33046-116">See Also</span></span>  
 
