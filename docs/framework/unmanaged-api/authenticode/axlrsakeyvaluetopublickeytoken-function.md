---
title: Funkcja _AxlRSAKeyValueToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ef73f0f7599fdff887437756a5995591fd8ec89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="2126e-102">Funkcja _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="2126e-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="2126e-103">Konwertuje modulo i wykładnik silnej nazwy tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="2126e-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2126e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2126e-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2126e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2126e-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="2126e-106">[in] Obiekt blob modulo algorytmem Base64 (z \<modulo > elementu).</span><span class="sxs-lookup"><span data-stu-id="2126e-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="2126e-107">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="2126e-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="2126e-108">[in] Obiekt blob wykładnik algorytmem Base64 (z \<wykładnik > elementu).</span><span class="sxs-lookup"><span data-stu-id="2126e-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="2126e-109">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="2126e-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="2126e-110">[out] Wskaźnik do WCHAR \* do odbierania zakodowane w systemie szesnastkowym token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="2126e-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2126e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2126e-111">Return Value</span></span>  
 <span data-ttu-id="2126e-112">`S_OK` Jeśli funkcja zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2126e-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2126e-113">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2126e-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2126e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2126e-114">See Also</span></span>  
 [<span data-ttu-id="2126e-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2126e-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
