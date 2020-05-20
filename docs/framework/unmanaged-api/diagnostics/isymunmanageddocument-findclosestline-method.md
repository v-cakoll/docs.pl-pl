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
ms.openlocfilehash: 9e6134d39096c4ab157aa545646d83339f92a0b8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441035"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="aafbd-102">ISymUnmanagedDocument::FindClosestLine — Metoda</span><span class="sxs-lookup"><span data-stu-id="aafbd-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="aafbd-103">Zwraca najbliższy wiersz będący punktem sekwencji, uwzględniając wiersz w tym dokumencie, który może lub nie jest punktem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="aafbd-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aafbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aafbd-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aafbd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aafbd-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="aafbd-106">podczas Wiersz w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="aafbd-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="aafbd-107">określoną Wskaźnik do zmiennej, która otrzymuje wiersz.</span><span class="sxs-lookup"><span data-stu-id="aafbd-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aafbd-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aafbd-108">Return Value</span></span>  
 <span data-ttu-id="aafbd-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="aafbd-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aafbd-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aafbd-110">See also</span></span>

- [<span data-ttu-id="aafbd-111">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="aafbd-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
