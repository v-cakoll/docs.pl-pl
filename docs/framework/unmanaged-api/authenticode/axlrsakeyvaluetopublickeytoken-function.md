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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eca6c5fc61d4f7e80046102a560d228fc01e5292
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038418"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="8b90e-102">\_AxlRSAKeyValueToPublicKeyToken, funkcja</span><span class="sxs-lookup"><span data-stu-id="8b90e-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="8b90e-103">Konwertuje modulo i wykładnik na token klucza publicznego o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8b90e-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b90e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b90e-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b90e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b90e-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="8b90e-106">podczas Obiekt BLOB modułu kodowanego algorytmem Base64 ( \<z elementu > modułu).</span><span class="sxs-lookup"><span data-stu-id="8b90e-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="8b90e-107">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="8b90e-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="8b90e-108">podczas Obiekt BLOB wykładnika zakodowany algorytmem Base64 \<(z elementu wykładnika >).</span><span class="sxs-lookup"><span data-stu-id="8b90e-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="8b90e-109">Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="8b90e-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="8b90e-110">określoną Wskaźnik do WCHAR \*, aby otrzymać token klucza publicznego zakodowany w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="8b90e-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b90e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b90e-111">Return Value</span></span>  
 <span data-ttu-id="8b90e-112">`S_OK`Jeśli funkcja się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="8b90e-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="8b90e-113">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8b90e-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b90e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b90e-114">See also</span></span>

- [<span data-ttu-id="8b90e-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8b90e-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
