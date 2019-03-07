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
ms.openlocfilehash: 640940cea30b489683972debdd14b592d565ef4b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469694"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="010fe-102">\_AxlRSAKeyValueToPublicKeyToken — funkcja</span><span class="sxs-lookup"><span data-stu-id="010fe-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="010fe-103">Konwertuje wyznaczanie modułu i wykładnik silnej nazwy token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="010fe-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="010fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="010fe-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="010fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="010fe-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="010fe-106">[in] Zakodowane w formacie base64 blob modulo (z \<modulo > element).</span><span class="sxs-lookup"><span data-stu-id="010fe-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="010fe-107">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="010fe-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="010fe-108">[in] Wykładnik algorytmem Base64 obiekt blob (z \<wykładnik > element).</span><span class="sxs-lookup"><span data-stu-id="010fe-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="010fe-109">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="010fe-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="010fe-110">[out] Wskaźnik do WCHAR \* do odbierania zakodowanego szesnastkowo token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="010fe-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="010fe-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="010fe-111">Return Value</span></span>  
 <span data-ttu-id="010fe-112">`S_OK` Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="010fe-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="010fe-113">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="010fe-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="010fe-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="010fe-114">See also</span></span>
- [<span data-ttu-id="010fe-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="010fe-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
