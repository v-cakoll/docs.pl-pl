---
title: StrongNameKeyGenEx — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8623c69390600380d80b0292d6a75fa395f9ae7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479136"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="84ec5-102">StrongNameKeyGenEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="84ec5-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="84ec5-103">Generuje nową parę kluczy publiczny/prywatny z określonego rozmiaru klucza do użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="84ec5-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="84ec5-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="84ec5-104">This function has been deprecated.</span></span> <span data-ttu-id="84ec5-105">Użyj [iclrstrongname::strongnamekeygenex —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="84ec5-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84ec5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="84ec5-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84ec5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="84ec5-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="84ec5-108">[in] Nazwa żądany kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="84ec5-108">[in] The requested key container name.</span></span> <span data-ttu-id="84ec5-109">`wszKeyContainer` musi być ciągiem niepustym, lub wartość null, można wygenerować tymczasowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="84ec5-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="84ec5-110">[in] Określa, czy należy pozostawić klawisz zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="84ec5-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="84ec5-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="84ec5-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="84ec5-112">0x00000000 — używany podczas `wszKeyContainer` ma wartość null, aby wygenerować nazwę kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="84ec5-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="84ec5-113">0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien być zarejestrowany po lewej.</span><span class="sxs-lookup"><span data-stu-id="84ec5-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="84ec5-114">[in] Żądany rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="84ec5-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="84ec5-115">[out] Zwrócone pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="84ec5-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="84ec5-116">[out] Rozmiar w bajtach z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="84ec5-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84ec5-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="84ec5-117">Return Value</span></span>  
 <span data-ttu-id="84ec5-118">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="84ec5-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84ec5-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84ec5-119">Remarks</span></span>  
 <span data-ttu-id="84ec5-120">Wymaga platformy .NET Framework w wersji 1.0 i 1.1 `dwKeySize` o długości 1024 bitów, aby podpisać zestaw silną nazwą; w wersji 2.0 dodaje obsługiwanych w przypadku 2048-bitowe klucze.</span><span class="sxs-lookup"><span data-stu-id="84ec5-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="84ec5-121">Po pobraniu klucza, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcję, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="84ec5-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="84ec5-122">Jeśli `StrongNameKeyGenEx` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="84ec5-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84ec5-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84ec5-123">Requirements</span></span>  
 <span data-ttu-id="84ec5-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84ec5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84ec5-125">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="84ec5-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="84ec5-126">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84ec5-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84ec5-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84ec5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ec5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84ec5-128">See also</span></span>
- [<span data-ttu-id="84ec5-129">StrongNameKeyGenEx, metoda</span><span class="sxs-lookup"><span data-stu-id="84ec5-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="84ec5-130">StrongNameKeyGen, metoda</span><span class="sxs-lookup"><span data-stu-id="84ec5-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="84ec5-131">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="84ec5-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
