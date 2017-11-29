---
title: "StrongNameKeyGenEx — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGenEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGenEx
helpviewer_keywords: StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87841c230c71650f822a6cb2f6cc3f3c17c2ef35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="a4646-102">StrongNameKeyGenEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a4646-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="a4646-103">Generuje nową parę kluczy publicznych i prywatnych z określonym rozmiarem klucza do użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a4646-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="a4646-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a4646-104">This function has been deprecated.</span></span> <span data-ttu-id="a4646-105">Użyj [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a4646-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4646-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4646-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4646-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4646-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a4646-108">[in] Nazwa żądanego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="a4646-108">[in] The requested key container name.</span></span> <span data-ttu-id="a4646-109">`wszKeyContainer`musi być niepustym ciągiem, lub wartość null, można wygenerować tymczasowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a4646-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a4646-110">[in] Określa, czy należy pozostawić klawisz zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="a4646-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="a4646-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="a4646-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="a4646-112">0x00000000 — używany, gdy `wszKeyContainer` ma wartość null, można wygenerować nazwy kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="a4646-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="a4646-113">0x00000001 (`SN_LEAVE_KEY`) — określa, czy klucz powinien być zarejestrowany po lewej.</span><span class="sxs-lookup"><span data-stu-id="a4646-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="a4646-114">[in] Żądany rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a4646-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a4646-115">[out] Zwrócony pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="a4646-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a4646-116">[out] Rozmiar w bajtach z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a4646-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4646-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a4646-117">Return Value</span></span>  
 <span data-ttu-id="a4646-118">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a4646-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4646-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4646-119">Remarks</span></span>  
 <span data-ttu-id="a4646-120">Wersje programu .NET Framework 1.0 i 1.1 wymagają `dwKeySize` 1024 bitów, aby podpisać zestaw o silnej nazwie; w wersji 2.0 dodaje obsługuje kluczy 2048-bitowego.</span><span class="sxs-lookup"><span data-stu-id="a4646-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="a4646-121">Po pobraniu klucza, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="a4646-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="a4646-122">Jeśli `StrongNameKeyGenEx` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="a4646-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4646-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4646-123">Requirements</span></span>  
 <span data-ttu-id="a4646-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4646-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4646-125">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a4646-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a4646-126">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4646-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4646-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4646-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4646-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4646-128">See Also</span></span>  
 [<span data-ttu-id="a4646-129">StrongNameKeyGenEx — metoda</span><span class="sxs-lookup"><span data-stu-id="a4646-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="a4646-130">StrongNameKeyGen — metoda</span><span class="sxs-lookup"><span data-stu-id="a4646-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="a4646-131">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="a4646-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
