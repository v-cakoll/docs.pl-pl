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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176958"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="36e75-102">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="36e75-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="36e75-103">Reprezentuje w formacie binarnym klucz publiczny pary klucza publicznego/prywatnego.</span><span class="sxs-lookup"><span data-stu-id="36e75-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36e75-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="36e75-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="36e75-105">Members</span></span>  
  
|<span data-ttu-id="36e75-106">Członek</span><span class="sxs-lookup"><span data-stu-id="36e75-106">Member</span></span>|<span data-ttu-id="36e75-107">Opis</span><span class="sxs-lookup"><span data-stu-id="36e75-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="36e75-108">Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w wincrypt.h) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="36e75-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="36e75-109">Identyfikator algorytmu mieszania (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="36e75-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="36e75-110">Długość klucza w bajtach.</span><span class="sxs-lookup"><span data-stu-id="36e75-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="36e75-111">Tablica bajtów o zmiennej długości, która zawiera wartość klucza w formacie zwracanym przez CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="36e75-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e75-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36e75-112">Remarks</span></span>  
 <span data-ttu-id="36e75-113">Struktura `PublicKeyBlob` jest używana przez [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)i inne silne funkcje nazwy do reprezentowania klucza publicznego pary klucza publicznego/prywatnego.</span><span class="sxs-lookup"><span data-stu-id="36e75-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36e75-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36e75-114">Requirements</span></span>  
 <span data-ttu-id="36e75-115">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36e75-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36e75-116">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="36e75-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="36e75-117">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36e75-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36e75-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36e75-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e75-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36e75-119">See also</span></span>

- [<span data-ttu-id="36e75-120">StrongNameGetPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="36e75-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="36e75-121">StrongNameSignatureGeneration, funkcja</span><span class="sxs-lookup"><span data-stu-id="36e75-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
