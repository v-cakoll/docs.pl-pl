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
ms.openlocfilehash: 319ba58b5d012cbc0f9ddac0b83e5f3ae2ae062a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446170"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="d3112-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3112-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="d3112-103">Pobiera długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d3112-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3112-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3112-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3112-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3112-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="d3112-106">określoną Wskaźnik do `ULONG32`, który odbiera rozmiar (w znakach) bufora wymaganego do przechowywania długości ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d3112-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3112-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3112-107">Return Value</span></span>  
 <span data-ttu-id="d3112-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d3112-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3112-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3112-109">Requirements</span></span>  
 <span data-ttu-id="d3112-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d3112-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3112-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3112-111">See also</span></span>

- [<span data-ttu-id="d3112-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3112-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
