---
title: ISymUnmanagedWriter3::OpenMethod2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178317"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="25ebf-102">ISymUnmanagedWriter3::OpenMethod2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="25ebf-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="25ebf-103">Otwiera metodę i zapewnia jej rzeczywiste przesunięcie przekroju na obrazie.</span><span class="sxs-lookup"><span data-stu-id="25ebf-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ebf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25ebf-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25ebf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25ebf-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="25ebf-106">[w] Token metadanych dla metody, która ma zostać otwarta.</span><span class="sxs-lookup"><span data-stu-id="25ebf-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="25ebf-107">[w] Przesunięcie sekcji na obrazie.</span><span class="sxs-lookup"><span data-stu-id="25ebf-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="25ebf-108">[w] Przesunięcie obrazu.</span><span class="sxs-lookup"><span data-stu-id="25ebf-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25ebf-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="25ebf-109">Return Value</span></span>  
 <span data-ttu-id="25ebf-110">S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="25ebf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ebf-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25ebf-111">Requirements</span></span>  
 <span data-ttu-id="25ebf-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25ebf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ebf-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25ebf-113">See also</span></span>

- [<span data-ttu-id="25ebf-114">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="25ebf-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="25ebf-115">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="25ebf-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
