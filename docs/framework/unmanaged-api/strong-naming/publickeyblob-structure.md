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
ms.openlocfilehash: 245d9dc6147f4140e823b79c3816b9bc567ad712
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732690"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="32709-102">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="32709-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="32709-103">Reprezentuje w formacie binarnym, klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="32709-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32709-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32709-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="32709-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="32709-105">Members</span></span>  
  
|<span data-ttu-id="32709-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="32709-106">Member</span></span>|<span data-ttu-id="32709-107">Opis</span><span class="sxs-lookup"><span data-stu-id="32709-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="32709-108">Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="32709-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="32709-109">Identyfikator algorytmu wyznaczania wartości skrótu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="32709-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="32709-110">Długość klucza w bajtach.</span><span class="sxs-lookup"><span data-stu-id="32709-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="32709-111">Tablica bajtów o zmiennej długości, która zawiera wartość klucza w formacie zwracane przez interfejs CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="32709-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32709-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32709-112">Remarks</span></span>  
 <span data-ttu-id="32709-113">`PublicKeyBlob` Struktury jest używany przez [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)i innych funkcji silnej nazwy, aby przedstawić klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="32709-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32709-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32709-114">Requirements</span></span>  
 <span data-ttu-id="32709-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32709-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32709-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="32709-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="32709-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32709-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32709-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32709-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32709-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32709-119">See also</span></span>
- [<span data-ttu-id="32709-120">StrongNameGetPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="32709-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="32709-121">StrongNameSignatureGeneration, funkcja</span><span class="sxs-lookup"><span data-stu-id="32709-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
- [<span data-ttu-id="32709-122">Silne nazewnictwo — struktury</span><span class="sxs-lookup"><span data-stu-id="32709-122">Strong Naming Structures</span></span>](https://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
