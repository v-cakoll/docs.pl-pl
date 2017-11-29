---
title: "ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c896c8bc8aa852fb69f182e484243a0c379e0a1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="5d1b9-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d1b9-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="5d1b9-103">Pobiera ścieżkę wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5d1b9-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d1b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d1b9-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d1b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d1b9-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="5d1b9-106">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w znaki buforu, muszą zawierać ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5d1b9-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d1b9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5d1b9-107">Return Value</span></span>  
 <span data-ttu-id="5d1b9-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5d1b9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d1b9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d1b9-109">Requirements</span></span>  
 <span data-ttu-id="5d1b9-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5d1b9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1b9-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d1b9-111">See Also</span></span>  
 [<span data-ttu-id="5d1b9-112">ISymUnmanagedSymbolSearchInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="5d1b9-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
