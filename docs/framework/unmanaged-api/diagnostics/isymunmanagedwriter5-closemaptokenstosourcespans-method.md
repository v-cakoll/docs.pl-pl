---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 053727604c795bf43a9b1658d5841fe85f53090a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614633"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="c0496-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0496-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="c0496-103">Zamknij sekcję specjalnych danych niestandardowych dla informacji dotyczących mapowania między tokenami i źródłami.</span><span class="sxs-lookup"><span data-stu-id="c0496-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="c0496-104">Po jego zamknięciu nie można dodać więcej informacji dotyczących mapowania.</span><span class="sxs-lookup"><span data-stu-id="c0496-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0496-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0496-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c0496-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c0496-106">Return Value</span></span>  
 <span data-ttu-id="c0496-107">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c0496-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0496-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0496-108">Requirements</span></span>  
 <span data-ttu-id="c0496-109">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c0496-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0496-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0496-110">See also</span></span>

- [<span data-ttu-id="c0496-111">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c0496-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
