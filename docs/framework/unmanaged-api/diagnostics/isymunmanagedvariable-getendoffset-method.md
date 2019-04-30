---
title: ISymUnmanagedVariable::GetEndOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 325db05cc322d85e836ca9ba62b6a169e8965241
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766366"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="4bde3-102">ISymUnmanagedVariable::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="4bde3-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="4bde3-103">Pobiera końcowy przesunięcie tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4bde3-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="4bde3-104">Jeśli jest to zmienna lokalna w zakresie, przesunięcia końcowego będą wchodzić w przesunięcia zdefiniowana dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="4bde3-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bde3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bde3-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bde3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bde3-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4bde3-107">[out] Wskaźnik do `ULONG32` odbierająca przesunięcia końcowego.</span><span class="sxs-lookup"><span data-stu-id="4bde3-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bde3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4bde3-108">Return Value</span></span>  
 <span data-ttu-id="4bde3-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="4bde3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bde3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bde3-110">Requirements</span></span>  
 <span data-ttu-id="4bde3-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4bde3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bde3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bde3-112">See also</span></span>

- [<span data-ttu-id="4bde3-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="4bde3-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="4bde3-114">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="4bde3-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
