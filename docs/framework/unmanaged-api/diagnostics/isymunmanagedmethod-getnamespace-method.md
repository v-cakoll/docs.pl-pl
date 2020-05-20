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
ms.openlocfilehash: cda30f3c73bf75c37ff79fc415e02382b053807e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614490"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="71383-102">ISymUnmanagedMethod::GetNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="71383-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="71383-103">Pobiera przestrzeń nazw, w której jest zdefiniowana ta metoda.</span><span class="sxs-lookup"><span data-stu-id="71383-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71383-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71383-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71383-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71383-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="71383-106">określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="71383-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71383-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="71383-107">Return Value</span></span>  
 <span data-ttu-id="71383-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="71383-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71383-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71383-109">Requirements</span></span>  
 <span data-ttu-id="71383-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="71383-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71383-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71383-111">See also</span></span>

- [<span data-ttu-id="71383-112">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71383-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
