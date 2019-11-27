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
ms.openlocfilehash: 348a8cebe0fd746f3ae490484ffcca2fcb77684b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446312"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="dd30b-102">ISymUnmanagedScope::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd30b-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="dd30b-103">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="dd30b-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd30b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd30b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd30b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd30b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="dd30b-106">określoną Wskaźnik do zwracanego interfejsu [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dd30b-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd30b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd30b-107">Return Value</span></span>  
 <span data-ttu-id="dd30b-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="dd30b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd30b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd30b-109">Requirements</span></span>  
 <span data-ttu-id="dd30b-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dd30b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd30b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd30b-111">See also</span></span>

- [<span data-ttu-id="dd30b-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd30b-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
