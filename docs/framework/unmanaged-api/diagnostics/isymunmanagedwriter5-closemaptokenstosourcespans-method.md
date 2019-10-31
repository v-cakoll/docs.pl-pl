---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 43c35596d31842b85bbdc96a63413a176a59a172
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121651"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="27306-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="27306-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="27306-103">Zamknij sekcję specjalnych danych niestandardowych dla informacji dotyczących mapowania między tokenami i źródłami.</span><span class="sxs-lookup"><span data-stu-id="27306-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="27306-104">Po jego zamknięciu nie można dodać więcej informacji dotyczących mapowania.</span><span class="sxs-lookup"><span data-stu-id="27306-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27306-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="27306-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="27306-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="27306-106">Return Value</span></span>  
 <span data-ttu-id="27306-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="27306-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27306-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27306-108">Requirements</span></span>  
 <span data-ttu-id="27306-109">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="27306-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27306-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27306-110">See also</span></span>

- [<span data-ttu-id="27306-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="27306-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
