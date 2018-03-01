---
title: Funkcja _AxlRSAKeyValueToPublicKeyToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="cbee8-102">Funkcja _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="cbee8-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="cbee8-103">Konwertuje modulo i wykładnik silnej nazwy tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="cbee8-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbee8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbee8-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbee8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbee8-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="cbee8-106">[in] Obiekt blob modulo algorytmem Base64 (z \<modulo > elementu).</span><span class="sxs-lookup"><span data-stu-id="cbee8-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="cbee8-107">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="cbee8-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="cbee8-108">[in] Obiekt blob wykładnik algorytmem Base64 (z \<wykładnik > elementu).</span><span class="sxs-lookup"><span data-stu-id="cbee8-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="cbee8-109">Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="cbee8-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="cbee8-110">[out] Wskaźnik do WCHAR \* do odbierania zakodowane w systemie szesnastkowym token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="cbee8-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbee8-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cbee8-111">Return Value</span></span>  
 <span data-ttu-id="cbee8-112">`S_OK`Jeśli funkcja zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cbee8-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="cbee8-113">W przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="cbee8-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbee8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbee8-114">See Also</span></span>  
 [<span data-ttu-id="cbee8-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="cbee8-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
