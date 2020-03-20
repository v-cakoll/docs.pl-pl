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
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175060"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="bc72d-102">StrongNameTokenFromPublicKey — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bc72d-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="bc72d-103">Pobiera token reprezentujący klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="bc72d-103">Gets a token representing a public key.</span></span> <span data-ttu-id="bc72d-104">Token silnej nazwy jest skróconą formą klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="bc72d-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="bc72d-105">Ta funkcja została przestarzała.</span><span class="sxs-lookup"><span data-stu-id="bc72d-105">This function has been deprecated.</span></span> <span data-ttu-id="bc72d-106">Zamiast tego należy użyć metody [ICLRStrongName::StrongNameTokenFromPublicKey.](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)</span><span class="sxs-lookup"><span data-stu-id="bc72d-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc72d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc72d-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc72d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc72d-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="bc72d-109">[w] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) który zawiera część publiczną pary kluczy używane do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="bc72d-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="bc72d-110">[w] Rozmiar w bajtach `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bc72d-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="bc72d-111">[na zewnątrz] Token silnej nazwy odpowiadający `pbPublicKeyBlob`kluczowi przekazanym w .</span><span class="sxs-lookup"><span data-stu-id="bc72d-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="bc72d-112">Środowisko wykonawcze języka wspólnego przydziela pamięć, w której do zwrócenia tokenu.</span><span class="sxs-lookup"><span data-stu-id="bc72d-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="bc72d-113">Wywołujący należy zwolnić tę pamięć przy użyciu [Funkcji StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="bc72d-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="bc72d-114">[na zewnątrz] Rozmiar w bajtach zwróconego tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="bc72d-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc72d-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bc72d-115">Return Value</span></span>  
 <span data-ttu-id="bc72d-116">`true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="bc72d-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc72d-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc72d-117">Remarks</span></span>  
 <span data-ttu-id="bc72d-118">Token silnej nazwy to skrócona forma klucza publicznego używana do zapisywania miejsca podczas przechowywania kluczowych informacji w metadanych.</span><span class="sxs-lookup"><span data-stu-id="bc72d-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="bc72d-119">W szczególności tokeny silnej nazwy są używane w odwołaniach do zestawu w celu odwoływania się do zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="bc72d-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="bc72d-120">Jeśli `StrongNameTokenFromPublicKey` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="bc72d-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc72d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc72d-121">Requirements</span></span>  
 <span data-ttu-id="bc72d-122">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc72d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc72d-123">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="bc72d-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bc72d-124">**Biblioteka:** Uwzględnione jako zasób w pliku mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bc72d-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="bc72d-125">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc72d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc72d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc72d-126">See also</span></span>

- [<span data-ttu-id="bc72d-127">StrongNameTokenFromPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="bc72d-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="bc72d-128">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="bc72d-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="bc72d-129">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="bc72d-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
