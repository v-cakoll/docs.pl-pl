---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d3bc8b00b568f96cd55b7811f310d34c1ff700d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428651"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="2c488-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c488-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="2c488-103">Otwórz sekcję specjalne danych niestandardowych można wyemitować informacji mapowaniem token do źródła do.</span><span class="sxs-lookup"><span data-stu-id="2c488-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="2c488-104">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, jest to błąd.</span><span class="sxs-lookup"><span data-stu-id="2c488-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c488-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c488-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2c488-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2c488-106">Return Value</span></span>  
 <span data-ttu-id="2c488-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2c488-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c488-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c488-108">Requirements</span></span>  
 <span data-ttu-id="2c488-109">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2c488-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c488-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c488-110">See Also</span></span>  
 [<span data-ttu-id="2c488-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="2c488-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
