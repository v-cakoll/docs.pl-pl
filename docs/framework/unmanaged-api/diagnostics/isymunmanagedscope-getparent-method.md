---
title: ISymUnmanagedScope::GetParent — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 634f30186c552f0e5330dd94f78c585da7d450c9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493833"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="e806f-102">ISymUnmanagedScope::GetParent — Metoda</span><span class="sxs-lookup"><span data-stu-id="e806f-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="e806f-103">Pobiera zakres nadrzędny tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e806f-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e806f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e806f-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e806f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e806f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e806f-106">[out] Wskaźnik do zwracanego [isymunmanagedscope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e806f-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e806f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e806f-107">Return Value</span></span>  
 <span data-ttu-id="e806f-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="e806f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e806f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e806f-109">Requirements</span></span>  
 <span data-ttu-id="e806f-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e806f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e806f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e806f-111">See also</span></span>
- [<span data-ttu-id="e806f-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="e806f-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="e806f-113">GetChildren, metoda</span><span class="sxs-lookup"><span data-stu-id="e806f-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
