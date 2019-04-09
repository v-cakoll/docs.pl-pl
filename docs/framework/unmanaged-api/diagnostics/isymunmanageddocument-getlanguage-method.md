---
title: ISymUnmanagedDocument::GetLanguage — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ce47953358b7025e30080fbbaf288a6c0e879d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104601"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="65671-102">ISymUnmanagedDocument::GetLanguage — Metoda</span><span class="sxs-lookup"><span data-stu-id="65671-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="65671-103">Pobiera identyfikator języka w tym dokumencie</span><span class="sxs-lookup"><span data-stu-id="65671-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65671-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65671-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65671-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65671-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="65671-106">[out] Wskaźnik do zmiennej, która odbiera identyfikator języka.</span><span class="sxs-lookup"><span data-stu-id="65671-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65671-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65671-107">Return Value</span></span>  
 <span data-ttu-id="65671-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="65671-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65671-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65671-109">See also</span></span>

- [<span data-ttu-id="65671-110">ISymUnmanagedDocument — Interfejs</span><span class="sxs-lookup"><span data-stu-id="65671-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
