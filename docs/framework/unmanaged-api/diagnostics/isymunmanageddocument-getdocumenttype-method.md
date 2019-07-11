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
ms.openlocfilehash: ae3575b759d8b6191f0b5e5cd557a6f6e56323fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776741"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="a77aa-102">ISymUnmanagedDocument::GetDocumentType — Metoda</span><span class="sxs-lookup"><span data-stu-id="a77aa-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="a77aa-103">Pobiera typ dokumentu w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a77aa-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a77aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a77aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a77aa-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a77aa-106">[out] Wskaźnik do zmiennej, która otrzymuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a77aa-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a77aa-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a77aa-107">Return Value</span></span>  
 <span data-ttu-id="a77aa-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a77aa-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77aa-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a77aa-109">See also</span></span>

- [<span data-ttu-id="a77aa-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="a77aa-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
