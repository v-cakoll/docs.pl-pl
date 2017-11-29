---
title: "ISymUnmanagedWriter5 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="ff259-102">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ff259-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="ff259-103">Isymunmanagedwriter5 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="ff259-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff259-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff259-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="ff259-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ff259-105">Methods</span></span>  
 <span data-ttu-id="ff259-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="ff259-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="ff259-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="ff259-107">Method</span></span>|<span data-ttu-id="ff259-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ff259-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff259-109">CloseMapTokensToSourceSpans — metoda</span><span class="sxs-lookup"><span data-stu-id="ff259-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="ff259-110">Zamknij sekcji specjalne dane niestandardowe dla tokenu do źródła obejmuje informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="ff259-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="ff259-111">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="ff259-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="ff259-112">MapTokenToSourceSpan — metoda</span><span class="sxs-lookup"><span data-stu-id="ff259-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="ff259-113">Map zakres token metadanych do wiersza danego źródłowego określony plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="ff259-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="ff259-114">Musi zostać wywołana między wywołań [OpenMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="ff259-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="ff259-115">OpenMapTokensToSourceSpans — metoda</span><span class="sxs-lookup"><span data-stu-id="ff259-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="ff259-116">Otwórz sekcję specjalne danych niestandardowych można wyemitować informacji mapowaniem token do źródła do.</span><span class="sxs-lookup"><span data-stu-id="ff259-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="ff259-117">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, jest to błąd.</span><span class="sxs-lookup"><span data-stu-id="ff259-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff259-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff259-118">Requirements</span></span>  
 <span data-ttu-id="ff259-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ff259-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff259-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff259-120">See Also</span></span>  
 [<span data-ttu-id="ff259-121">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ff259-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="ff259-122">Isymunmanagedwriter4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ff259-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
