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
ms.openlocfilehash: 9d1ee82f24e1908af1998e424006415af3134456
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446275"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="a0f9a-102">ISymUnmanagedScope::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0f9a-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="a0f9a-103">Gets the start offset for this scope.</span><span class="sxs-lookup"><span data-stu-id="a0f9a-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0f9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0f9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0f9a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a0f9a-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span><span class="sxs-lookup"><span data-stu-id="a0f9a-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0f9a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0f9a-107">Return Value</span></span>  
 <span data-ttu-id="a0f9a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="a0f9a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0f9a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0f9a-109">Requirements</span></span>  
 <span data-ttu-id="a0f9a-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a0f9a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f9a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0f9a-111">See also</span></span>

- [<span data-ttu-id="a0f9a-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0f9a-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="a0f9a-113">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="a0f9a-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
