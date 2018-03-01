---
title: Funkcja _AxlPublicKeyBlobToPublicKeyToken
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
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c9dfd42d0908032ed9a652f6f4f5736ba775ce8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="61708-102">Funkcja _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="61708-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="61708-103">Oblicza silnej nazwy token klucza publicznego z formatu PUBLICKEYBLOB dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="61708-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61708-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61708-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61708-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61708-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="61708-106">[in] Publiczny blob klucza dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="61708-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="61708-107">[out] Wskaźnik do WCHAR \* do odbierania zakodowane w systemie szesnastkowym wartość skrótu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="61708-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61708-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61708-108">Return Value</span></span>  
 <span data-ttu-id="61708-109">`S_OK`Jeśli funkcja zakończy się pomyślnie; w przeciwnym razie `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="61708-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61708-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61708-110">See Also</span></span>  
 [<span data-ttu-id="61708-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="61708-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
