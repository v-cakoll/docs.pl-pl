---
title: ISymUnmanagedScope::GetLocalCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eae5b0bc6ba9f891527282a0a8c209dd3698c4df
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488452"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="baea2-102">ISymUnmanagedScope::GetLocalCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="baea2-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="baea2-103">Pobiera liczbę zmiennych lokalnych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="baea2-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baea2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="baea2-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baea2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="baea2-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="baea2-106">[out] Wskaźnik do `ULONG32` odbierająca liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="baea2-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baea2-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="baea2-107">Return Value</span></span>  
 <span data-ttu-id="baea2-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="baea2-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baea2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="baea2-109">Requirements</span></span>  
 <span data-ttu-id="baea2-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="baea2-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baea2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baea2-111">See also</span></span>
- [<span data-ttu-id="baea2-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="baea2-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
