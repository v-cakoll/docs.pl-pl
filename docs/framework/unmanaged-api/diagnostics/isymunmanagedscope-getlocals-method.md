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
ms.openlocfilehash: bf932b63973f93c56883f099ddaadd9d1519f337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446327"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="620df-102">ISymUnmanagedScope::GetLocals — Metoda</span><span class="sxs-lookup"><span data-stu-id="620df-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="620df-103">Pobiera zmienne lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="620df-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="620df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="620df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="620df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="620df-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="620df-106">podczas `ULONG32`, który wskazuje rozmiar tablicy `locals`.</span><span class="sxs-lookup"><span data-stu-id="620df-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="620df-107">określoną Wskaźnik do `ULONG32`, który odbiera rozmiar buforu wymaganego do przechowywania zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="620df-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="620df-108">określoną Tablica, która odbiera zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="620df-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="620df-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="620df-109">Return Value</span></span>  
 <span data-ttu-id="620df-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="620df-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="620df-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="620df-111">Requirements</span></span>  
 <span data-ttu-id="620df-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="620df-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620df-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="620df-113">See also</span></span>

- [<span data-ttu-id="620df-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="620df-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
