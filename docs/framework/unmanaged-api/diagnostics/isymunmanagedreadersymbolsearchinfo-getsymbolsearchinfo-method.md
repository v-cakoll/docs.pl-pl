---
title: "ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77c573865ad9fba14259e9bb1538a15cb3067925
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="4d1dd-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d1dd-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="4d1dd-103">Pobiera informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="4d1dd-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d1dd-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d1dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d1dd-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="4d1dd-106">[in] A `ULONG32` wskazuje, że rozmiar `rgpSearchInfo`.</span><span class="sxs-lookup"><span data-stu-id="4d1dd-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="4d1dd-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać informacje dotyczące wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="4d1dd-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="4d1dd-108">[out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4d1dd-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d1dd-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d1dd-109">Return Value</span></span>  
 <span data-ttu-id="4d1dd-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4d1dd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d1dd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d1dd-111">Requirements</span></span>  
 <span data-ttu-id="4d1dd-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d1dd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1dd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d1dd-113">See Also</span></span>  
 [<span data-ttu-id="4d1dd-114">ISymUnmanagedReaderSymbolSearchInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="4d1dd-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
