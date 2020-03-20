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
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176321"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="1f4ad-102">ICLRStrongName::StrongNameTokenFromPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f4ad-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="1f4ad-103">Pobiera token, który reprezentuje klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="1f4ad-104">Token silnej nazwy jest skróconą formą klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f4ad-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f4ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f4ad-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="1f4ad-107">[w] Struktura typu [PublicKeyBlob,](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) który zawiera część publiczną pary kluczy używane do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="1f4ad-108">[w] Rozmiar w bajtach `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="1f4ad-109">[na zewnątrz] Token silnej nazwy odpowiadający `pbPublicKeyBlob`kluczowi przekazanym w .</span><span class="sxs-lookup"><span data-stu-id="1f4ad-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="1f4ad-110">Środowisko wykonawcze języka wspólnego przydziela pamięć, w której do zwrócenia tokenu.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="1f4ad-111">Wywołujący należy zwolnić tę pamięć przy użyciu [metody ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="1f4ad-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="1f4ad-112">[na zewnątrz] Rozmiar w bajtach zwróconego tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f4ad-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f4ad-113">Return Value</span></span>  
 <span data-ttu-id="1f4ad-114">`S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="1f4ad-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f4ad-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f4ad-115">Remarks</span></span>  
 <span data-ttu-id="1f4ad-116">Token silnej nazwy to skrócona forma klucza publicznego, który jest używany do zapisywania miejsca podczas przechowywania kluczowych informacji w metadanych.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="1f4ad-117">W szczególności tokeny silnej nazwy są używane w odwołaniach do zestawu w celu odwoływania się do zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="1f4ad-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f4ad-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f4ad-118">Requirements</span></span>  
 <span data-ttu-id="1f4ad-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f4ad-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f4ad-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1f4ad-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1f4ad-121">**Biblioteka:** Uwzględnione jako zasób w pliku mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1f4ad-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="1f4ad-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f4ad-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4ad-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f4ad-123">See also</span></span>

- [<span data-ttu-id="1f4ad-124">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="1f4ad-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="1f4ad-125">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="1f4ad-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="1f4ad-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f4ad-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
