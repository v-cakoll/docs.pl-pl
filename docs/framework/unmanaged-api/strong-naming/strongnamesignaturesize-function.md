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
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176893"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="29c5c-102">StrongNameSignatureSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="29c5c-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="29c5c-103">Zwraca rozmiar podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="29c5c-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="29c5c-104">`StrongNameSignatureSize`jest zazwyczaj używany przez kompilatory, aby określić, ile miejsca do zarezerwowania w pliku podczas tworzenia zestawu podpisane z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="29c5c-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="29c5c-105">Ta funkcja została przestarzała.</span><span class="sxs-lookup"><span data-stu-id="29c5c-105">This function has been deprecated.</span></span> <span data-ttu-id="29c5c-106">Zamiast tego należy użyć metody [ICLRStrongName::StrongNameSignatureSize.](../hosting/iclrstrongname-strongnamesignaturesize-method.md)</span><span class="sxs-lookup"><span data-stu-id="29c5c-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c5c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="29c5c-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="29c5c-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="29c5c-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="29c5c-109">[w] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) który zawiera część publiczną pary kluczy używane do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="29c5c-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="29c5c-110">[w] Rozmiar w bajtach `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="29c5c-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="29c5c-111">[w] Liczba bajtów wymaganych do przechowywania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="29c5c-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29c5c-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29c5c-112">Return Value</span></span>  
 <span data-ttu-id="29c5c-113">`true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="29c5c-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29c5c-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29c5c-114">Remarks</span></span>  
 <span data-ttu-id="29c5c-115">Jeśli `StrongNameSignatureSize` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="29c5c-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c5c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29c5c-116">Requirements</span></span>  
 <span data-ttu-id="29c5c-117">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c5c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c5c-118">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="29c5c-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="29c5c-119">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29c5c-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29c5c-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c5c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c5c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29c5c-121">See also</span></span>

- [<span data-ttu-id="29c5c-122">StrongNameSignatureSize, metoda</span><span class="sxs-lookup"><span data-stu-id="29c5c-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="29c5c-123">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="29c5c-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
