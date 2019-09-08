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
ms.openlocfilehash: 38f98b971e430a2c35a4c484f4f9c4bf387c640c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798956"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="600c7-102">StrongNameSignatureSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="600c7-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="600c7-103">Zwraca rozmiar sygnatury silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="600c7-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="600c7-104">`StrongNameSignatureSize`jest zwykle używany przez kompilatory do określenia ilości miejsca do zarezerwowania w pliku podczas tworzenia zestawu z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="600c7-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="600c7-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="600c7-105">This function has been deprecated.</span></span> <span data-ttu-id="600c7-106">Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureSize —](../hosting/iclrstrongname-strongnamesignaturesize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="600c7-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600c7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="600c7-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="600c7-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="600c7-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="600c7-109">podczas Struktura typu [PublicKeyBlob —](publickeyblob-structure.md) , która zawiera publiczną część pary kluczy używanej do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="600c7-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="600c7-110">podczas Rozmiar, w bajtach, z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="600c7-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="600c7-111">podczas Liczba bajtów wymagana do zapisania sygnatury silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="600c7-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="600c7-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="600c7-112">Return Value</span></span>  
 <span data-ttu-id="600c7-113">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="600c7-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="600c7-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="600c7-114">Remarks</span></span>  
 <span data-ttu-id="600c7-115">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameSignatureSize`</span><span class="sxs-lookup"><span data-stu-id="600c7-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="600c7-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="600c7-116">Requirements</span></span>  
 <span data-ttu-id="600c7-117">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="600c7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="600c7-118">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="600c7-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="600c7-119">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="600c7-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="600c7-120">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="600c7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600c7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="600c7-121">See also</span></span>

- [<span data-ttu-id="600c7-122">StrongNameSignatureSize, metoda</span><span class="sxs-lookup"><span data-stu-id="600c7-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="600c7-123">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="600c7-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
