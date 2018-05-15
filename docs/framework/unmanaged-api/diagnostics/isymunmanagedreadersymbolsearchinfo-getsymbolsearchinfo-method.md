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
ms.openlocfilehash: 628d6fac45b046d9e8f26ad8777c38450da27a1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="c286d-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="c286d-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="c286d-103">Pobiera informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="c286d-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c286d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c286d-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c286d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c286d-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="c286d-106">[in] A `ULONG32` wskazuje, że rozmiar `rgpSearchInfo`.</span><span class="sxs-lookup"><span data-stu-id="c286d-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="c286d-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać informacje dotyczące wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c286d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="c286d-108">[out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c286d-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c286d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c286d-109">Return Value</span></span>  
 <span data-ttu-id="c286d-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c286d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c286d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c286d-111">Requirements</span></span>  
 <span data-ttu-id="c286d-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c286d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c286d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c286d-113">See Also</span></span>  
 [<span data-ttu-id="c286d-114">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c286d-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
