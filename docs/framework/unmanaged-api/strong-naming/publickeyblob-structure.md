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
ms.openlocfilehash: fd7a4b19613ea771a055af7dd91ec368859ee191
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529137"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="39ef6-102">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="39ef6-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="39ef6-103">Reprezentuje w formacie binarnym, klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="39ef6-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ef6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39ef6-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="39ef6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="39ef6-105">Members</span></span>  
  
|<span data-ttu-id="39ef6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="39ef6-106">Member</span></span>|<span data-ttu-id="39ef6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="39ef6-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="39ef6-108">Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="39ef6-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="39ef6-109">Identyfikator algorytmu wyznaczania wartości skrótu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="39ef6-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="39ef6-110">Długość klucza w bajtach.</span><span class="sxs-lookup"><span data-stu-id="39ef6-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="39ef6-111">Tablica bajtów o zmiennej długości, która zawiera wartość klucza w formacie zwracane przez interfejs CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="39ef6-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39ef6-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39ef6-112">Remarks</span></span>  
 <span data-ttu-id="39ef6-113">`PublicKeyBlob` Struktury jest używany przez [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)i innych funkcji silnej nazwy, aby przedstawić klucz publiczny z pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="39ef6-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39ef6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39ef6-114">Requirements</span></span>  
 <span data-ttu-id="39ef6-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39ef6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39ef6-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="39ef6-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="39ef6-117">**Biblioteka:** dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39ef6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39ef6-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39ef6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ef6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39ef6-119">See Also</span></span>  
 [<span data-ttu-id="39ef6-120">StrongNameGetPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="39ef6-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="39ef6-121">StrongNameSignatureGeneration, funkcja</span><span class="sxs-lookup"><span data-stu-id="39ef6-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="39ef6-122">Silne nazewnictwo — struktury</span><span class="sxs-lookup"><span data-stu-id="39ef6-122">Strong Naming Structures</span></span>](https://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
