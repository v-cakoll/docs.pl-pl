---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc2ced988f7277c994eb9449e7c26efa5450b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968587"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="66098-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="66098-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="66098-103">Otwórz sekcji danych niestandardowych specjalny emitowanie informacji o mapowaniu zakresu źródłem tokenu do.</span><span class="sxs-lookup"><span data-stu-id="66098-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="66098-104">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="66098-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66098-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="66098-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="66098-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66098-106">Return Value</span></span>  
 <span data-ttu-id="66098-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="66098-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66098-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66098-108">Requirements</span></span>  
 <span data-ttu-id="66098-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66098-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66098-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66098-110">See also</span></span>

- [<span data-ttu-id="66098-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="66098-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
