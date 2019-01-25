---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88a9fa2f720db403c45d4254b17dfaf4689cd0f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706907"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="66f74-102">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="66f74-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="66f74-103">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="66f74-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66f74-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="66f74-105">Metody</span><span class="sxs-lookup"><span data-stu-id="66f74-105">Methods</span></span>  
 <span data-ttu-id="66f74-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="66f74-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="66f74-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="66f74-107">Method</span></span>|<span data-ttu-id="66f74-108">Opis</span><span class="sxs-lookup"><span data-stu-id="66f74-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66f74-109">CloseMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="66f74-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="66f74-110">Zamknij źródłem tokenu można znaleźć w sekcji specjalne niestandardowe dane obejmują informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="66f74-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="66f74-111">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="66f74-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="66f74-112">MapTokenToSourceSpan, metoda</span><span class="sxs-lookup"><span data-stu-id="66f74-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="66f74-113">Mapy token określonych metadanych do wiersza danego źródła zakres określony plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="66f74-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="66f74-114">Musi zostać wywołana między wywołaniami [OpenMapTokensToSourceSpans, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="66f74-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="66f74-115">OpenMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="66f74-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="66f74-116">Otwórz sekcji danych niestandardowych specjalny emitowanie informacji o mapowaniu zakresu źródłem tokenu do.</span><span class="sxs-lookup"><span data-stu-id="66f74-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="66f74-117">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="66f74-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66f74-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66f74-118">Requirements</span></span>  
 <span data-ttu-id="66f74-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66f74-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f74-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66f74-120">See also</span></span>
- [<span data-ttu-id="66f74-121">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="66f74-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="66f74-122">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="66f74-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
