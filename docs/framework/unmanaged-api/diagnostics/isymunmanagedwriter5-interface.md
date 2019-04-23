---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6ed8c6e61c558a4bc9e3f92d559615ac93ecff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144238"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="c7143-102">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7143-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="c7143-103">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7143-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7143-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7143-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="c7143-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c7143-105">Methods</span></span>  
 <span data-ttu-id="c7143-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="c7143-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="c7143-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7143-107">Method</span></span>|<span data-ttu-id="c7143-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c7143-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7143-109">CloseMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="c7143-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="c7143-110">Zamknij źródłem tokenu można znaleźć w sekcji specjalne niestandardowe dane obejmują informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="c7143-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="c7143-111">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="c7143-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="c7143-112">MapTokenToSourceSpan, metoda</span><span class="sxs-lookup"><span data-stu-id="c7143-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="c7143-113">Mapy token określonych metadanych do wiersza danego źródła zakres określony plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="c7143-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="c7143-114">Musi zostać wywołana między wywołaniami [OpenMapTokensToSourceSpans, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="c7143-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="c7143-115">OpenMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="c7143-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="c7143-116">Otwórz sekcji danych niestandardowych specjalny emitowanie informacji o mapowaniu zakresu źródłem tokenu do.</span><span class="sxs-lookup"><span data-stu-id="c7143-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="c7143-117">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="c7143-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7143-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7143-118">Requirements</span></span>  
 <span data-ttu-id="c7143-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c7143-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7143-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7143-120">See also</span></span>

- [<span data-ttu-id="c7143-121">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c7143-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c7143-122">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7143-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
