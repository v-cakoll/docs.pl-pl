---
title: ISymUnmanagedVariable::GetStartOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f551e2f8a89cf2988ce43bf72a1e87e0ddaf713
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543214"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="1b5fe-102">ISymUnmanagedVariable::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b5fe-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="1b5fe-103">Pobiera Przesunięcie początku tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="1b5fe-104">Jeśli jest to zmienna lokalna w zakresie, Przesunięcie początku będą wchodzić w przesunięcia zdefiniowana dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b5fe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b5fe-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b5fe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b5fe-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1b5fe-107">[out] Wskaźnik do `ULONG32` odbierająca Przesunięcie początku.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b5fe-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1b5fe-108">Return Value</span></span>  
 <span data-ttu-id="1b5fe-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b5fe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b5fe-110">Requirements</span></span>  
 <span data-ttu-id="1b5fe-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1b5fe-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b5fe-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b5fe-112">See also</span></span>
- [<span data-ttu-id="1b5fe-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b5fe-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="1b5fe-114">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="1b5fe-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
