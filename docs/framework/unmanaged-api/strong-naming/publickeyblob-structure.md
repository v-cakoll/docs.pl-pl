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
ms.openlocfilehash: e66196e2bd2cb326ca3f5badc67bcf8d81e5fc3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799163"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="87ff1-102">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="87ff1-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="87ff1-103">Reprezentuje w formacie binarnym klucz publiczny pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="87ff1-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ff1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87ff1-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="87ff1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="87ff1-105">Members</span></span>  
  
|<span data-ttu-id="87ff1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="87ff1-106">Member</span></span>|<span data-ttu-id="87ff1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="87ff1-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="87ff1-108">Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w WinCrypt. h) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="87ff1-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="87ff1-109">Identyfikator algorytmu wyznaczania wartości skrótu (typu `ALG_ID`, zgodnie z definicją w WinCrypt. h) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="87ff1-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="87ff1-110">Długość klucza w bajtach.</span><span class="sxs-lookup"><span data-stu-id="87ff1-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="87ff1-111">Tablica bajtów o zmiennej długości, która zawiera wartość klucza w formacie zwracanym przez interfejs CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="87ff1-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87ff1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87ff1-112">Remarks</span></span>  
 <span data-ttu-id="87ff1-113">Struktura jest używana przez [StrongNameGetPublicKey —](strongnamegetpublickey-function.md), StrongNameSignatureGeneration — i inne funkcje silnej nazwy do reprezentowania klucza publicznego pary kluczy publicznych/prywatnych. [](strongnamesignaturegeneration-function.md) `PublicKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="87ff1-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ff1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87ff1-114">Requirements</span></span>  
 <span data-ttu-id="87ff1-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ff1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ff1-116">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="87ff1-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="87ff1-117">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87ff1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87ff1-118">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ff1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ff1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87ff1-119">See also</span></span>

- [<span data-ttu-id="87ff1-120">StrongNameGetPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="87ff1-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="87ff1-121">StrongNameSignatureGeneration, funkcja</span><span class="sxs-lookup"><span data-stu-id="87ff1-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
