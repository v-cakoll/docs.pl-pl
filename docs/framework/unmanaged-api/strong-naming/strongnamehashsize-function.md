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
ms.openlocfilehash: 7ad1f015f04b3829090417c26e8d58892ee15af4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487437"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="2ef9c-102">StrongNameHashSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2ef9c-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="2ef9c-103">Pobiera rozmiar bufora wymaganych do wyznaczania wartości skrótu, za pomocą określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="2ef9c-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="2ef9c-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="2ef9c-104">This function has been deprecated.</span></span> <span data-ttu-id="2ef9c-105">Użyj [iclrstrongname::strongnamehashsize —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2ef9c-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ef9c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ef9c-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ef9c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ef9c-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="2ef9c-108">[in] Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="2ef9c-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="2ef9c-109">[out] Rozmiar buforu zwrócony w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2ef9c-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ef9c-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ef9c-110">Return Value</span></span>  
 <span data-ttu-id="2ef9c-111">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="2ef9c-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ef9c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ef9c-112">Remarks</span></span>  
 <span data-ttu-id="2ef9c-113">Jeśli `StrongNameHashSize` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="2ef9c-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ef9c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ef9c-114">Requirements</span></span>  
 <span data-ttu-id="2ef9c-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ef9c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ef9c-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2ef9c-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2ef9c-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ef9c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ef9c-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ef9c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef9c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ef9c-119">See also</span></span>
- [<span data-ttu-id="2ef9c-120">StrongNameHashSize, metoda</span><span class="sxs-lookup"><span data-stu-id="2ef9c-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="2ef9c-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ef9c-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
