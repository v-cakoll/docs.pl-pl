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
ms.openlocfilehash: c7e807b502e0905f9ae785203289447c71d25e04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072148"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="5d00b-102">StrongNameHashSize — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5d00b-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="5d00b-103">Pobiera rozmiar bufora wymaganych do wyznaczania wartości skrótu, za pomocą określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="5d00b-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="5d00b-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="5d00b-104">This function has been deprecated.</span></span> <span data-ttu-id="5d00b-105">Użyj [iclrstrongname::strongnamehashsize —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5d00b-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d00b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d00b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d00b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d00b-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="5d00b-108">[in] Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="5d00b-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="5d00b-109">[out] Rozmiar buforu zwrócony w bajtach.</span><span class="sxs-lookup"><span data-stu-id="5d00b-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d00b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5d00b-110">Return Value</span></span>  
 `true` <span data-ttu-id="5d00b-111">Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="5d00b-111">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d00b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d00b-112">Remarks</span></span>  
 <span data-ttu-id="5d00b-113">Jeśli `StrongNameHashSize` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="5d00b-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d00b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d00b-114">Requirements</span></span>  
 <span data-ttu-id="5d00b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d00b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d00b-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="5d00b-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5d00b-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d00b-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5d00b-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5d00b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d00b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d00b-119">See also</span></span>

- [<span data-ttu-id="5d00b-120">StrongNameHashSize, metoda</span><span class="sxs-lookup"><span data-stu-id="5d00b-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="5d00b-121">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5d00b-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
