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
ms.openlocfilehash: a2bba44af50607772f2a52203a47e21d8699f78b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716159"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="c5e11-102">ISymUnmanagedMethod::GetNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5e11-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="c5e11-103">Pobiera obszar nazw, w którym ta metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="c5e11-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5e11-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5e11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5e11-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c5e11-106">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagednamespace —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c5e11-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5e11-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c5e11-107">Return Value</span></span>  
 <span data-ttu-id="c5e11-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="c5e11-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5e11-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5e11-109">Requirements</span></span>  
 <span data-ttu-id="c5e11-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c5e11-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e11-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5e11-111">See also</span></span>
- [<span data-ttu-id="c5e11-112">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5e11-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
