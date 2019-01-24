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
ms.openlocfilehash: 63b597c6d15310c78397b9aac7b618c52df743ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711924"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="9aad1-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="9aad1-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="9aad1-103">Pobiera liczbę informacji wyszukiwania symboli.</span><span class="sxs-lookup"><span data-stu-id="9aad1-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aad1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9aad1-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9aad1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9aad1-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="9aad1-106">] out] wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać informacje dotyczące wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="9aad1-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9aad1-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9aad1-107">Return Value</span></span>  
 <span data-ttu-id="9aad1-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="9aad1-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aad1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9aad1-109">Requirements</span></span>  
 <span data-ttu-id="9aad1-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9aad1-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aad1-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9aad1-111">See also</span></span>
- [<span data-ttu-id="9aad1-112">ISymUnmanagedReaderSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9aad1-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
