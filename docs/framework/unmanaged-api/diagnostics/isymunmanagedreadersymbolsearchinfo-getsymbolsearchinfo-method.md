---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86c28cdfe171b0b2bde1d28fa4c06ceaf7b26e18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667038"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="ddcc6-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddcc6-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="ddcc6-103">Pobiera informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="ddcc6-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcc6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddcc6-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddcc6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddcc6-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="ddcc6-106">[in] A `ULONG32` oznacza rozmiar `rgpSearchInfo`.</span><span class="sxs-lookup"><span data-stu-id="ddcc6-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="ddcc6-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać informacje dotyczące wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ddcc6-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="ddcc6-108">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagedsymbolsearchinfo —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ddcc6-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddcc6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ddcc6-109">Return Value</span></span>  
 <span data-ttu-id="ddcc6-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="ddcc6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcc6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddcc6-111">Requirements</span></span>  
 <span data-ttu-id="ddcc6-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ddcc6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcc6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddcc6-113">See also</span></span>
- [<span data-ttu-id="ddcc6-114">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddcc6-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
