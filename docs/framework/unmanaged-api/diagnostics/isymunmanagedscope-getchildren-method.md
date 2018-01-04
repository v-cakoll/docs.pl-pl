---
title: "ISymUnmanagedScope::GetChildren — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetChildren
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2259eccc3be68f562a0c5b00ffe7fd47bad9a238
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="18430-102">ISymUnmanagedScope::GetChildren — Metoda</span><span class="sxs-lookup"><span data-stu-id="18430-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="18430-103">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="18430-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18430-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18430-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18430-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18430-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="18430-106">[in] A `ULONG32` wskazuje, że rozmiar `children` tablicy.</span><span class="sxs-lookup"><span data-stu-id="18430-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="18430-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="18430-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="18430-108">[out] Tablica zwrócona elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="18430-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18430-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="18430-109">Return Value</span></span>  
 <span data-ttu-id="18430-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="18430-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18430-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18430-111">Requirements</span></span>  
 <span data-ttu-id="18430-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18430-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18430-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18430-113">See Also</span></span>  
 [<span data-ttu-id="18430-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="18430-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="18430-115">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="18430-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
