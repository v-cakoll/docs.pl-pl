---
title: Funkcja _AxlRSAKeyValueToPublicKeyToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4af27a2abf1a0bcf4d79eda389c5f79f0ecb1eef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="3f15e-102">Funkcja _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="3f15e-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="3f15e-103">Konwertuje modulo i wykładnik silnej nazwy tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3f15e-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f15e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f15e-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f15e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f15e-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="3f15e-106">[in] Obiekt blob modulo algorytmem Base64 (z \<modulo > elementu).</span><span class="sxs-lookup"><span data-stu-id="3f15e-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="3f15e-107">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="3f15e-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="3f15e-108">[in] Obiekt blob wykładnik algorytmem Base64 (z \<wykładnik > elementu).</span><span class="sxs-lookup"><span data-stu-id="3f15e-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="3f15e-109">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="3f15e-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="3f15e-110">[out] Wskaźnik do WCHAR * do odbierania zakodowane w systemie szesnastkowym token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3f15e-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f15e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3f15e-111">Return Value</span></span>  
 <span data-ttu-id="3f15e-112">`S_OK`Jeśli funkcja zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3f15e-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="3f15e-113">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3f15e-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f15e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f15e-114">See Also</span></span>  
 [<span data-ttu-id="3f15e-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3f15e-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
