---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 649f44bd7966b9ca89d2d040b7eede662404aa0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093556"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="f5da4-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5da4-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="f5da4-103">Pobiera ścieżkę wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f5da4-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5da4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5da4-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5da4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5da4-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="f5da4-106">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu wymagane w celu przechowywania ścieżek wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f5da4-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5da4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5da4-107">Return Value</span></span>  
 <span data-ttu-id="f5da4-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="f5da4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5da4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5da4-109">Requirements</span></span>  
 <span data-ttu-id="f5da4-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f5da4-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5da4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5da4-111">See also</span></span>

- [<span data-ttu-id="f5da4-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5da4-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
