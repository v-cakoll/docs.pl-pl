---
title: ISymUnmanagedDocument::GetSourceLength — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3341159600c85915cd3c1a138265dc386edbb766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="9991b-102">ISymUnmanagedDocument::GetSourceLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="9991b-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="9991b-103">Pobiera długość w bajtach osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="9991b-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9991b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9991b-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9991b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9991b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9991b-106">[out] Wskaźnik do zmiennej, która wskazuje długość w bajtach osadzone źródło.</span><span class="sxs-lookup"><span data-stu-id="9991b-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9991b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9991b-107">Return Value</span></span>  
 <span data-ttu-id="9991b-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9991b-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9991b-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9991b-109">See Also</span></span>  
 [<span data-ttu-id="9991b-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="9991b-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
