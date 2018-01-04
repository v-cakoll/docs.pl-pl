---
title: "ISymUnmanagedWriter::SetMethodSourceRange — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetMethodSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f82be130dba8087cf649d3e89bec8afc065e86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="90de3-102">ISymUnmanagedWriter::SetMethodSourceRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="90de3-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="90de3-103">Określa wartość true, początek i koniec metody w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="90de3-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="90de3-104">Użyj tej metody, aby określić zakres metody, niezależnie od punkty sekwencji, które istnieją w metodzie.</span><span class="sxs-lookup"><span data-stu-id="90de3-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90de3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="90de3-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90de3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="90de3-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="90de3-107">[in] Wskaźnik do dokumentu zawierającego pozycji początkowej.</span><span class="sxs-lookup"><span data-stu-id="90de3-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="90de3-108">[in] Numer wiersza początkowego.</span><span class="sxs-lookup"><span data-stu-id="90de3-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="90de3-109">[in] Kolumna początkowa.</span><span class="sxs-lookup"><span data-stu-id="90de3-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="90de3-110">[in] Wskaźnik do dokumentu zawierającego pozycję końcową.</span><span class="sxs-lookup"><span data-stu-id="90de3-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="90de3-111">[in] Numer wiersza końcowego.</span><span class="sxs-lookup"><span data-stu-id="90de3-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="90de3-112">[in] Numer kolumny końcowej.</span><span class="sxs-lookup"><span data-stu-id="90de3-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90de3-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="90de3-113">Return Value</span></span>  
 <span data-ttu-id="90de3-114">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="90de3-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90de3-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90de3-115">Requirements</span></span>  
 <span data-ttu-id="90de3-116">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="90de3-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90de3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90de3-117">See Also</span></span>  
 [<span data-ttu-id="90de3-118">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="90de3-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
