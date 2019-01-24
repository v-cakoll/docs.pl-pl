---
title: ISymUnmanagedScope::GetEndOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 739398d8c20f58d8b5e458e2de4cbb6f56c50fd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624191"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="b51f9-102">ISymUnmanagedScope::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="b51f9-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="b51f9-103">Pobiera wartość przesunięcia końcowego dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="b51f9-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b51f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b51f9-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b51f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b51f9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b51f9-106">[out] Wskaźnik do `ULONG32` odbierająca przesunięcia końcowego.</span><span class="sxs-lookup"><span data-stu-id="b51f9-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b51f9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b51f9-107">Return Value</span></span>  
 <span data-ttu-id="b51f9-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="b51f9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b51f9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b51f9-109">Requirements</span></span>  
 <span data-ttu-id="b51f9-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b51f9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51f9-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b51f9-111">See also</span></span>
- [<span data-ttu-id="b51f9-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="b51f9-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="b51f9-113">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="b51f9-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
