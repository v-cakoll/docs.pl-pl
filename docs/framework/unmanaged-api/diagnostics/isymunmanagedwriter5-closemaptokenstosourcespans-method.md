---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 653dd933066898c1954cfbcc57c0c0493e47b4be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428615"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="8cb2b-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="8cb2b-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="8cb2b-103">Zamknij sekcji specjalne dane niestandardowe dla tokenu do źródła obejmuje informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="8cb2b-104">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb2b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cb2b-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8cb2b-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8cb2b-106">Return Value</span></span>  
 <span data-ttu-id="8cb2b-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cb2b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cb2b-108">Requirements</span></span>  
 <span data-ttu-id="8cb2b-109">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8cb2b-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb2b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cb2b-110">See Also</span></span>  
 [<span data-ttu-id="8cb2b-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="8cb2b-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
