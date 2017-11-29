---
title: "ISymUnmanagedSymbolSearchInfo::GetSearchPathLength — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 58a788d8ef96a52c0b1bc361a97013f27c2809da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="1a7bf-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a7bf-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="1a7bf-103">Pobiera długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="1a7bf-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a7bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a7bf-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a7bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a7bf-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="1a7bf-106">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera znakami buforu, muszą zawierać długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="1a7bf-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a7bf-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a7bf-107">Return Value</span></span>  
 <span data-ttu-id="1a7bf-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1a7bf-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a7bf-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a7bf-109">Requirements</span></span>  
 <span data-ttu-id="1a7bf-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1a7bf-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a7bf-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a7bf-111">See Also</span></span>  
 [<span data-ttu-id="1a7bf-112">ISymUnmanagedSymbolSearchInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="1a7bf-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
