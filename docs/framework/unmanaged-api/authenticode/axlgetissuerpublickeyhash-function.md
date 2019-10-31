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
ms.openlocfilehash: 6d5ad995b55a3cde6363b297df6b8faf72689468
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132485"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="c5253-102">\_funkcja AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="c5253-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="c5253-103">Pobiera skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c5253-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5253-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5253-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5253-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5253-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="c5253-106">podczas Obiekt BLOB klucza publicznego dostawcy usług kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="c5253-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="c5253-107">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="c5253-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="c5253-108">określoną Wskaźnik do WCHAR \*, aby otrzymać token klucza publicznego zakodowany w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="c5253-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5253-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c5253-109">Return Value</span></span>  
 <span data-ttu-id="c5253-110">`S_OK`, jeśli funkcja się powiedzie; w przeciwnym razie `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="c5253-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5253-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5253-111">See also</span></span>

- [<span data-ttu-id="c5253-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c5253-112">Authenticode</span></span>](index.md)
