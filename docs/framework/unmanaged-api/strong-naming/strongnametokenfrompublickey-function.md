---
title: StrongNameTokenFromPublicKey — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbfd3ae32f4d3033894fdaf6b1bcc880c324e928
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000288"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="5b60c-102">StrongNameTokenFromPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5b60c-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="5b60c-103">Pobiera token reprezentujący klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="5b60c-103">Gets a token representing a public key.</span></span> <span data-ttu-id="5b60c-104">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="5b60c-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="5b60c-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="5b60c-105">This function has been deprecated.</span></span> <span data-ttu-id="5b60c-106">Użyj [iclrstrongname::strongnametokenfrompublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5b60c-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b60c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b60c-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b60c-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b60c-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="5b60c-109">[in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5b60c-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="5b60c-110">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5b60c-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="5b60c-111">[out] Przekazany token silną nazwę odpowiadającą kluczowi `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5b60c-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="5b60c-112">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w których ma zostać zwrócony token.</span><span class="sxs-lookup"><span data-stu-id="5b60c-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="5b60c-113">Obiekt wywołujący musi zwolnić ta pamięć przy użyciu [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="5b60c-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="5b60c-114">[out] Rozmiar w bajtach, token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5b60c-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b60c-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5b60c-115">Return Value</span></span>  
 <span data-ttu-id="5b60c-116">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="5b60c-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b60c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b60c-117">Remarks</span></span>  
 <span data-ttu-id="5b60c-118">Token silna nazwa jest skrócona forma kluczem publicznym, która pozwala zaoszczędzić miejsce, gdy kluczowe informacje są przechowywane w metadanych.</span><span class="sxs-lookup"><span data-stu-id="5b60c-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="5b60c-119">W szczególności tokenów silnych nazw są używane w odwołania do zestawów do odwoływania się do zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="5b60c-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="5b60c-120">Jeśli `StrongNameTokenFromPublicKey` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="5b60c-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b60c-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b60c-121">Requirements</span></span>  
 <span data-ttu-id="5b60c-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b60c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b60c-123">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="5b60c-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5b60c-124">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5b60c-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="5b60c-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b60c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b60c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b60c-126">See also</span></span>

- [<span data-ttu-id="5b60c-127">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="5b60c-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="5b60c-128">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="5b60c-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="5b60c-129">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="5b60c-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
