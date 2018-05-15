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
ms.openlocfilehash: 103444e0b4b17b6384473eac714fba025cee9a55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="6c39e-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c39e-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="6c39e-103">Pobiera liczbę informacji wyszukiwania symboli.</span><span class="sxs-lookup"><span data-stu-id="6c39e-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c39e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c39e-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c39e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c39e-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="6c39e-106">[] limit] wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać informacje dotyczące wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="6c39e-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c39e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c39e-107">Return Value</span></span>  
 <span data-ttu-id="6c39e-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6c39e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c39e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c39e-109">Requirements</span></span>  
 <span data-ttu-id="6c39e-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c39e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c39e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c39e-111">See Also</span></span>  
 [<span data-ttu-id="6c39e-112">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c39e-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
