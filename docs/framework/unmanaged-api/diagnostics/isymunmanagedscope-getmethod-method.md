---
title: ISymUnmanagedScope::GetMethod — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 954b1d91f33fe9a7e4df1ef51ee3666047836a17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986131"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="6d1d0-102">ISymUnmanagedScope::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d1d0-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="6d1d0-103">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="6d1d0-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d1d0-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d1d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d1d0-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6d1d0-106">[out] Wskaźnik do zwracanego [isymunmanagedmethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6d1d0-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d1d0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6d1d0-107">Return Value</span></span>  
 <span data-ttu-id="6d1d0-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="6d1d0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d1d0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d1d0-109">Requirements</span></span>  
 <span data-ttu-id="6d1d0-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6d1d0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1d0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d1d0-111">See also</span></span>

- [<span data-ttu-id="6d1d0-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d1d0-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
