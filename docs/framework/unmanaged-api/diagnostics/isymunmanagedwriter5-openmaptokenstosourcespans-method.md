---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc2ced988f7277c994eb9449e7c26efa5450b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222682"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="76104-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="76104-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="76104-103">Otwórz sekcji danych niestandardowych specjalny emitowanie informacji o mapowaniu zakresu źródłem tokenu do.</span><span class="sxs-lookup"><span data-stu-id="76104-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="76104-104">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="76104-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76104-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="76104-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="76104-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="76104-106">Return Value</span></span>  
 <span data-ttu-id="76104-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="76104-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76104-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76104-108">Requirements</span></span>  
 <span data-ttu-id="76104-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="76104-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76104-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76104-110">See also</span></span>

- [<span data-ttu-id="76104-111">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76104-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
