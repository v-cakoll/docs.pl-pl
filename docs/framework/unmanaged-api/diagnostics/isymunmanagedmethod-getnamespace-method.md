---
title: ISymUnmanagedMethod::GetNamespace — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 544fffd1b230469227d6ddbe3afcba54b6a7d5c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484592"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="900bb-102">ISymUnmanagedMethod::GetNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="900bb-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="900bb-103">Pobiera obszar nazw, w którym ta metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="900bb-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="900bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="900bb-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="900bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="900bb-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="900bb-106">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagednamespace —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="900bb-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="900bb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="900bb-107">Return Value</span></span>  
 <span data-ttu-id="900bb-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="900bb-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="900bb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="900bb-109">Requirements</span></span>  
 <span data-ttu-id="900bb-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="900bb-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="900bb-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="900bb-111">See also</span></span>
- [<span data-ttu-id="900bb-112">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="900bb-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
