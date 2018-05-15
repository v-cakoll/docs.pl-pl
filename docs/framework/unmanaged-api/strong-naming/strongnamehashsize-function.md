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
ms.openlocfilehash: 92b9d9b5baee856f09dd24a62767aff604728997
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="35f40-102">StrongNameHashSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="35f40-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="35f40-103">Pobiera wymagane dla skrótu, przy użyciu algorytmu wyznaczania wartości skrótu określonej rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="35f40-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="35f40-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="35f40-104">This function has been deprecated.</span></span> <span data-ttu-id="35f40-105">Użyj [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="35f40-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35f40-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="35f40-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35f40-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="35f40-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="35f40-108">[in] Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="35f40-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="35f40-109">[out] Rozmiar buforu zwrócony w bajtach.</span><span class="sxs-lookup"><span data-stu-id="35f40-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35f40-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="35f40-110">Return Value</span></span>  
 <span data-ttu-id="35f40-111">`true` Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="35f40-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35f40-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35f40-112">Remarks</span></span>  
 <span data-ttu-id="35f40-113">Jeśli `StrongNameHashSize` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="35f40-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35f40-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35f40-114">Requirements</span></span>  
 <span data-ttu-id="35f40-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35f40-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35f40-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="35f40-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="35f40-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35f40-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35f40-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35f40-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f40-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35f40-119">See Also</span></span>  
 [<span data-ttu-id="35f40-120">StrongNameHashSize, metoda</span><span class="sxs-lookup"><span data-stu-id="35f40-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="35f40-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="35f40-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
