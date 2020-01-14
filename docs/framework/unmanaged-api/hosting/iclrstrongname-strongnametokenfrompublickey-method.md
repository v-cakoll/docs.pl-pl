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
ms.openlocfilehash: 13c1c505d939c1048eebef3d1d6b2abe493d319e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937421"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="933c5-102">ICLRStrongName::StrongNameTokenFromPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="933c5-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="933c5-103">Pobiera token reprezentujący klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="933c5-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="933c5-104">Token silnej nazwy to skrócona postać klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="933c5-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="933c5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="933c5-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="933c5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="933c5-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="933c5-107">podczas Struktura typu [PublicKeyBlob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) , która zawiera publiczną część pary kluczy używanej do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="933c5-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="933c5-108">podczas Rozmiar w bajtach `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="933c5-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="933c5-109">określoną Token silnej nazwy odpowiadający kluczowi przesłanemu `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="933c5-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="933c5-110">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w której ma zostać zwrócony token.</span><span class="sxs-lookup"><span data-stu-id="933c5-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="933c5-111">Obiekt wywołujący musi zwolnić tę pamięć przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="933c5-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="933c5-112">określoną Rozmiar (w bajtach) zwracanego tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="933c5-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="933c5-113">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="933c5-113">Return Value</span></span>  
 <span data-ttu-id="933c5-114">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="933c5-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="933c5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="933c5-115">Remarks</span></span>  
 <span data-ttu-id="933c5-116">Token silnej nazwy jest skróconą formą klucza publicznego, który służy do oszczędzania miejsca podczas zapisywania informacji o kluczu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="933c5-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="933c5-117">W odniesieniu do zestawu zależnego w odwołaniach do zestawów są używane tokeny silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="933c5-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="933c5-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="933c5-118">Requirements</span></span>  
 <span data-ttu-id="933c5-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="933c5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="933c5-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="933c5-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="933c5-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="933c5-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="933c5-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="933c5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933c5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="933c5-123">See also</span></span>

- [<span data-ttu-id="933c5-124">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="933c5-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="933c5-125">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="933c5-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="933c5-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="933c5-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
