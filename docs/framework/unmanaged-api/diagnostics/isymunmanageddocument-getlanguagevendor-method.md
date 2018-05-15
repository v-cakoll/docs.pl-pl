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
ms.openlocfilehash: 0a6830f47d5cac2cf9c84144c18486489b0ec581
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="eff8f-102">ISymUnmanagedDocument::GetLanguageVendor — Metoda</span><span class="sxs-lookup"><span data-stu-id="eff8f-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="eff8f-103">Pobiera dostawcy języka tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eff8f-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eff8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eff8f-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eff8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eff8f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="eff8f-106">[out] Wskaźnik do zmiennej, która odbiera dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="eff8f-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eff8f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eff8f-107">Return Value</span></span>  
 <span data-ttu-id="eff8f-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="eff8f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff8f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eff8f-109">See Also</span></span>  
 [<span data-ttu-id="eff8f-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="eff8f-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
