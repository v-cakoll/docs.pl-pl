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
ms.openlocfilehash: 0898d554a2602a1139f2e37eb67f3aa00c5bd79e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436088"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="3cf2b-102">ISymUnmanagedMethod::GetScopeFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="3cf2b-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="3cf2b-103">Pobiera najbardziej otaczającym zakresie leksykalne w ramach tej metody, które umieszcza danego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="3cf2b-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="3cf2b-104">Może być używany w celu rozpoczęcia wyszukiwania zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="3cf2b-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf2b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3cf2b-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cf2b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf2b-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="3cf2b-107">[in] A `ULONG` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="3cf2b-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3cf2b-108">[out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3cf2b-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cf2b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3cf2b-109">Return Value</span></span>  
 <span data-ttu-id="3cf2b-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3cf2b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cf2b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3cf2b-111">Requirements</span></span>  
 <span data-ttu-id="3cf2b-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3cf2b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf2b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cf2b-113">See Also</span></span>  
 [<span data-ttu-id="3cf2b-114">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="3cf2b-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
