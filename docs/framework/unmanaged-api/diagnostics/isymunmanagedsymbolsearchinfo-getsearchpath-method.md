---
title: "ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d1c4e1873aa3441e0348751717443e8189a67e61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="e6126-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda</span><span class="sxs-lookup"><span data-stu-id="e6126-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="e6126-103">Pobiera ścieżkę wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e6126-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6126-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6126-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6126-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6126-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="e6126-106">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w znaki buforu, muszą zawierać ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e6126-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6126-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e6126-107">Return Value</span></span>  
 <span data-ttu-id="e6126-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e6126-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6126-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6126-109">Requirements</span></span>  
 <span data-ttu-id="e6126-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e6126-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6126-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6126-111">See Also</span></span>  
 [<span data-ttu-id="e6126-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e6126-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
