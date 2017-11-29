---
title: "StrongNameTokenFromPublicKey — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: COM
f1_keywords: StrongNameTokenFromPublicKey
helpviewer_keywords: StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfde09f6383646f24077c3bdc0efa4b31bc50ba0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="24b4d-102">StrongNameTokenFromPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="24b4d-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="24b4d-103">Pobiera token reprezentujący klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="24b4d-103">Gets a token representing a public key.</span></span> <span data-ttu-id="24b4d-104">Token silnej nazwy jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="24b4d-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="24b4d-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="24b4d-105">This function has been deprecated.</span></span> <span data-ttu-id="24b4d-106">Użyj [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="24b4d-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b4d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="24b4d-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24b4d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="24b4d-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="24b4d-109">[in] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawiera część publiczną pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="24b4d-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="24b4d-110">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="24b4d-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="24b4d-111">[out] Przekazano token silną nazwą odpowiadającą kluczowi `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="24b4d-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="24b4d-112">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, do której należy zwrócić token.</span><span class="sxs-lookup"><span data-stu-id="24b4d-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="24b4d-113">Obiekt wywołujący musi zwolnić tej pamięci za pomocą [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="24b4d-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="24b4d-114">[out] Rozmiar w bajtach tokenu zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="24b4d-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24b4d-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24b4d-115">Return Value</span></span>  
 <span data-ttu-id="24b4d-116">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="24b4d-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24b4d-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24b4d-117">Remarks</span></span>  
 <span data-ttu-id="24b4d-118">Token silnej nazwy jest skrócona forma klucz publiczny pozwala zaoszczędzić miejsce, gdy są przechowywane informacje o kluczu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="24b4d-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="24b4d-119">W szczególności tokeny silnej nazwy są używane w odwołania do zestawów w odwołaniu do zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="24b4d-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="24b4d-120">Jeśli `StrongNameTokenFromPublicKey` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="24b4d-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b4d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24b4d-121">Requirements</span></span>  
 <span data-ttu-id="24b4d-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24b4d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b4d-123">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="24b4d-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="24b4d-124">**Biblioteka:** uwzględnione jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="24b4d-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="24b4d-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b4d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b4d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24b4d-126">See Also</span></span>  
 [<span data-ttu-id="24b4d-127">StrongNameTokenFromPublicKey — metoda</span><span class="sxs-lookup"><span data-stu-id="24b4d-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="24b4d-128">StrongNameGetPublicKey — metoda</span><span class="sxs-lookup"><span data-stu-id="24b4d-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="24b4d-129">Publickeyblob — struktura</span><span class="sxs-lookup"><span data-stu-id="24b4d-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
