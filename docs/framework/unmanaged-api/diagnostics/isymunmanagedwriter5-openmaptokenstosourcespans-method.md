---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60c1984e6193481efdaaeb82a2bc025aef67a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534447"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="950e1-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="950e1-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="950e1-103">Otwórz sekcji danych niestandardowych specjalny emitowanie informacji o mapowaniu zakresu źródłem tokenu do.</span><span class="sxs-lookup"><span data-stu-id="950e1-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="950e1-104">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="950e1-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="950e1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="950e1-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="950e1-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="950e1-106">Return Value</span></span>  
 <span data-ttu-id="950e1-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="950e1-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="950e1-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="950e1-108">Requirements</span></span>  
 <span data-ttu-id="950e1-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="950e1-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950e1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="950e1-110">See also</span></span>
- [<span data-ttu-id="950e1-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="950e1-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
