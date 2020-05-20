---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 82b46ea315009b65254735d44e355154b83b22e2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609498"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="d232b-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="d232b-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="d232b-103">Otwórz specjalną sekcję z danymi niestandardowymi, aby emitować informacje o mapowaniu między tokenami i źródłami do programu.</span><span class="sxs-lookup"><span data-stu-id="d232b-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="d232b-104">Otwarcie tej sekcji, gdy metoda jest już otwarta lub na odwrót, jest błędem.</span><span class="sxs-lookup"><span data-stu-id="d232b-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d232b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d232b-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d232b-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d232b-106">Return Value</span></span>  
 <span data-ttu-id="d232b-107">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d232b-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d232b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d232b-108">Requirements</span></span>  
 <span data-ttu-id="d232b-109">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d232b-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d232b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d232b-110">See also</span></span>

- [<span data-ttu-id="d232b-111">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d232b-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
