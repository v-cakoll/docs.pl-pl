---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: f5898cab08f332314fb33684399dcb4f2ff71cc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609459"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="c14c5-102">ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda</span><span class="sxs-lookup"><span data-stu-id="c14c5-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="c14c5-103">Mapuje podany token metadanych do podanego zakresu wierszy źródłowych w określonym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="c14c5-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="c14c5-104">Musi być wywoływana między wywołaniami [metody OpenMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans —](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="c14c5-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14c5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c14c5-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c14c5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c14c5-106">Parameters</span></span>  
  
|<span data-ttu-id="c14c5-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="c14c5-107">Parameter</span></span>|<span data-ttu-id="c14c5-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c14c5-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="c14c5-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c14c5-109">Return Value</span></span>  
 <span data-ttu-id="c14c5-110">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c14c5-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c14c5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c14c5-111">Requirements</span></span>  
 <span data-ttu-id="c14c5-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c14c5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14c5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c14c5-113">See also</span></span>

- [<span data-ttu-id="c14c5-114">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c14c5-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
