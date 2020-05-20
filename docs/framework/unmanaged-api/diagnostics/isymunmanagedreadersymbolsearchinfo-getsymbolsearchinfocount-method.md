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
ms.openlocfilehash: a81a5afeec8f97864e1772347c6575b9d09cb176
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614893"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="3de8e-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="3de8e-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="3de8e-103">Pobiera liczbę informacji o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="3de8e-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de8e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3de8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3de8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3de8e-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="3de8e-106">] out] wskaźnik do obiektu `ULONG32` , który odbiera rozmiar buforu wymaganego do przechowywania informacji o wyszukiwaniu.</span><span class="sxs-lookup"><span data-stu-id="3de8e-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3de8e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3de8e-107">Return Value</span></span>  
 <span data-ttu-id="3de8e-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3de8e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de8e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3de8e-109">Requirements</span></span>  
 <span data-ttu-id="3de8e-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3de8e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de8e-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3de8e-111">See also</span></span>

- [<span data-ttu-id="3de8e-112">ISymUnmanagedReaderSymbolSearchInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3de8e-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
