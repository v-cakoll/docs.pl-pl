---
title: ICLRStrongName::StrongNameTokenFromPublicKey — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: e61a652072b424d1245518c832f9b0856e0f2021
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762607"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="73003-102">ICLRStrongName::StrongNameTokenFromPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="73003-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="73003-103">Pobiera token reprezentujący klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="73003-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="73003-104">Token silnej nazwy to skrócona postać klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="73003-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73003-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="73003-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73003-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="73003-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="73003-107">podczas Struktura typu [PublicKeyBlob —](../strong-naming/publickeyblob-structure.md) , która zawiera publiczną część pary kluczy używanej do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="73003-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="73003-108">podczas Rozmiar, w bajtach, z `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="73003-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="73003-109">określoną Token silnej nazwy odpowiadający kluczowi przekazaniu `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="73003-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="73003-110">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w której ma zostać zwrócony token.</span><span class="sxs-lookup"><span data-stu-id="73003-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="73003-111">Obiekt wywołujący musi zwolnić tę pamięć przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="73003-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="73003-112">określoną Rozmiar (w bajtach) zwracanego tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="73003-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73003-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73003-113">Return Value</span></span>  
 <span data-ttu-id="73003-114">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="73003-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73003-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73003-115">Remarks</span></span>  
 <span data-ttu-id="73003-116">Token silnej nazwy jest skróconą formą klucza publicznego, który służy do oszczędzania miejsca podczas zapisywania informacji o kluczu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="73003-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="73003-117">W odniesieniu do zestawu zależnego w odwołaniach do zestawów są używane tokeny silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="73003-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73003-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73003-118">Requirements</span></span>  
 <span data-ttu-id="73003-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73003-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73003-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="73003-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="73003-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="73003-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="73003-122">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73003-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73003-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73003-123">See also</span></span>

- [<span data-ttu-id="73003-124">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="73003-124">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="73003-125">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="73003-125">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="73003-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="73003-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
