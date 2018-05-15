---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ad2167ab26eaa8164233ab9566854417f78df29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="ed744-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed744-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="ed744-103">Pobiera długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ed744-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed744-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed744-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed744-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed744-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="ed744-106">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera znakami buforu, muszą zawierać długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ed744-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed744-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ed744-107">Return Value</span></span>  
 <span data-ttu-id="ed744-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ed744-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed744-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed744-109">Requirements</span></span>  
 <span data-ttu-id="ed744-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ed744-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed744-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed744-111">See Also</span></span>  
 [<span data-ttu-id="ed744-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed744-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
