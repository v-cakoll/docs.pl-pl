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
ms.openlocfilehash: 0e95255479792c7056bee7ee4f6c507e0f41eb6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449215"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="6c4fb-102">ISymUnmanagedDocument::FindClosestLine — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c4fb-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="6c4fb-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span><span class="sxs-lookup"><span data-stu-id="6c4fb-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c4fb-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c4fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c4fb-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="6c4fb-106">[in] A line in this document.</span><span class="sxs-lookup"><span data-stu-id="6c4fb-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6c4fb-107">[out] A pointer to a variable that receives the line.</span><span class="sxs-lookup"><span data-stu-id="6c4fb-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c4fb-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c4fb-108">Return Value</span></span>  
 <span data-ttu-id="6c4fb-109">S_OK if the method succeeds; otherwise, an error code.</span><span class="sxs-lookup"><span data-stu-id="6c4fb-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4fb-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c4fb-110">See also</span></span>

- [<span data-ttu-id="6c4fb-111">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c4fb-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
