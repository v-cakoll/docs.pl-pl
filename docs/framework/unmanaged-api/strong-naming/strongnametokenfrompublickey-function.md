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
ms.openlocfilehash: 197504cbb0dd66c0cf43dee718026fc63e918d60
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798851"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="6edd0-102">StrongNameTokenFromPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6edd0-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="6edd0-103">Pobiera token reprezentujący klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="6edd0-103">Gets a token representing a public key.</span></span> <span data-ttu-id="6edd0-104">Token silnej nazwy to skrócona postać klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="6edd0-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="6edd0-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="6edd0-105">This function has been deprecated.</span></span> <span data-ttu-id="6edd0-106">Zamiast tego użyj metody [ICLRStrongName:: StrongNameTokenFromPublicKey —](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6edd0-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edd0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6edd0-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6edd0-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="6edd0-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="6edd0-109">podczas Struktura typu [PublicKeyBlob —](publickeyblob-structure.md) , która zawiera publiczną część pary kluczy używanej do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6edd0-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="6edd0-110">podczas Rozmiar, w bajtach, z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="6edd0-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="6edd0-111">określoną Token silnej nazwy odpowiadający kluczowi przekazaniu `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="6edd0-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="6edd0-112">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w której ma zostać zwrócony token.</span><span class="sxs-lookup"><span data-stu-id="6edd0-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="6edd0-113">Obiekt wywołujący musi zwolnić tę pamięć przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6edd0-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="6edd0-114">określoną Rozmiar (w bajtach) zwracanego tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6edd0-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6edd0-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6edd0-115">Return Value</span></span>  
 <span data-ttu-id="6edd0-116">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="6edd0-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6edd0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6edd0-117">Remarks</span></span>  
 <span data-ttu-id="6edd0-118">Token silnej nazwy to Skrócona forma klucza publicznego służąca do oszczędzania miejsca podczas przechowywania informacji o kluczu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="6edd0-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="6edd0-119">W odniesieniu do zestawu zależnego w odwołaniach do zestawów są używane tokeny silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6edd0-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="6edd0-120">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameTokenFromPublicKey`</span><span class="sxs-lookup"><span data-stu-id="6edd0-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edd0-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6edd0-121">Requirements</span></span>  
 <span data-ttu-id="6edd0-122">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6edd0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6edd0-123">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6edd0-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6edd0-124">**Biblioteki** Uwzględnione jako zasób w bibliotece mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6edd0-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="6edd0-125">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6edd0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edd0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6edd0-126">See also</span></span>

- [<span data-ttu-id="6edd0-127">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="6edd0-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="6edd0-128">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="6edd0-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="6edd0-129">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="6edd0-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
