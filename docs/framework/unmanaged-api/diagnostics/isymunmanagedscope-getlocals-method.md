---
title: ISymUnmanagedScope::GetLocals — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 781111db30ae664c9dd45744f88387e161f2716f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="73225-102">ISymUnmanagedScope::GetLocals — Metoda</span><span class="sxs-lookup"><span data-stu-id="73225-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="73225-103">Pobiera zmienne lokalne, zdefiniowanego w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="73225-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73225-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73225-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73225-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73225-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="73225-106">[in] A `ULONG32` wskazuje, że rozmiar `locals` tablicy.</span><span class="sxs-lookup"><span data-stu-id="73225-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="73225-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="73225-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="73225-108">[out] Tablica, która odbiera zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="73225-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73225-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73225-109">Return Value</span></span>  
 <span data-ttu-id="73225-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="73225-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73225-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73225-111">Requirements</span></span>  
 <span data-ttu-id="73225-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="73225-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73225-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73225-113">See Also</span></span>  
 [<span data-ttu-id="73225-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="73225-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
