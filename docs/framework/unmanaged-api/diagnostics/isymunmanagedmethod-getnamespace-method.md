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
ms.openlocfilehash: b8bbedb4c60a2df6070373f2b6a104fff094869a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448969"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="deee3-102">ISymUnmanagedMethod::GetNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="deee3-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="deee3-103">Pobiera przestrzeń nazw, w której jest zdefiniowana ta metoda.</span><span class="sxs-lookup"><span data-stu-id="deee3-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deee3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="deee3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deee3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="deee3-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="deee3-106">określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="deee3-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="deee3-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="deee3-107">Return Value</span></span>  
 <span data-ttu-id="deee3-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="deee3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deee3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="deee3-109">Requirements</span></span>  
 <span data-ttu-id="deee3-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="deee3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deee3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="deee3-111">See also</span></span>

- [<span data-ttu-id="deee3-112">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="deee3-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
