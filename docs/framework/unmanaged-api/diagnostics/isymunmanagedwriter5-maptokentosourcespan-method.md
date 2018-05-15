---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7751ed951c213c52c68125543622ed110124f5b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="4c17f-102">ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c17f-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="4c17f-103">Map zakres token metadanych do wiersza danego źródłowego określony plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="4c17f-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="4c17f-104">Musi zostać wywołana między wywołań [OpenMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="4c17f-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c17f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c17f-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c17f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c17f-106">Parameters</span></span>  
  
|<span data-ttu-id="4c17f-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="4c17f-107">Parameter</span></span>|<span data-ttu-id="4c17f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4c17f-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="4c17f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4c17f-109">Return Value</span></span>  
 <span data-ttu-id="4c17f-110">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4c17f-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c17f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c17f-111">Requirements</span></span>  
 <span data-ttu-id="4c17f-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4c17f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c17f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c17f-113">See Also</span></span>  
 [<span data-ttu-id="4c17f-114">ISymUnmanagedWriter5, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c17f-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
