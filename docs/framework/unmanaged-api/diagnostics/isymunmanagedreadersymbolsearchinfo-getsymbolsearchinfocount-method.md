---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6764fe1472052e2657fd32078abe987b68cf9643
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465897"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="fb779-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb779-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="fb779-103">Pobiera liczbę informacji wyszukiwania symboli.</span><span class="sxs-lookup"><span data-stu-id="fb779-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb779-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb779-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb779-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb779-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="fb779-106">] out] wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać informacje dotyczące wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="fb779-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb779-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fb779-107">Return Value</span></span>  
 <span data-ttu-id="fb779-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="fb779-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb779-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb779-109">Requirements</span></span>  
 <span data-ttu-id="fb779-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fb779-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb779-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb779-111">See also</span></span>
- [<span data-ttu-id="fb779-112">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb779-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
