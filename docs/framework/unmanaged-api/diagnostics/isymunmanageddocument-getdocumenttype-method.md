---
title: ISymUnmanagedDocument::GetDocumentType — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 107039643e097ada1756054b2d14fcf0cbb71c00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493378"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="baa58-102">ISymUnmanagedDocument::GetDocumentType — Metoda</span><span class="sxs-lookup"><span data-stu-id="baa58-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="baa58-103">Pobiera typ dokumentu w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="baa58-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="baa58-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baa58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="baa58-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="baa58-106">[out] Wskaźnik do zmiennej, która otrzymuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="baa58-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baa58-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="baa58-107">Return Value</span></span>  
 <span data-ttu-id="baa58-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="baa58-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa58-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baa58-109">See also</span></span>
- [<span data-ttu-id="baa58-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="baa58-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
