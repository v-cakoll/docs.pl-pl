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
ms.openlocfilehash: 350aecb9f9c99c9aa44ae6df6d31c7cb69ae5760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430348"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="2a26f-102">ISymUnmanagedDocument::HasEmbeddedSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a26f-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="2a26f-103">Zwraca `true` Jeśli dokument ma źródła osadzone w symbole debugowania; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="2a26f-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a26f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a26f-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a26f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a26f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2a26f-106">[out] Wskaźnik do zmiennej, która wskazuje, czy dokument zawiera osadzony w symbole debugowania źródła.</span><span class="sxs-lookup"><span data-stu-id="2a26f-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a26f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2a26f-107">Return Value</span></span>  
 <span data-ttu-id="2a26f-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2a26f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a26f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a26f-109">See Also</span></span>  
 [<span data-ttu-id="2a26f-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a26f-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
