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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4d720480e4c8b21b3aa56ce81634a26ac9c75de
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776672"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="6bd13-102">\_AxlPublicKeyBlobToPublicKeyToken, funkcja</span><span class="sxs-lookup"><span data-stu-id="6bd13-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="6bd13-103">Oblicza token klucza publicznego o silnej nazwie w formacie PublicKeyBlob — dostawcy usług kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="6bd13-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bd13-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bd13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bd13-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="6bd13-106">podczas Obiekt BLOB klucza publicznego dostawcy usług kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="6bd13-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="6bd13-107">określoną Wskaźnik do WCHAR \*, aby otrzymać skrót klucza publicznego zakodowany szesnastkowo.</span><span class="sxs-lookup"><span data-stu-id="6bd13-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bd13-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6bd13-108">Return Value</span></span>  
 <span data-ttu-id="6bd13-109">`S_OK`Jeśli funkcja się powiedzie; w `S_FALSE`przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="6bd13-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd13-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bd13-110">See also</span></span>

- [<span data-ttu-id="6bd13-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6bd13-111">Authenticode</span></span>](index.md)
