---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 18371b6aefb002f5adf27d43f85194c6c35f6ef5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121640"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="324b4-102">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="324b4-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="324b4-103">Interfejs ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="324b4-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="324b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="324b4-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="324b4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="324b4-105">Methods</span></span>  
 <span data-ttu-id="324b4-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="324b4-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="324b4-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="324b4-107">Method</span></span>|<span data-ttu-id="324b4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="324b4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="324b4-109">CloseMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="324b4-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="324b4-110">Zamknij sekcję specjalnych danych niestandardowych dla informacji dotyczących mapowania między tokenami i źródłami.</span><span class="sxs-lookup"><span data-stu-id="324b4-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="324b4-111">Po jego zamknięciu nie można dodać więcej informacji dotyczących mapowania.</span><span class="sxs-lookup"><span data-stu-id="324b4-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="324b4-112">MapTokenToSourceSpan, metoda</span><span class="sxs-lookup"><span data-stu-id="324b4-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="324b4-113">Mapuje podany token metadanych do podanego zakresu wierszy źródłowych w określonym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="324b4-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="324b4-114">Musi być wywoływana między wywołaniami [metody OpenMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="324b4-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="324b4-115">OpenMapTokensToSourceSpans, metoda</span><span class="sxs-lookup"><span data-stu-id="324b4-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="324b4-116">Otwórz specjalną sekcję z danymi niestandardowymi, aby emitować informacje o mapowaniu między tokenami i źródłami do programu.</span><span class="sxs-lookup"><span data-stu-id="324b4-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="324b4-117">Otwarcie tej sekcji, gdy metoda jest już otwarta lub na odwrót, jest błędem.</span><span class="sxs-lookup"><span data-stu-id="324b4-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="324b4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="324b4-118">Requirements</span></span>  
 <span data-ttu-id="324b4-119">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="324b4-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324b4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="324b4-120">See also</span></span>

- [<span data-ttu-id="324b4-121">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="324b4-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="324b4-122">ISymUnmanagedWriter4, interfejs</span><span class="sxs-lookup"><span data-stu-id="324b4-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
