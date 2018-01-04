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
ms.workload: dotnet
ms.openlocfilehash: 701b8de977d49a7d93f393b320bcb9d0d780c7bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="4ae25-102">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4ae25-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="4ae25-103">Isymunmanagedwriter5 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="4ae25-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ae25-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="4ae25-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4ae25-105">Methods</span></span>  
 <span data-ttu-id="4ae25-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="4ae25-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="4ae25-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="4ae25-107">Method</span></span>|<span data-ttu-id="4ae25-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4ae25-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ae25-109">CloseMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="4ae25-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="4ae25-110">Zamknij sekcji specjalne dane niestandardowe dla tokenu do źródła obejmuje informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="4ae25-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="4ae25-111">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="4ae25-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="4ae25-112">MapTokenToSourceSpan, metoda</span><span class="sxs-lookup"><span data-stu-id="4ae25-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="4ae25-113">Map zakres token metadanych do wiersza danego źródłowego określony plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="4ae25-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="4ae25-114">Musi zostać wywołana między wywołań [OpenMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="4ae25-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="4ae25-115">OpenMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="4ae25-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="4ae25-116">Otwórz sekcję specjalne danych niestandardowych można wyemitować informacji mapowaniem token do źródła do.</span><span class="sxs-lookup"><span data-stu-id="4ae25-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="4ae25-117">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, jest to błąd.</span><span class="sxs-lookup"><span data-stu-id="4ae25-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ae25-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ae25-118">Requirements</span></span>  
 <span data-ttu-id="4ae25-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4ae25-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae25-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ae25-120">See Also</span></span>  
 [<span data-ttu-id="4ae25-121">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="4ae25-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="4ae25-122">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ae25-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
