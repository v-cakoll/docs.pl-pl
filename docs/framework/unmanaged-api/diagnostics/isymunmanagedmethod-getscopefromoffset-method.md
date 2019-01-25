---
title: ISymUnmanagedMethod::GetScopeFromOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5422e781ab2f494e85f637219aa540bf4ac34cb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629738"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="59644-102">ISymUnmanagedMethod::GetScopeFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="59644-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="59644-103">Pobiera najbardziej otaczającym zakresie leksykalnym w ramach tej metody, która otacza danego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="59644-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="59644-104">Może to służyć do rozpoczęcia wyszukiwania zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="59644-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59644-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="59644-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59644-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="59644-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="59644-107">[in] Element `ULONG` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="59644-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="59644-108">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagedscope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="59644-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59644-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="59644-109">Return Value</span></span>  
 <span data-ttu-id="59644-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="59644-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59644-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59644-111">Requirements</span></span>  
 <span data-ttu-id="59644-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="59644-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59644-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59644-113">See also</span></span>
- [<span data-ttu-id="59644-114">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="59644-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
