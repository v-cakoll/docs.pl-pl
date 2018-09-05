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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563679"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="04f47-102">Funkcja _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="04f47-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="04f47-103">Pobiera Skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="04f47-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04f47-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04f47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04f47-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="04f47-106">[in] Dostawcy usług Kryptograficznych blob klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="04f47-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="04f47-107">Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="04f47-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="04f47-108">[out] Wskaźnik do WCHAR \* do odbierania zakodowanego szesnastkowo token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="04f47-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04f47-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="04f47-109">Return Value</span></span>  
 <span data-ttu-id="04f47-110">`S_OK` Jeśli funkcja się powiedzie; w przeciwnym razie `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="04f47-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f47-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04f47-111">See Also</span></span>  
 [<span data-ttu-id="04f47-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="04f47-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
