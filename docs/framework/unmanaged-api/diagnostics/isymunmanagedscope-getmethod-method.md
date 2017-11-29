---
title: "ISymUnmanagedScope::GetMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb062ad7ab485a1631a9cbe15f904b21226cb502
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="a0f52-102">ISymUnmanagedScope::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0f52-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="a0f52-103">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="a0f52-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0f52-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0f52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0f52-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a0f52-106">[out] Wskaźnik do zwróconego [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0f52-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0f52-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0f52-107">Return Value</span></span>  
 <span data-ttu-id="a0f52-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a0f52-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0f52-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0f52-109">Requirements</span></span>  
 <span data-ttu-id="a0f52-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a0f52-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f52-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0f52-111">See Also</span></span>  
 [<span data-ttu-id="a0f52-112">ISymUnmanagedScope — interfejs</span><span class="sxs-lookup"><span data-stu-id="a0f52-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
