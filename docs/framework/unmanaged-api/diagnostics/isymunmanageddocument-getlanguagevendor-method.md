---
title: ISymUnmanagedDocument::GetLanguageVendor — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b73c9d6fa802a90e59345eb477bccfe80cf2275e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704933"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="0895c-102">ISymUnmanagedDocument::GetLanguageVendor — Metoda</span><span class="sxs-lookup"><span data-stu-id="0895c-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="0895c-103">Pobiera dostawcę język tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0895c-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0895c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0895c-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0895c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0895c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0895c-106">[out] Wskaźnik do zmiennej, która odbiera dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="0895c-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0895c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0895c-107">Return Value</span></span>  
 <span data-ttu-id="0895c-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0895c-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0895c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0895c-109">See also</span></span>
- [<span data-ttu-id="0895c-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="0895c-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
