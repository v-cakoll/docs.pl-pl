---
title: StrongNameHashSize — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53384a5aa7f8d11f868057f892f7b60aac2e9f02
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799041"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="d17ff-102">StrongNameHashSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d17ff-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="d17ff-103">Pobiera rozmiar buforu wymagany dla skrótu przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d17ff-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="d17ff-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="d17ff-104">This function has been deprecated.</span></span> <span data-ttu-id="d17ff-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameHashSize —](../hosting/iclrstrongname-strongnamehashsize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d17ff-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d17ff-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d17ff-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d17ff-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d17ff-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="d17ff-108">podczas Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="d17ff-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="d17ff-109">określoną Zwrócony rozmiar buforu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="d17ff-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d17ff-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d17ff-110">Return Value</span></span>  
 <span data-ttu-id="d17ff-111">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="d17ff-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d17ff-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d17ff-112">Remarks</span></span>  
 <span data-ttu-id="d17ff-113">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameHashSize`</span><span class="sxs-lookup"><span data-stu-id="d17ff-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d17ff-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d17ff-114">Requirements</span></span>  
 <span data-ttu-id="d17ff-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d17ff-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d17ff-116">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d17ff-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d17ff-117">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d17ff-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d17ff-118">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d17ff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d17ff-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d17ff-119">See also</span></span>

- [<span data-ttu-id="d17ff-120">StrongNameHashSize, metoda</span><span class="sxs-lookup"><span data-stu-id="d17ff-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="d17ff-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d17ff-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
