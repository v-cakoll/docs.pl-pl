---
title: Funkcja _AxlGetIssuerPublicKeyHash
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408b71bf38427d12418e05f8b509fe841bc95ef1
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752332"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="0441d-102">Funkcja _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="0441d-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="0441d-103">Pobiera Skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0441d-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0441d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0441d-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0441d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0441d-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="0441d-106">[in] Dostawcy usług Kryptograficznych blob klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="0441d-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="0441d-107">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="0441d-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="0441d-108">[out] Wskaźnik do WCHAR \* do odbierania zakodowanego szesnastkowo token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="0441d-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0441d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0441d-109">Return Value</span></span>  
 <span data-ttu-id="0441d-110">`S_OK` Jeśli funkcja się powiedzie; w przeciwnym razie `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="0441d-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0441d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0441d-111">See Also</span></span>  
 [<span data-ttu-id="0441d-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0441d-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
