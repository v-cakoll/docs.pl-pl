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
ms.openlocfilehash: e09391af9b5d71cfa423b3bf1a2b307117d0dee1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385890"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="da220-102">\_AxlRSAKeyValueToPublicKeyToken — funkcja</span><span class="sxs-lookup"><span data-stu-id="da220-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="da220-103">Konwertuje wyznaczanie modułu i wykładnik silnej nazwy token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="da220-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da220-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da220-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
### <a name="parameters"></a><span data-ttu-id="da220-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da220-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="da220-106">[in] Zakodowane w formacie base64 blob modulo (z \<modulo > element).</span><span class="sxs-lookup"><span data-stu-id="da220-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="da220-107">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="da220-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="da220-108">[in] Wykładnik algorytmem Base64 obiekt blob (z \<wykładnik > element).</span><span class="sxs-lookup"><span data-stu-id="da220-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="da220-109">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="da220-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="da220-110">[out] Wskaźnik do WCHAR \* do odbierania zakodowanego szesnastkowo token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="da220-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da220-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="da220-111">Return Value</span></span>  
 <span data-ttu-id="da220-112">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="da220-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="da220-113">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="da220-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da220-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da220-114">See Also</span></span>  
 [<span data-ttu-id="da220-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="da220-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
