---
title: PublicKeyBlob — Struktura
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a5e18c0cf65ee8f336b74a2d8e44fcf5af0cfef
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261781"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="22093-102">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="22093-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="22093-103">Reprezentuje w formacie binarnym, klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="22093-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22093-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22093-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="22093-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="22093-105">Members</span></span>  
  
|<span data-ttu-id="22093-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="22093-106">Member</span></span>|<span data-ttu-id="22093-107">Opis</span><span class="sxs-lookup"><span data-stu-id="22093-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="22093-108">Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="22093-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="22093-109">Identyfikator algorytmu wyznaczania wartości skrótu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="22093-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="22093-110">Długość klucza w bajtach.</span><span class="sxs-lookup"><span data-stu-id="22093-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="22093-111">Tablica bajtów o zmiennej długości, która zawiera wartość klucza w formacie zwracane przez interfejs CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="22093-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22093-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22093-112">Remarks</span></span>  
 <span data-ttu-id="22093-113">`PublicKeyBlob` Struktury jest używany przez [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)i innych funkcji silnej nazwy, aby przedstawić klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="22093-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22093-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22093-114">Requirements</span></span>  
 <span data-ttu-id="22093-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22093-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22093-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="22093-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="22093-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22093-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22093-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22093-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22093-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22093-119">See also</span></span>
- [<span data-ttu-id="22093-120">StrongNameGetPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="22093-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="22093-121">StrongNameSignatureGeneration, funkcja</span><span class="sxs-lookup"><span data-stu-id="22093-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
