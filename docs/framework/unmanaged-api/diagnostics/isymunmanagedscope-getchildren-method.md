---
title: ISymUnmanagedScope::GetChildren — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffc4d5a1e6b8f1acc7603e9c2e01216e3188989e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751308"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="89069-102">ISymUnmanagedScope::GetChildren — Metoda</span><span class="sxs-lookup"><span data-stu-id="89069-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="89069-103">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="89069-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89069-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89069-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89069-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89069-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="89069-106">[in] A `ULONG32` oznacza rozmiar `children` tablicy.</span><span class="sxs-lookup"><span data-stu-id="89069-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="89069-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="89069-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="89069-108">[out] Zwracana tablica elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="89069-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89069-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="89069-109">Return Value</span></span>  
 <span data-ttu-id="89069-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="89069-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89069-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89069-111">Requirements</span></span>  
 <span data-ttu-id="89069-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="89069-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89069-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89069-113">See also</span></span>

- [<span data-ttu-id="89069-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="89069-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="89069-115">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="89069-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
