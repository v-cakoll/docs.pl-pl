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
ms.openlocfilehash: 3ce2372be02bc0bae7097389d4933f1f28a4ed79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="906bf-102">ISymUnmanagedScope::GetChildren — Metoda</span><span class="sxs-lookup"><span data-stu-id="906bf-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="906bf-103">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="906bf-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="906bf-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="906bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="906bf-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="906bf-106">[in] A `ULONG32` wskazuje, że rozmiar `children` tablicy.</span><span class="sxs-lookup"><span data-stu-id="906bf-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="906bf-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="906bf-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="906bf-108">[out] Tablica zwrócona elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="906bf-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="906bf-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="906bf-109">Return Value</span></span>  
 <span data-ttu-id="906bf-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="906bf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="906bf-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="906bf-111">Requirements</span></span>  
 <span data-ttu-id="906bf-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="906bf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906bf-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="906bf-113">See Also</span></span>  
 [<span data-ttu-id="906bf-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="906bf-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="906bf-115">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="906bf-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
