---
title: StrongNameKeyGen — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f062f47790136e8cd39c6751b7c75eef660c2b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799137"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="c2973-102">StrongNameKeyGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c2973-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="c2973-103">Tworzy nową parę kluczy publiczny/prywatny w celu użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c2973-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="c2973-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="c2973-104">This function has been deprecated.</span></span> <span data-ttu-id="c2973-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameKeyGen —](../hosting/iclrstrongname-strongnamekeygen-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c2973-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2973-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2973-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2973-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2973-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="c2973-108">podczas Nazwa żądanego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="c2973-108">[in] The requested key container name.</span></span> <span data-ttu-id="c2973-109">`wszKeyContainer`nie może być pustym ciągiem ani mieć wartości null w celu wygenerowania nazwy tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="c2973-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c2973-110">podczas Określa, czy klucz ma pozostać zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="c2973-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="c2973-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="c2973-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="c2973-112">0x00000000 — używany, `wszKeyContainer` gdy ma wartość null, aby wygenerować nazwę kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="c2973-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="c2973-113">0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien pozostać zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="c2973-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="c2973-114">określoną Zwracana para kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="c2973-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="c2973-115">określoną Rozmiar, w bajtach, z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="c2973-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2973-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c2973-116">Return Value</span></span>  
 <span data-ttu-id="c2973-117">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="c2973-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2973-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2973-118">Remarks</span></span>  
 <span data-ttu-id="c2973-119">`StrongNameKeyGen` Funkcja tworzy klucz 1024-bitowy.</span><span class="sxs-lookup"><span data-stu-id="c2973-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="c2973-120">Po pobraniu klucza należy wywołać funkcję [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) , aby zwolnić przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="c2973-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="c2973-121">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameKeyGen`</span><span class="sxs-lookup"><span data-stu-id="c2973-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2973-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2973-122">Requirements</span></span>  
 <span data-ttu-id="c2973-123">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2973-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2973-124">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c2973-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c2973-125">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c2973-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2973-126">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2973-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2973-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2973-127">See also</span></span>

- [<span data-ttu-id="c2973-128">StrongNameKeyGen, metoda</span><span class="sxs-lookup"><span data-stu-id="c2973-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="c2973-129">StrongNameKeyGenEx, metoda</span><span class="sxs-lookup"><span data-stu-id="c2973-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="c2973-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2973-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
