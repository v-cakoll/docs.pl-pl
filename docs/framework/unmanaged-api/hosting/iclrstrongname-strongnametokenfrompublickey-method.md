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
ms.openlocfilehash: 17947526513bd1fbe3cb093e8ecaa7ed67983a7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759164"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="8f685-102">ICLRStrongName::StrongNameTokenFromPublicKey — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f685-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="8f685-103">Pobiera token, który reprezentuje klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="8f685-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="8f685-104">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="8f685-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f685-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f685-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f685-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f685-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="8f685-107">[in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8f685-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="8f685-108">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8f685-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="8f685-109">[out] Przekazany token silną nazwę odpowiadającą kluczowi `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8f685-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="8f685-110">Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w których ma zostać zwrócony token.</span><span class="sxs-lookup"><span data-stu-id="8f685-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="8f685-111">Obiekt wywołujący musi zwolnić ta pamięć przy użyciu [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8f685-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="8f685-112">[out] Rozmiar w bajtach, token zwrócony silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8f685-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f685-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8f685-113">Return Value</span></span>  
 <span data-ttu-id="8f685-114">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="8f685-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f685-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f685-115">Remarks</span></span>  
 <span data-ttu-id="8f685-116">Token silna nazwa jest skrócona forma kluczem publicznym, używanego w taki sposób, aby zaoszczędzić miejsce, gdy kluczowe informacje są przechowywane w metadanych.</span><span class="sxs-lookup"><span data-stu-id="8f685-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="8f685-117">W szczególności tokenów silnych nazw są używane w odwołania do zestawów do odwoływania się do zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="8f685-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f685-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f685-118">Requirements</span></span>  
 <span data-ttu-id="8f685-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f685-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f685-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8f685-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8f685-121">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8f685-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="8f685-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f685-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f685-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f685-123">See also</span></span>

- [<span data-ttu-id="8f685-124">StrongNameGetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="8f685-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="8f685-125">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="8f685-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="8f685-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f685-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
