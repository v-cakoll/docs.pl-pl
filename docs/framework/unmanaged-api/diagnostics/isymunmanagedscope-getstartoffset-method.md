---
title: ISymUnmanagedScope::GetStartOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b81ac93c67d59c294f22eb825527fa9982d9124
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721100"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="d3dca-102">ISymUnmanagedScope::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3dca-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="d3dca-103">Pobiera Przesunięcie początkowe dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="d3dca-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3dca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3dca-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3dca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3dca-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d3dca-106">[out] Wskaźnik do `ULONG32` zawierający Przesunięcie początkowe.</span><span class="sxs-lookup"><span data-stu-id="d3dca-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3dca-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3dca-107">Return Value</span></span>  
 <span data-ttu-id="d3dca-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="d3dca-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3dca-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3dca-109">Requirements</span></span>  
 <span data-ttu-id="d3dca-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d3dca-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3dca-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3dca-111">See also</span></span>
- [<span data-ttu-id="d3dca-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3dca-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="d3dca-113">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="d3dca-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
