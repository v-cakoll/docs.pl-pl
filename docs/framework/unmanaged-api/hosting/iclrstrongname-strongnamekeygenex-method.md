---
title: "ICLRStrongName::StrongNameKeyGenEx — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGenEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a303dd65cd366936d060f96899d5e218eeec9d7e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="8d29f-102">ICLRStrongName::StrongNameKeyGenEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d29f-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="8d29f-103">Generuje nową parę kluczy publicznych i prywatnych z określonym rozmiarem klucza do użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8d29f-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d29f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d29f-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d29f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d29f-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8d29f-106">[in] Nazwa żądanego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="8d29f-106">[in] The requested key container name.</span></span> <span data-ttu-id="8d29f-107">`wszKeyContainer`musi być niepustym ciągiem lub wartość null, można wygenerować tymczasowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8d29f-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8d29f-108">[in] Wartość, która określa, czy należy pozostawić klawisz zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="8d29f-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="8d29f-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="8d29f-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="8d29f-110">0x00000000 — używany, gdy `wszKeyContainer` ma wartość null, można wygenerować nazwy kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="8d29f-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="8d29f-111">0x00000001 (`SN_LEAVE_KEY`) — określa, czy klucz powinien być zarejestrowany po lewej.</span><span class="sxs-lookup"><span data-stu-id="8d29f-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="8d29f-112">[in] Żądany rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="8d29f-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="8d29f-113">[out] Zwrócony pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="8d29f-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="8d29f-114">[out] Rozmiar w bajtach z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8d29f-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d29f-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8d29f-115">Return Value</span></span>  
 <span data-ttu-id="8d29f-116">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="8d29f-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d29f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d29f-117">Remarks</span></span>  
 <span data-ttu-id="8d29f-118">Wersje programu .NET Framework 1.0 i 1.1 wymagają `dwKeySize` 1024 bitów, aby podpisać zestaw o silnej nazwie; w wersji 2.0 dodaje obsługuje kluczy 2048-bitowego.</span><span class="sxs-lookup"><span data-stu-id="8d29f-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="8d29f-119">Po pobraniu klucza, należy wywołać [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="8d29f-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d29f-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d29f-120">Requirements</span></span>  
 <span data-ttu-id="8d29f-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d29f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d29f-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8d29f-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8d29f-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d29f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d29f-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d29f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d29f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d29f-125">See Also</span></span>  
 [<span data-ttu-id="8d29f-126">StrongNameKeyGen — metoda</span><span class="sxs-lookup"><span data-stu-id="8d29f-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="8d29f-127">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="8d29f-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
