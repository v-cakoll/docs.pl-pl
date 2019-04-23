---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3dea6b9710f1ee5ccf8c51261f59b2de026f5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127780"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="96a0d-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="96a0d-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="96a0d-103">Zamknij źródłem tokenu można znaleźć w sekcji specjalne niestandardowe dane obejmują informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="96a0d-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="96a0d-104">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="96a0d-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a0d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="96a0d-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="96a0d-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="96a0d-106">Return Value</span></span>  
 <span data-ttu-id="96a0d-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="96a0d-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96a0d-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96a0d-108">Requirements</span></span>  
 <span data-ttu-id="96a0d-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="96a0d-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a0d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96a0d-110">See also</span></span>

- [<span data-ttu-id="96a0d-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="96a0d-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
