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
ms.openlocfilehash: 38c4819a375cdd94ee31c2744871c600d8de0b40
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446005"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="2f3c1-102">ISymUnmanagedVariable::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f3c1-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="2f3c1-103">Pobiera przesunięcie początku tej zmiennej w elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="2f3c1-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="2f3c1-104">Jeśli jest to zmienna lokalna w zakresie, przesunięcie rozpoczęcia będzie należeć do przesunięć zdefiniowanych dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="2f3c1-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3c1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f3c1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f3c1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f3c1-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2f3c1-107">określoną Wskaźnik do `ULONG32`, który odbiera przesunięcie rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="2f3c1-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f3c1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2f3c1-108">Return Value</span></span>  
 <span data-ttu-id="2f3c1-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2f3c1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f3c1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f3c1-110">Requirements</span></span>  
 <span data-ttu-id="2f3c1-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2f3c1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f3c1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f3c1-112">See also</span></span>

- [<span data-ttu-id="2f3c1-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f3c1-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="2f3c1-114">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="2f3c1-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
