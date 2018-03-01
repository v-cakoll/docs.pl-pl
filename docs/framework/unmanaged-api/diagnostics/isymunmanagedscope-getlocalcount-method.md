---
title: "ISymUnmanagedScope::GetLocalCount — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9db774140ef55b2dfcb54ff701c2b842418a4923
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="7888c-102">ISymUnmanagedScope::GetLocalCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="7888c-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="7888c-103">Pobiera liczbę zmiennych lokalnych, zdefiniowanego w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7888c-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7888c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7888c-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7888c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7888c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7888c-106">[out] Wskaźnik do `ULONG32` odbierająca liczba zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7888c-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7888c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7888c-107">Return Value</span></span>  
 <span data-ttu-id="7888c-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7888c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7888c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7888c-109">Requirements</span></span>  
 <span data-ttu-id="7888c-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7888c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7888c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7888c-111">See Also</span></span>  
 [<span data-ttu-id="7888c-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="7888c-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
