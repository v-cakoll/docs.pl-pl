---
title: Funkcja _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
ms.openlocfilehash: 33b8f47813a3bf43bd69741c9febb150fa3a92e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099904"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="2e21d-102">\_funkcja AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="2e21d-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="2e21d-103">Oblicza token klucza publicznego o silnej nazwie w formacie PublicKeyBlob — dostawcy usług kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="2e21d-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e21d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e21d-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e21d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e21d-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="2e21d-106">podczas Obiekt BLOB klucza publicznego dostawcy usług kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="2e21d-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="2e21d-107">określoną Wskaźnik do WCHAR \*, aby otrzymać skrót klucza publicznego zakodowany szesnastkowo.</span><span class="sxs-lookup"><span data-stu-id="2e21d-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e21d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2e21d-108">Return Value</span></span>  
 <span data-ttu-id="2e21d-109">`S_OK`, jeśli funkcja się powiedzie; w przeciwnym razie `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="2e21d-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e21d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e21d-110">See also</span></span>

- [<span data-ttu-id="2e21d-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2e21d-111">Authenticode</span></span>](index.md)
