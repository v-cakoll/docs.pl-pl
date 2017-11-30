---
title: "ISymUnmanagedDocument::GetLanguage — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguage
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af0ffb422ec677997b6e2b6323b975ba4d69e5ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="97515-102">ISymUnmanagedDocument::GetLanguage — Metoda</span><span class="sxs-lookup"><span data-stu-id="97515-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="97515-103">Pobiera identyfikator języka tego dokumentu</span><span class="sxs-lookup"><span data-stu-id="97515-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97515-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97515-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97515-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97515-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="97515-106">[out] Wskaźnik do zmiennej, która odbiera identyfikator języka.</span><span class="sxs-lookup"><span data-stu-id="97515-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97515-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="97515-107">Return Value</span></span>  
 <span data-ttu-id="97515-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="97515-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97515-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97515-109">See Also</span></span>  
 [<span data-ttu-id="97515-110">ISymUnmanagedDocument — interfejs</span><span class="sxs-lookup"><span data-stu-id="97515-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
