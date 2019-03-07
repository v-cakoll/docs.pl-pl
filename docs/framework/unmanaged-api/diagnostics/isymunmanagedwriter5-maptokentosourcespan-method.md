---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf061de3e75550e33ba67c1d624279b1673c5382
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465339"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="c4655-102">ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda</span><span class="sxs-lookup"><span data-stu-id="c4655-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="c4655-103">Mapy token określonych metadanych do wiersza danego źródła zakres określony plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="c4655-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="c4655-104">Musi zostać wywołana między wywołaniami [OpenMapTokensToSourceSpans, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="c4655-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4655-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4655-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4655-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4655-106">Parameters</span></span>  
  
|<span data-ttu-id="c4655-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="c4655-107">Parameter</span></span>|<span data-ttu-id="c4655-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c4655-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="c4655-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c4655-109">Return Value</span></span>  
 <span data-ttu-id="c4655-110">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c4655-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4655-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4655-111">Requirements</span></span>  
 <span data-ttu-id="c4655-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c4655-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4655-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4655-113">See also</span></span>
- [<span data-ttu-id="c4655-114">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4655-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
