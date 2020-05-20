---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: bdc630c3c94c7d03b736efa0a95665f10aac7c6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609433"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="0ab43-102">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ab43-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="0ab43-103">Interfejs ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="0ab43-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ab43-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="0ab43-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0ab43-105">Methods</span></span>  
 <span data-ttu-id="0ab43-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="0ab43-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="0ab43-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ab43-107">Method</span></span>|<span data-ttu-id="0ab43-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0ab43-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ab43-109">CloseMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="0ab43-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="0ab43-110">Zamknij sekcję specjalnych danych niestandardowych dla informacji dotyczących mapowania między tokenami i źródłami.</span><span class="sxs-lookup"><span data-stu-id="0ab43-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="0ab43-111">Po jego zamknięciu nie można dodać więcej informacji dotyczących mapowania.</span><span class="sxs-lookup"><span data-stu-id="0ab43-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="0ab43-112">MapTokenToSourceSpan, metoda</span><span class="sxs-lookup"><span data-stu-id="0ab43-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="0ab43-113">Mapuje podany token metadanych do podanego zakresu wierszy źródłowych w określonym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="0ab43-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="0ab43-114">Musi być wywoływana między wywołaniami [metody OpenMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans —](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ab43-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="0ab43-115">OpenMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="0ab43-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="0ab43-116">Otwórz specjalną sekcję z danymi niestandardowymi, aby emitować informacje o mapowaniu między tokenami i źródłami do programu.</span><span class="sxs-lookup"><span data-stu-id="0ab43-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="0ab43-117">Otwarcie tej sekcji, gdy metoda jest już otwarta lub na odwrót, jest błędem.</span><span class="sxs-lookup"><span data-stu-id="0ab43-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ab43-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ab43-118">Requirements</span></span>  
 <span data-ttu-id="0ab43-119">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0ab43-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab43-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ab43-120">See also</span></span>

- [<span data-ttu-id="0ab43-121">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="0ab43-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0ab43-122">ISymUnmanagedWriter4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ab43-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
