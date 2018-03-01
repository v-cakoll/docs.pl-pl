---
title: "StrongNameKeyGen — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3bb9530884f61345d439ec8662a088e1d152de7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="e5761-102">StrongNameKeyGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e5761-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="e5761-103">Tworzy nową parę kluczy publicznych/prywatnych do użytku silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e5761-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="e5761-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="e5761-104">This function has been deprecated.</span></span> <span data-ttu-id="e5761-105">Użyj [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e5761-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5761-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5761-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5761-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5761-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="e5761-108">[in] Nazwa żądanego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5761-108">[in] The requested key container name.</span></span> <span data-ttu-id="e5761-109">`wszKeyContainer`musi być niepustym ciągiem, lub wartość null, można wygenerować tymczasowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e5761-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e5761-110">[in] Określa, czy należy pozostawić klawisz zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="e5761-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="e5761-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="e5761-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e5761-112">0x00000000 — używany, gdy `wszKeyContainer` ma wartość null, można wygenerować nazwy kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="e5761-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="e5761-113">0x00000001 (`SN_LEAVE_KEY`) — określa, czy klucz powinien być zarejestrowany po lewej.</span><span class="sxs-lookup"><span data-stu-id="e5761-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="e5761-114">[out] Zwrócony pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="e5761-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="e5761-115">[out] Rozmiar w bajtach z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="e5761-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5761-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e5761-116">Return Value</span></span>  
 <span data-ttu-id="e5761-117">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e5761-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5761-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5761-118">Remarks</span></span>  
 <span data-ttu-id="e5761-119">`StrongNameKeyGen` Funkcja tworzy 1024-bitowego klucza.</span><span class="sxs-lookup"><span data-stu-id="e5761-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="e5761-120">Po pobraniu klucza, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="e5761-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="e5761-121">Jeśli `StrongNameKeyGen` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="e5761-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5761-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5761-122">Requirements</span></span>  
 <span data-ttu-id="e5761-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5761-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5761-124">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e5761-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e5761-125">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5761-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5761-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5761-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5761-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5761-127">See Also</span></span>  
 [<span data-ttu-id="e5761-128">StrongNameKeyGen, metoda</span><span class="sxs-lookup"><span data-stu-id="e5761-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="e5761-129">StrongNameKeyGenEx, metoda</span><span class="sxs-lookup"><span data-stu-id="e5761-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="e5761-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5761-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
