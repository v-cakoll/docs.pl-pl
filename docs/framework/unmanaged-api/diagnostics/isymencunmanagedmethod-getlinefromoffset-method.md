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
ms.openlocfilehash: 29990ad6a94f063577236bdbc84d02d4d2b4b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426136"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="503e8-102">ISymENCUnmanagedMethod::GetLineFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="503e8-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="503e8-103">Pobiera informacje o wiersz skojarzony z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="503e8-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="503e8-104">Jeśli parametr offset (`dwOffset`) nie jest punktu sekwencji, ta metoda pobiera informacje o wiersz skojarzony z poprzednich przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="503e8-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503e8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="503e8-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="503e8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="503e8-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="503e8-107">[in] A `ULONG32` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="503e8-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="503e8-108">[out] Wskaźnik do `ULONG32` odbierająca wiersza.</span><span class="sxs-lookup"><span data-stu-id="503e8-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="503e8-109">[out] Wskaźnik do `ULONG32` odbierająca kolumny.</span><span class="sxs-lookup"><span data-stu-id="503e8-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="503e8-110">[out] Wskaźnik do `ULONG32` odbierająca zakończyć wiersza.</span><span class="sxs-lookup"><span data-stu-id="503e8-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="503e8-111">[out] Wskaźnik do `ULONG32` odbierająca końcowa kolumny.</span><span class="sxs-lookup"><span data-stu-id="503e8-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="503e8-112">[out] Wskaźnik do `ULONG32` odbierająca punktu skojarzone sekwencji.</span><span class="sxs-lookup"><span data-stu-id="503e8-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="503e8-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="503e8-113">Return Value</span></span>  
 <span data-ttu-id="503e8-114">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="503e8-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="503e8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="503e8-115">Requirements</span></span>  
 <span data-ttu-id="503e8-116">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="503e8-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503e8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="503e8-117">See Also</span></span>  
 [<span data-ttu-id="503e8-118">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="503e8-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
