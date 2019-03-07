---
title: ISymUnmanagedDocument::FindClosestLine — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 760a6feb8400e60b7e14bf244d66c9026031e5dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474240"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="dd5f8-102">ISymUnmanagedDocument::FindClosestLine — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd5f8-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="dd5f8-103">Zwraca najbliższego wiersz, który jest punktem sekwencji, rozpoczynając od podanej linię w tym dokumencie, który może być lub może nie być punktu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dd5f8-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd5f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd5f8-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd5f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd5f8-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="dd5f8-106">[in] Wiersz w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="dd5f8-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="dd5f8-107">[out] Wskaźnik do zmiennej, która odbiera wiersza.</span><span class="sxs-lookup"><span data-stu-id="dd5f8-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd5f8-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd5f8-108">Return Value</span></span>  
 <span data-ttu-id="dd5f8-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="dd5f8-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5f8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd5f8-110">See also</span></span>
- [<span data-ttu-id="dd5f8-111">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd5f8-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
