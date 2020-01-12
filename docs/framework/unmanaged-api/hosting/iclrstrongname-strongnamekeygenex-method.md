---
title: ICLRStrongName::StrongNameKeyGenEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: b09677a45c5d515aacb2cac709599140039a9dd8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899555"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="bea09-102">ICLRStrongName::StrongNameKeyGenEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="bea09-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="bea09-103">Generuje nową parę kluczy publicznych/prywatnych z określonym rozmiarem klucza w celu użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="bea09-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bea09-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bea09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bea09-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="bea09-106">podczas Nazwa żądanego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="bea09-106">[in] The requested key container name.</span></span> <span data-ttu-id="bea09-107">`wszKeyContainer` musi być niepustym ciągiem lub wartością null w celu wygenerowania nazwy tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="bea09-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bea09-108">podczas Wartość określająca, czy klucz ma pozostać zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="bea09-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="bea09-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="bea09-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="bea09-110">0x00000000 — używany, gdy `wszKeyContainer` ma wartość null w celu wygenerowania nazwy kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="bea09-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="bea09-111">0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien pozostać zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="bea09-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="bea09-112">podczas Żądany rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="bea09-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="bea09-113">określoną Zwracana para kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="bea09-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="bea09-114">określoną Rozmiar w bajtach `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bea09-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bea09-115">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="bea09-115">Return Value</span></span>  
 <span data-ttu-id="bea09-116">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="bea09-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bea09-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bea09-117">Remarks</span></span>  
 <span data-ttu-id="bea09-118">.NET Framework wersje 1,0 i 1,1 wymagają `dwKeySize` 1024 BITS do podpisania zestawu silną nazwą; w wersji 2,0 dodano obsługę kluczy 2048-bitowych.</span><span class="sxs-lookup"><span data-stu-id="bea09-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="bea09-119">Po pobraniu klucza należy wywołać metodę [ICLRStrongName:: StrongNameFreeBuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) , aby zwolnić przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="bea09-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bea09-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bea09-120">Requirements</span></span>  
 <span data-ttu-id="bea09-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bea09-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bea09-122">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="bea09-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bea09-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bea09-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bea09-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bea09-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea09-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bea09-125">See also</span></span>

- [<span data-ttu-id="bea09-126">StrongNameKeyGen, metoda</span><span class="sxs-lookup"><span data-stu-id="bea09-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="bea09-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="bea09-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
