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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97e6f16029b9a273a68d52b830939819bfa5380
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083560"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="8513c-102">ICLRStrongName::StrongNameKeyGenEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="8513c-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="8513c-103">Generuje nową parę kluczy publiczny/prywatny z określonego rozmiaru klucza do użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8513c-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8513c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8513c-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8513c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8513c-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8513c-106">[in] Nazwa żądany kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="8513c-106">[in] The requested key container name.</span></span> <span data-ttu-id="8513c-107">`wszKeyContainer` musi być niepustym ciągiem lub wartością null można wygenerować tymczasowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8513c-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8513c-108">[in] Wartość, która określa, czy należy pozostawić klawisz zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="8513c-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="8513c-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="8513c-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="8513c-110">0x00000000 — używany podczas `wszKeyContainer` ma wartość null, aby wygenerować nazwę kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="8513c-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="8513c-111">0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien być zarejestrowany po lewej.</span><span class="sxs-lookup"><span data-stu-id="8513c-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="8513c-112">[in] Żądany rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="8513c-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="8513c-113">[out] Zwrócone pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="8513c-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="8513c-114">[out] Rozmiar w bajtach z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8513c-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8513c-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8513c-115">Return Value</span></span>  
 <span data-ttu-id="8513c-116">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="8513c-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8513c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8513c-117">Remarks</span></span>  
 <span data-ttu-id="8513c-118">Wymaga platformy .NET Framework w wersji 1.0 i 1.1 `dwKeySize` o długości 1024 bitów, aby podpisać zestaw silną nazwą; w wersji 2.0 dodaje obsługiwanych w przypadku 2048-bitowe klucze.</span><span class="sxs-lookup"><span data-stu-id="8513c-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="8513c-119">Po pobraniu klucza, należy wywołać [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="8513c-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8513c-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8513c-120">Requirements</span></span>  
 <span data-ttu-id="8513c-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8513c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8513c-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8513c-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8513c-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8513c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8513c-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8513c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8513c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8513c-125">See also</span></span>

- [<span data-ttu-id="8513c-126">StrongNameKeyGen, metoda</span><span class="sxs-lookup"><span data-stu-id="8513c-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="8513c-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="8513c-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
