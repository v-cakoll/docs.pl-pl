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
ms.openlocfilehash: 2b5a42c89e0e3efed61b1b471c227e0df85a51aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614906"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="fe15a-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe15a-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="fe15a-103">Pobiera informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="fe15a-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe15a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe15a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe15a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe15a-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="fe15a-106">podczas A `ULONG32` , który wskazuje rozmiar `rgpSearchInfo` .</span><span class="sxs-lookup"><span data-stu-id="fe15a-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="fe15a-107">określoną Wskaźnik do obiektu `ULONG32` , który odbiera rozmiar buforu, który musi zawierać informacje o wyszukiwaniu.</span><span class="sxs-lookup"><span data-stu-id="fe15a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="fe15a-108">określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fe15a-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe15a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fe15a-109">Return Value</span></span>  
 <span data-ttu-id="fe15a-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fe15a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe15a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe15a-111">Requirements</span></span>  
 <span data-ttu-id="fe15a-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fe15a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe15a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe15a-113">See also</span></span>

- [<span data-ttu-id="fe15a-114">ISymUnmanagedReaderSymbolSearchInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fe15a-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
