---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48d7b70b8ad014845a60fd66759c96419c46139b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698640"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="b1b06-102">ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1b06-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="b1b06-103">Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.</span><span class="sxs-lookup"><span data-stu-id="b1b06-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1b06-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1b06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1b06-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b1b06-106">[in] Ścieżka do pliku wykonalnego (PE) pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="b1b06-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="b1b06-107">[out] Token zwracany silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b1b06-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="b1b06-108">[out] Rozmiar w bajtach, token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b1b06-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="b1b06-109">[out] Zwrócony klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="b1b06-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="b1b06-110">[out] Rozmiar w bajtach klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b1b06-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1b06-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b1b06-111">Return Value</span></span>  
 <span data-ttu-id="b1b06-112">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="b1b06-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1b06-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1b06-113">Remarks</span></span>  
 <span data-ttu-id="b1b06-114">Token silna nazwa jest skrócona forma klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b1b06-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="b1b06-115">Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="b1b06-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="b1b06-116">Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="b1b06-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="b1b06-117">Po na pobranie klucza i jest tworzony token, należy wywołać [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="b1b06-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1b06-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1b06-118">Requirements</span></span>  
 <span data-ttu-id="b1b06-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1b06-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b06-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b1b06-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b1b06-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1b06-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1b06-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b06-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b06-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1b06-123">See also</span></span>
- [<span data-ttu-id="b1b06-124">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="b1b06-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="b1b06-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1b06-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
