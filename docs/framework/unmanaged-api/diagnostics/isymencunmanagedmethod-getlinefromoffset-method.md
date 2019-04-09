---
title: ISymENCUnmanagedMethod::GetLineFromOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3106c6680750826306cffb31e599ee2260bf4ad7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136451"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="66788-102">ISymENCUnmanagedMethod::GetLineFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="66788-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="66788-103">Pobiera informacje o wiersz skojarzony z przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="66788-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="66788-104">Jeśli parametr offset (`dwOffset`) nie jest punktem sekwencji, ta metoda pobiera informacje o wiersz skojarzony z poprzednim przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="66788-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66788-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="66788-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66788-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="66788-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="66788-107">[in] Element `ULONG32` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="66788-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="66788-108">[out] Wskaźnik do `ULONG32` odbierająca wiersza.</span><span class="sxs-lookup"><span data-stu-id="66788-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="66788-109">[out] Wskaźnik do `ULONG32` kolumny, która otrzymuje.</span><span class="sxs-lookup"><span data-stu-id="66788-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="66788-110">[out] Wskaźnik do `ULONG32` odbierająca zakończyć wiersza.</span><span class="sxs-lookup"><span data-stu-id="66788-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="66788-111">[out] Wskaźnik do `ULONG32` końcowa kolumny, która otrzymuje.</span><span class="sxs-lookup"><span data-stu-id="66788-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="66788-112">[out] Wskaźnik do `ULONG32` odbierająca punktu sekwencji skojarzone.</span><span class="sxs-lookup"><span data-stu-id="66788-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66788-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66788-113">Return Value</span></span>  
 <span data-ttu-id="66788-114">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="66788-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66788-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66788-115">Requirements</span></span>  
 <span data-ttu-id="66788-116">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66788-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66788-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66788-117">See also</span></span>

- [<span data-ttu-id="66788-118">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="66788-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
