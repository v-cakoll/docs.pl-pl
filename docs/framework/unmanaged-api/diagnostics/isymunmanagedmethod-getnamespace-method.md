---
title: "ISymUnmanagedMethod::GetNamespace — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2244229b50a9944cefb5804720198bf391fd0e6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="47b89-102">ISymUnmanagedMethod::GetNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="47b89-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="47b89-103">Pobiera obszar nazw, w którym ta metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="47b89-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47b89-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47b89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47b89-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="47b89-106">[out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="47b89-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47b89-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="47b89-107">Return Value</span></span>  
 <span data-ttu-id="47b89-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="47b89-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b89-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47b89-109">Requirements</span></span>  
 <span data-ttu-id="47b89-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47b89-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b89-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47b89-111">See Also</span></span>  
 [<span data-ttu-id="47b89-112">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="47b89-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
