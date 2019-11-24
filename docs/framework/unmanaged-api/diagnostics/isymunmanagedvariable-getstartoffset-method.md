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
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="01628-102">ISymUnmanagedVariable::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="01628-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="01628-103">Gets the start offset of this variable within its parent.</span><span class="sxs-lookup"><span data-stu-id="01628-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="01628-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span><span class="sxs-lookup"><span data-stu-id="01628-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01628-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="01628-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01628-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="01628-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="01628-107">[out] A pointer to a `ULONG32` that receives the start offset.</span><span class="sxs-lookup"><span data-stu-id="01628-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01628-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="01628-108">Return Value</span></span>  
 <span data-ttu-id="01628-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="01628-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01628-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01628-110">Requirements</span></span>  
 <span data-ttu-id="01628-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="01628-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01628-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01628-112">See also</span></span>

- [<span data-ttu-id="01628-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="01628-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="01628-114">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="01628-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
