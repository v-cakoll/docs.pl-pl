---
title: "ISymUnmanagedScope::GetLocals — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetLocals
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 07d42423d284da39d40268727de13b4605221b5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="2d704-102">ISymUnmanagedScope::GetLocals — Metoda</span><span class="sxs-lookup"><span data-stu-id="2d704-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="2d704-103">Pobiera zmienne lokalne, zdefiniowanego w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="2d704-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d704-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d704-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d704-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d704-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="2d704-106">[in] A `ULONG32` wskazuje, że rozmiar `locals` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2d704-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="2d704-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2d704-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="2d704-108">[out] Tablica, która odbiera zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2d704-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d704-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2d704-109">Return Value</span></span>  
 <span data-ttu-id="2d704-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2d704-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d704-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d704-111">Requirements</span></span>  
 <span data-ttu-id="2d704-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2d704-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d704-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d704-113">See Also</span></span>  
 [<span data-ttu-id="2d704-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d704-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
