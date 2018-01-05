---
title: "ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb283198de5621748b37fe8e22f2fbc408754ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="c5684-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5684-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="c5684-103">Otwórz sekcję specjalne danych niestandardowych można wyemitować informacji mapowaniem token do źródła do.</span><span class="sxs-lookup"><span data-stu-id="c5684-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="c5684-104">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, jest to błąd.</span><span class="sxs-lookup"><span data-stu-id="c5684-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5684-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5684-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c5684-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c5684-106">Return Value</span></span>  
 <span data-ttu-id="c5684-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c5684-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5684-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5684-108">Requirements</span></span>  
 <span data-ttu-id="c5684-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c5684-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5684-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5684-110">See Also</span></span>  
 [<span data-ttu-id="c5684-111">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5684-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
