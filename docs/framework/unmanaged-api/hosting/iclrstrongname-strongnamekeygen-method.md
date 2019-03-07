---
title: ICLRStrongName::StrongNameKeyGen — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98a53f488467ed1c66543c9861f056bc9890f617
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478521"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="81d26-102">ICLRStrongName::StrongNameKeyGen — Metoda</span><span class="sxs-lookup"><span data-stu-id="81d26-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="81d26-103">Tworzy nową parę kluczy publiczny/prywatny do użytku silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="81d26-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d26-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81d26-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81d26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81d26-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="81d26-106">[in] Nazwa żądany kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="81d26-106">[in] The requested key container name.</span></span> <span data-ttu-id="81d26-107">`wszKeyContainer` musi być niepustym ciągiem lub wartością null można wygenerować tymczasowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="81d26-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="81d26-108">[in] Wartość, która określa, czy należy pozostawić klawisz zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="81d26-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="81d26-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="81d26-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="81d26-110">0x00000000 — używany podczas `wszKeyContainer` ma wartość null, aby wygenerować nazwę kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="81d26-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="81d26-111">0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien być zarejestrowany po lewej.</span><span class="sxs-lookup"><span data-stu-id="81d26-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="81d26-112">[out] Zwrócone pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="81d26-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="81d26-113">[out] Rozmiar w bajtach z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="81d26-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81d26-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81d26-114">Return Value</span></span>  
 <span data-ttu-id="81d26-115">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="81d26-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81d26-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81d26-116">Remarks</span></span>  
 <span data-ttu-id="81d26-117">[Iclrstrongname::strongnamekeygen —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda tworzy klucz 1024-bitowy.</span><span class="sxs-lookup"><span data-stu-id="81d26-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="81d26-118">Po pobraniu klucza, należy wywołać [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="81d26-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d26-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81d26-119">Requirements</span></span>  
 <span data-ttu-id="81d26-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d26-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d26-121">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="81d26-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="81d26-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81d26-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81d26-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d26-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d26-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81d26-124">See also</span></span>
- [<span data-ttu-id="81d26-125">StrongNameKeyGenEx, metoda</span><span class="sxs-lookup"><span data-stu-id="81d26-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="81d26-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="81d26-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
