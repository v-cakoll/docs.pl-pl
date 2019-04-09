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
ms.openlocfilehash: 625609d8632f1f73ee2ec01e3b2e0e1af7e4a134
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085717"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="7e151-102">ISymUnmanagedScope::GetLocals — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e151-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="7e151-103">Pobiera zmienne lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7e151-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e151-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e151-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e151-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e151-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="7e151-106">[in] A `ULONG32` oznacza rozmiar `locals` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e151-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="7e151-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7e151-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="7e151-108">[out] Tablica, która odbiera zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7e151-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e151-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7e151-109">Return Value</span></span>  
 <span data-ttu-id="7e151-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="7e151-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e151-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e151-111">Requirements</span></span>  
 <span data-ttu-id="7e151-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7e151-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e151-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e151-113">See also</span></span>

- [<span data-ttu-id="7e151-114">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e151-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
