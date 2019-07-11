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
ms.openlocfilehash: 2ef32a963b73f2109b9747ef303e8ccd6a729838
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778260"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="ebbaf-102">ISymUnmanagedVariable::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebbaf-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="ebbaf-103">Pobiera końcowy przesunięcie tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ebbaf-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="ebbaf-104">Jeśli jest to zmienna lokalna w zakresie, przesunięcia końcowego będą wchodzić w przesunięcia zdefiniowana dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="ebbaf-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebbaf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebbaf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebbaf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebbaf-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ebbaf-107">[out] Wskaźnik do `ULONG32` odbierająca przesunięcia końcowego.</span><span class="sxs-lookup"><span data-stu-id="ebbaf-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebbaf-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ebbaf-108">Return Value</span></span>  
 <span data-ttu-id="ebbaf-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="ebbaf-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebbaf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebbaf-110">Requirements</span></span>  
 <span data-ttu-id="ebbaf-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ebbaf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbaf-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebbaf-112">See also</span></span>

- [<span data-ttu-id="ebbaf-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebbaf-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="ebbaf-114">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="ebbaf-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
