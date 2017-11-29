---
title: "ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5f23c3fe39adcebcfdfadb9e9c2b639f16330d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="dfd4c-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfd4c-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="dfd4c-103">Zamknij sekcji specjalne dane niestandardowe dla tokenu do źródła obejmuje informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="dfd4c-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="dfd4c-104">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="dfd4c-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfd4c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfd4c-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dfd4c-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dfd4c-106">Return Value</span></span>  
 <span data-ttu-id="dfd4c-107">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="dfd4c-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfd4c-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfd4c-108">Requirements</span></span>  
 <span data-ttu-id="dfd4c-109">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dfd4c-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfd4c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfd4c-110">See Also</span></span>  
 [<span data-ttu-id="dfd4c-111">Isymunmanagedwriter5 — interfejs</span><span class="sxs-lookup"><span data-stu-id="dfd4c-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
