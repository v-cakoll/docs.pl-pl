---
title: _AxlRSAKeyValueToPublicKeyToken, funkcja
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
ms.openlocfilehash: 1f53df33a65d3f75b7574eda3507e370c2e086ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099814"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="80595-102">\_funkcja AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="80595-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="80595-103">Konwertuje modulo i wykładnik na token klucza publicznego o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="80595-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80595-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80595-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80595-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80595-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="80595-106">podczas Obiekt BLOB modułu kodowanego algorytmem Base64 (z elementu \<moduł >).</span><span class="sxs-lookup"><span data-stu-id="80595-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="80595-107">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="80595-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="80595-108">podczas Obiekt BLOB wykładnika zakodowany algorytmem Base64 (z \<wykładnika > elementu).</span><span class="sxs-lookup"><span data-stu-id="80595-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="80595-109">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="80595-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="80595-110">określoną Wskaźnik do WCHAR \*, aby otrzymać token klucza publicznego zakodowany w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="80595-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80595-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80595-111">Return Value</span></span>  
 <span data-ttu-id="80595-112">`S_OK`, jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="80595-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="80595-113">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="80595-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80595-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80595-114">See also</span></span>

- [<span data-ttu-id="80595-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="80595-115">Authenticode</span></span>](index.md)
