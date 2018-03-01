---
title: "ICLRStrongName::StrongNameTokenFromPublicKey — Metoda"
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
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5ee9153cec51f279e08b0ac0838456645cd7ada
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="3abd6-102">ICLRStrongName::StrongNameTokenFromPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="3abd6-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="3abd6-103">Pobiera token, który reprezentuje klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="3abd6-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="3abd6-104">Token silnej nazwy jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3abd6-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3abd6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3abd6-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3abd6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3abd6-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="3abd6-107">[in] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawiera część publiczną pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3abd6-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="3abd6-108">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3abd6-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="3abd6-109">[out] Przekazano token silną nazwą odpowiadającą kluczowi `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3abd6-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="3abd6-110">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, do której należy zwrócić token.</span><span class="sxs-lookup"><span data-stu-id="3abd6-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="3abd6-111">Obiekt wywołujący musi zwolnić tej pamięci za pomocą [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3abd6-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="3abd6-112">[out] Rozmiar w bajtach tokenu zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3abd6-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3abd6-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3abd6-113">Return Value</span></span>  
 <span data-ttu-id="3abd6-114">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="3abd6-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3abd6-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3abd6-115">Remarks</span></span>  
 <span data-ttu-id="3abd6-116">Token silnej nazwy jest skrócona forma klucz publiczny, który służy do zapisywania miejsce, gdy klucza informacje są przechowywane w metadanych.</span><span class="sxs-lookup"><span data-stu-id="3abd6-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="3abd6-117">W szczególności tokeny silnej nazwy są używane w odwołania do zestawów w odwołaniu do zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="3abd6-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3abd6-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3abd6-118">Requirements</span></span>  
 <span data-ttu-id="3abd6-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3abd6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3abd6-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3abd6-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3abd6-121">**Biblioteka:** uwzględnione jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3abd6-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="3abd6-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3abd6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3abd6-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3abd6-123">See Also</span></span>  
 [<span data-ttu-id="3abd6-124">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="3abd6-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="3abd6-125">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="3abd6-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="3abd6-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="3abd6-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
