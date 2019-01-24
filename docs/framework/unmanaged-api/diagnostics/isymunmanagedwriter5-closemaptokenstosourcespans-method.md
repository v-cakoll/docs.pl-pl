---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce4b41854d5d9324169b1873f431ef81c0a4c5be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677922"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="81567-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="81567-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="81567-103">Zamknij źródłem tokenu można znaleźć w sekcji specjalne niestandardowe dane obejmują informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="81567-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="81567-104">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="81567-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81567-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="81567-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="81567-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81567-106">Return Value</span></span>  
 <span data-ttu-id="81567-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="81567-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81567-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81567-108">Requirements</span></span>  
 <span data-ttu-id="81567-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="81567-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81567-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81567-110">See also</span></span>
- [<span data-ttu-id="81567-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="81567-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
