---
title: "ISymUnmanagedScope::GetMethod — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4756ff1f373f09a96daa64c1fb01875274a6d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="2c10a-102">ISymUnmanagedScope::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c10a-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="2c10a-103">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="2c10a-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c10a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c10a-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c10a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c10a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2c10a-106">[out] Wskaźnik do zwróconego [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2c10a-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c10a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2c10a-107">Return Value</span></span>  
 <span data-ttu-id="2c10a-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2c10a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c10a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c10a-109">Requirements</span></span>  
 <span data-ttu-id="2c10a-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2c10a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c10a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c10a-111">See Also</span></span>  
 [<span data-ttu-id="2c10a-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="2c10a-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
