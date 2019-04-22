---
title: ISymUnmanagedDocument::HasEmbeddedSource — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d6c79be95ff80c8de9b07cb33be46a5f5db22b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094271"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="57a6a-102">ISymUnmanagedDocument::HasEmbeddedSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="57a6a-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="57a6a-103">Zwraca `true` Jeśli dokument ma źródło osadzone w symbole debugowania; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="57a6a-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57a6a-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57a6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57a6a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="57a6a-106">[out] Wskaźnik do zmiennej, która wskazuje, czy dokument ma źródło osadzone w symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="57a6a-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57a6a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="57a6a-107">Return Value</span></span>  
 <span data-ttu-id="57a6a-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="57a6a-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a6a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57a6a-109">See also</span></span>

- [<span data-ttu-id="57a6a-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="57a6a-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
