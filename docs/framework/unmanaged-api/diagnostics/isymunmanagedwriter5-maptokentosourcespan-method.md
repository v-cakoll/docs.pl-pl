---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 0f00dd34ffbdd58a46260132d8d7ace74ec2f294
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501680"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="2c6bc-102">ISymUnmanagedWriter5::MapTokenToSourceSpan — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c6bc-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="2c6bc-103">Mapuje podany token metadanych do podanego zakresu wierszy źródłowych w określonym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="2c6bc-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="2c6bc-104">Musi być wywoływana między wywołaniami [metody OpenMapTokensToSourceSpans —](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans —](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="2c6bc-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c6bc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c6bc-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c6bc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c6bc-106">Parameters</span></span>  
  
|<span data-ttu-id="2c6bc-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="2c6bc-107">Parameter</span></span>|<span data-ttu-id="2c6bc-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2c6bc-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="2c6bc-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2c6bc-109">Return Value</span></span>  
 <span data-ttu-id="2c6bc-110">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2c6bc-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c6bc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c6bc-111">Requirements</span></span>  
 <span data-ttu-id="2c6bc-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2c6bc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6bc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c6bc-113">See also</span></span>

- [<span data-ttu-id="2c6bc-114">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2c6bc-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
