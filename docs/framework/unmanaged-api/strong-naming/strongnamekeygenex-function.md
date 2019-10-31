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
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125216"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="dc41e-102">StrongNameKeyGenEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="dc41e-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="dc41e-103">Generuje nową parę kluczy publicznych/prywatnych z określonym rozmiarem klucza w celu użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="dc41e-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="dc41e-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="dc41e-104">This function has been deprecated.</span></span> <span data-ttu-id="dc41e-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameKeyGenEx —](../hosting/iclrstrongname-strongnamekeygenex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dc41e-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc41e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc41e-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc41e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc41e-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="dc41e-108">podczas Nazwa żądanego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="dc41e-108">[in] The requested key container name.</span></span> <span data-ttu-id="dc41e-109">`wszKeyContainer` nie może być pustym ciągiem ani mieć wartości null w celu wygenerowania nazwy tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="dc41e-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dc41e-110">podczas Określa, czy klucz ma pozostać zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="dc41e-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="dc41e-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="dc41e-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="dc41e-112">0x00000000 — używany, gdy `wszKeyContainer` ma wartość null w celu wygenerowania nazwy kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="dc41e-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="dc41e-113">0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien pozostać zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="dc41e-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="dc41e-114">podczas Żądany rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="dc41e-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="dc41e-115">określoną Zwracana para kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="dc41e-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="dc41e-116">określoną Rozmiar w bajtach `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="dc41e-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc41e-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dc41e-117">Return Value</span></span>  
 <span data-ttu-id="dc41e-118">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="dc41e-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc41e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc41e-119">Remarks</span></span>  
 <span data-ttu-id="dc41e-120">.NET Framework wersje 1,0 i 1,1 wymagają `dwKeySize` 1024 BITS do podpisania zestawu silną nazwą; w wersji 2,0 dodano obsługę kluczy 2048-bitowych.</span><span class="sxs-lookup"><span data-stu-id="dc41e-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="dc41e-121">Po pobraniu klucza należy wywołać funkcję [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) , aby zwolnić przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="dc41e-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="dc41e-122">Jeśli funkcja `StrongNameKeyGenEx` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="dc41e-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc41e-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc41e-123">Requirements</span></span>  
 <span data-ttu-id="dc41e-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc41e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc41e-125">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="dc41e-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dc41e-126">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc41e-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc41e-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc41e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc41e-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc41e-128">See also</span></span>

- [<span data-ttu-id="dc41e-129">StrongNameKeyGenEx, metoda</span><span class="sxs-lookup"><span data-stu-id="dc41e-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="dc41e-130">StrongNameKeyGen, metoda</span><span class="sxs-lookup"><span data-stu-id="dc41e-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="dc41e-131">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc41e-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
