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
ms.openlocfilehash: acff919cbeb6b5d71197664139cdc9212961e314
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629517"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="c9a5b-102">ISymUnmanagedDocument::HasEmbeddedSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9a5b-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="c9a5b-103">Zwraca `true` Jeśli dokument ma źródło osadzone w symbole debugowania; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="c9a5b-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9a5b-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9a5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9a5b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c9a5b-106">[out] Wskaźnik do zmiennej, która wskazuje, czy dokument ma źródło osadzone w symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="c9a5b-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9a5b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c9a5b-107">Return Value</span></span>  
 <span data-ttu-id="c9a5b-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c9a5b-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a5b-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9a5b-109">See also</span></span>
- [<span data-ttu-id="c9a5b-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9a5b-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
