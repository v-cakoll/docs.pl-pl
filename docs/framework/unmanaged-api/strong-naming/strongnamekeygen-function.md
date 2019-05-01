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
ms.openlocfilehash: a8ebecce4078ba6c2b59e6bfba2d54300ba0c4ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000262"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="a7203-102">StrongNameKeyGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a7203-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="a7203-103">Tworzy nową parę kluczy publiczny/prywatny do użytku silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a7203-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="a7203-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a7203-104">This function has been deprecated.</span></span> <span data-ttu-id="a7203-105">Użyj [iclrstrongname::strongnamekeygen —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a7203-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7203-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7203-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7203-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7203-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a7203-108">[in] Nazwa żądany kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7203-108">[in] The requested key container name.</span></span> <span data-ttu-id="a7203-109">`wszKeyContainer` musi być ciągiem niepustym, lub wartość null, można wygenerować tymczasowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a7203-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a7203-110">[in] Określa, czy należy pozostawić klawisz zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="a7203-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="a7203-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="a7203-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="a7203-112">0x00000000 — używany podczas `wszKeyContainer` ma wartość null, aby wygenerować nazwę kontenera kluczy tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="a7203-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a7203-113">0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien być zarejestrowany po lewej.</span><span class="sxs-lookup"><span data-stu-id="a7203-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a7203-114">[out] Zwrócone pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="a7203-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a7203-115">[out] Rozmiar w bajtach z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a7203-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7203-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7203-116">Return Value</span></span>  
 <span data-ttu-id="a7203-117">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a7203-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7203-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7203-118">Remarks</span></span>  
 <span data-ttu-id="a7203-119">`StrongNameKeyGen` Funkcja tworzy klucz 1024-bitowy.</span><span class="sxs-lookup"><span data-stu-id="a7203-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="a7203-120">Po pobraniu klucza, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcję, aby zwolnić alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="a7203-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="a7203-121">Jeśli `StrongNameKeyGen` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="a7203-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7203-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7203-122">Requirements</span></span>  
 <span data-ttu-id="a7203-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7203-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7203-124">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a7203-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a7203-125">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7203-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7203-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7203-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7203-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7203-127">See also</span></span>

- [<span data-ttu-id="a7203-128">StrongNameKeyGen, metoda</span><span class="sxs-lookup"><span data-stu-id="a7203-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="a7203-129">StrongNameKeyGenEx, metoda</span><span class="sxs-lookup"><span data-stu-id="a7203-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a7203-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7203-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
