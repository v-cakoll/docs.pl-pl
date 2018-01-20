---
title: "PublicKeyBlob — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PublicKeyBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: PublicKeyBlob
helpviewer_keywords: PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1f04c692b7549c4d7d8d431591eeb867b673d9a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="f7987-102">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="f7987-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="f7987-103">Reprezentuje w formacie binarnym, klucz publiczny pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="f7987-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7987-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7987-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="f7987-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f7987-105">Members</span></span>  
  
|<span data-ttu-id="f7987-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f7987-106">Member</span></span>|<span data-ttu-id="f7987-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f7987-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="f7987-108">Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="f7987-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="f7987-109">Identyfikator algorytmu wyznaczania wartości skrótu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="f7987-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="f7987-110">Długość klucza w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f7987-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="f7987-111">Tablica bajtów o zmiennej długości, która zawiera wartości klucza w formacie zwracane przez interfejs CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="f7987-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7987-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7987-112">Remarks</span></span>  
 <span data-ttu-id="f7987-113">`PublicKeyBlob` Struktura jest używana przez [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)i inne funkcje silnej nazwy do reprezentowania klucz publiczny pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="f7987-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7987-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7987-114">Requirements</span></span>  
 <span data-ttu-id="f7987-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7987-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7987-116">**Header:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f7987-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f7987-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7987-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7987-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7987-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7987-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7987-119">See Also</span></span>  
 [<span data-ttu-id="f7987-120">StrongNameGetPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="f7987-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="f7987-121">StrongNameSignatureGeneration, funkcja</span><span class="sxs-lookup"><span data-stu-id="f7987-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="f7987-122">Silne nazewnictwo struktury</span><span class="sxs-lookup"><span data-stu-id="f7987-122">Strong Naming Structures</span></span>](http://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
