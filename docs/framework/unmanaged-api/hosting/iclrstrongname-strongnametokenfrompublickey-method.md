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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e595904eacebdd42467fc4e0550db77578c075c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169731"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="1ed6c-102">ICLRStrongName::StrongNameTokenFromPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ed6c-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="1ed6c-103">Pobiera token, który reprezentuje klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="1ed6c-104">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed6c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ed6c-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ed6c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ed6c-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="1ed6c-107">[in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="1ed6c-108">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="1ed6c-109">[out] Przekazany token silną nazwę odpowiadającą kluczowi `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="1ed6c-110">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w których ma zostać zwrócony token.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="1ed6c-111">Obiekt wywołujący musi zwolnić ta pamięć przy użyciu [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="1ed6c-112">[out] Rozmiar w bajtach, token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ed6c-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1ed6c-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="1ed6c-114">Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="1ed6c-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ed6c-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ed6c-115">Remarks</span></span>  
 <span data-ttu-id="1ed6c-116">Token silna nazwa jest skrócona forma kluczem publicznym, używanego w taki sposób, aby zaoszczędzić miejsce, gdy kluczowe informacje są przechowywane w metadanych.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="1ed6c-117">W szczególności tokenów silnych nazw są używane w odwołania do zestawów do odwoływania się do zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ed6c-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ed6c-118">Requirements</span></span>  
 <span data-ttu-id="1ed6c-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ed6c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ed6c-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1ed6c-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1ed6c-121">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1ed6c-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="1ed6c-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1ed6c-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ed6c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ed6c-123">See also</span></span>

- [<span data-ttu-id="1ed6c-124">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="1ed6c-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="1ed6c-125">PublicKeyBlob — Struktura</span><span class="sxs-lookup"><span data-stu-id="1ed6c-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="1ed6c-126">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1ed6c-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
