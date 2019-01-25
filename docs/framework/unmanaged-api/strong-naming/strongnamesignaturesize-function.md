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
ms.openlocfilehash: b5e4e2a817abff7b0cf24223b7f245fc6f86c1d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544994"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="df97f-102">StrongNameSignatureSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="df97f-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="df97f-103">Zwraca rozmiar podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="df97f-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="df97f-104">`StrongNameSignatureSize` Aby określić, ile miejsca do zarezerwowania w pliku, podczas tworzenia zestawu podpisanego z opóźnieniem zwykle jest używana przez kompilatory.</span><span class="sxs-lookup"><span data-stu-id="df97f-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="df97f-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="df97f-105">This function has been deprecated.</span></span> <span data-ttu-id="df97f-106">Użyj [iclrstrongname::strongnamesignaturesize —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="df97f-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df97f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="df97f-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="df97f-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="df97f-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="df97f-109">[in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="df97f-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="df97f-110">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="df97f-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="df97f-111">[in] Liczba bajtów potrzebnych do przechowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="df97f-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df97f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="df97f-112">Return Value</span></span>  
 <span data-ttu-id="df97f-113">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="df97f-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df97f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df97f-114">Remarks</span></span>  
 <span data-ttu-id="df97f-115">Jeśli `StrongNameSignatureSize` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="df97f-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df97f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df97f-116">Requirements</span></span>  
 <span data-ttu-id="df97f-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df97f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df97f-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="df97f-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="df97f-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df97f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df97f-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df97f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df97f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df97f-121">See also</span></span>
- [<span data-ttu-id="df97f-122">StrongNameSignatureSize, metoda</span><span class="sxs-lookup"><span data-stu-id="df97f-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="df97f-123">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="df97f-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
