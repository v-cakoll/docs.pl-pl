---
title: StrongNameSignatureSize — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01c0f9ca0299e817618d93133c0eaca9fc63788e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767510"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="4d611-102">StrongNameSignatureSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4d611-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="4d611-103">Zwraca rozmiar podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4d611-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="4d611-104">`StrongNameSignatureSize` Aby określić, ile miejsca do zarezerwowania w pliku, podczas tworzenia zestawu podpisanego z opóźnieniem zwykle jest używana przez kompilatory.</span><span class="sxs-lookup"><span data-stu-id="4d611-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="4d611-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="4d611-105">This function has been deprecated.</span></span> <span data-ttu-id="4d611-106">Użyj [iclrstrongname::strongnamesignaturesize —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="4d611-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d611-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d611-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="4d611-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d611-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="4d611-109">[in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4d611-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="4d611-110">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="4d611-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="4d611-111">[in] Liczba bajtów potrzebnych do przechowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4d611-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d611-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d611-112">Return Value</span></span>  
 <span data-ttu-id="4d611-113">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="4d611-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d611-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d611-114">Remarks</span></span>  
 <span data-ttu-id="4d611-115">Jeśli `StrongNameSignatureSize` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="4d611-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d611-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d611-116">Requirements</span></span>  
 <span data-ttu-id="4d611-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d611-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d611-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4d611-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4d611-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d611-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d611-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d611-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d611-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d611-121">See also</span></span>

- [<span data-ttu-id="4d611-122">StrongNameSignatureSize, metoda</span><span class="sxs-lookup"><span data-stu-id="4d611-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="4d611-123">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d611-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
