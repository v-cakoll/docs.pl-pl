---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 876804e7b825443116b1f44a02a685a73153915c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121625"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="bfbaa-102">ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda</span><span class="sxs-lookup"><span data-stu-id="bfbaa-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="bfbaa-103">Mapuje podany token metadanych do podanego zakresu wierszy źródłowych w określonym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="bfbaa-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="bfbaa-104">Musi być wywoływana między wywołaniami [metody OpenMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="bfbaa-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfbaa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfbaa-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfbaa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfbaa-106">Parameters</span></span>  
  
|<span data-ttu-id="bfbaa-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="bfbaa-107">Parameter</span></span>|<span data-ttu-id="bfbaa-108">Opis</span><span class="sxs-lookup"><span data-stu-id="bfbaa-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="bfbaa-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bfbaa-109">Return Value</span></span>  
 <span data-ttu-id="bfbaa-110">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="bfbaa-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfbaa-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfbaa-111">Requirements</span></span>  
 <span data-ttu-id="bfbaa-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bfbaa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfbaa-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfbaa-113">See also</span></span>

- [<span data-ttu-id="bfbaa-114">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfbaa-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
