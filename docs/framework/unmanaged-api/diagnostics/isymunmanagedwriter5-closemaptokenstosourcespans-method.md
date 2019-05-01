---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3dea6b9710f1ee5ccf8c51261f59b2de026f5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962282"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="0a51c-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a51c-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="0a51c-103">Zamknij źródłem tokenu można znaleźć w sekcji specjalne niestandardowe dane obejmują informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="0a51c-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="0a51c-104">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="0a51c-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a51c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a51c-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0a51c-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0a51c-106">Return Value</span></span>  
 <span data-ttu-id="0a51c-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0a51c-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a51c-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a51c-108">Requirements</span></span>  
 <span data-ttu-id="0a51c-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0a51c-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a51c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a51c-110">See also</span></span>

- [<span data-ttu-id="0a51c-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a51c-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
