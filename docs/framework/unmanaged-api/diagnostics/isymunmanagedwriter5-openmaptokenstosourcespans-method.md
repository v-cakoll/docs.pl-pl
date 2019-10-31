---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 004e1ddae8a6c0262846422a2eeb4314a4c82f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121614"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="a6c3e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6c3e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="a6c3e-103">Otwórz specjalną sekcję z danymi niestandardowymi, aby emitować informacje o mapowaniu między tokenami i źródłami do programu.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="a6c3e-104">Otwarcie tej sekcji, gdy metoda jest już otwarta lub na odwrót, jest błędem.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c3e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6c3e-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a6c3e-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a6c3e-106">Return Value</span></span>  
 <span data-ttu-id="a6c3e-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6c3e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6c3e-108">Requirements</span></span>  
 <span data-ttu-id="a6c3e-109">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a6c3e-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c3e-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6c3e-110">See also</span></span>

- [<span data-ttu-id="a6c3e-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6c3e-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
