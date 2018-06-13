---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fd7c2bd4fae94d1ef5021b558a04b734803b68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430560"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="d2c27-102">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d2c27-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="d2c27-103">Isymunmanagedwriter5 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="d2c27-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c27-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2c27-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="d2c27-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d2c27-105">Methods</span></span>  
 <span data-ttu-id="d2c27-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="d2c27-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="d2c27-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="d2c27-107">Method</span></span>|<span data-ttu-id="d2c27-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d2c27-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2c27-109">CloseMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="d2c27-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="d2c27-110">Zamknij sekcji specjalne dane niestandardowe dla tokenu do źródła obejmuje informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="d2c27-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="d2c27-111">Po zamknięciu, można dodać nie więcej informacji o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="d2c27-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="d2c27-112">MapTokenToSourceSpan, metoda</span><span class="sxs-lookup"><span data-stu-id="d2c27-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="d2c27-113">Map zakres token metadanych do wiersza danego źródłowego określony plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="d2c27-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="d2c27-114">Musi zostać wywołana między wywołań [OpenMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="d2c27-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="d2c27-115">OpenMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="d2c27-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="d2c27-116">Otwórz sekcję specjalne danych niestandardowych można wyemitować informacji mapowaniem token do źródła do.</span><span class="sxs-lookup"><span data-stu-id="d2c27-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="d2c27-117">Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, jest to błąd.</span><span class="sxs-lookup"><span data-stu-id="d2c27-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2c27-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2c27-118">Requirements</span></span>  
 <span data-ttu-id="d2c27-119">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2c27-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c27-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2c27-120">See Also</span></span>  
 [<span data-ttu-id="d2c27-121">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="d2c27-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="d2c27-122">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2c27-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
