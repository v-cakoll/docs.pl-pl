---
title: "ISymUnmanagedDocument::FindClosestLine — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.FindClosestLine
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a4fff5ce5cdcde35c8483136cf4c3cd75854f6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="60e3f-102">ISymUnmanagedDocument::FindClosestLine — Metoda</span><span class="sxs-lookup"><span data-stu-id="60e3f-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="60e3f-103">Zwraca najbliższego wiersza, który jest punktem sekwencji danego wiersza w tym dokumencie, który może lub nie może być punktu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="60e3f-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60e3f-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60e3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60e3f-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="60e3f-106">[in] Wiersz w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="60e3f-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="60e3f-107">[out] Wskaźnik do zmiennej, która odbiera wiersza.</span><span class="sxs-lookup"><span data-stu-id="60e3f-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60e3f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="60e3f-108">Return Value</span></span>  
 <span data-ttu-id="60e3f-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="60e3f-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e3f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60e3f-110">See Also</span></span>  
 [<span data-ttu-id="60e3f-111">ISymUnmanagedDocument — interfejs</span><span class="sxs-lookup"><span data-stu-id="60e3f-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
