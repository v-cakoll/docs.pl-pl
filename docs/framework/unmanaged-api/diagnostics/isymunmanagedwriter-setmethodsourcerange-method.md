---
title: ISymUnmanagedWriter::SetMethodSourceRange — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46072718a7dafc0a00294757d5ccce6242a11e23
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468367"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="e8fb4-102">ISymUnmanagedWriter::SetMethodSourceRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8fb4-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="e8fb4-103">Określa wartość true, początek i koniec okresu metody w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="e8fb4-104">Ta metoda umożliwia określenie stopnia metody, niezależnie od punktów sekwencji, które istnieją w metodzie.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8fb4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8fb4-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8fb4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8fb4-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="e8fb4-107">[in] Wskaźnik do dokumentu zawierającego pozycja początkowa.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="e8fb4-108">[in] Numer wiersza początkowego.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="e8fb4-109">[in] Kolumna początkowa.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="e8fb4-110">[in] Wskaźnik do dokumentu zawierającego pozycji końcowej.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="e8fb4-111">[in] Końcowy numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="e8fb4-112">[in] Numer kolumny końcowej.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8fb4-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e8fb4-113">Return Value</span></span>  
 <span data-ttu-id="e8fb4-114">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="e8fb4-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8fb4-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8fb4-115">Requirements</span></span>  
 <span data-ttu-id="e8fb4-116">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e8fb4-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8fb4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8fb4-117">See also</span></span>
- [<span data-ttu-id="e8fb4-118">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8fb4-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
