---
title: ISymUnmanagedMethod::GetRanges — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6afe0f0d8780a93a7d98f24a11bb67ef65ebf63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604278"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="cba12-102">ISymUnmanagedMethod::GetRanges — Metoda</span><span class="sxs-lookup"><span data-stu-id="cba12-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="cba12-103">Danou pozici w dokumencie zwraca tablicę rozpoczęcia i zakończenia pary przesunięcia, które odnoszą się do zakresów języka Microsoft intermediate language (MSIL) uwzględniającą pozycja w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="cba12-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="cba12-104">Tablica jest tablicy liczb całkowitych i ma format [rozpoczęcia, zakończenia, uruchamianie i kończenie].</span><span class="sxs-lookup"><span data-stu-id="cba12-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="cba12-105">Liczba par zakres jest długość tablicy podzielonej przez 2.</span><span class="sxs-lookup"><span data-stu-id="cba12-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba12-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cba12-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cba12-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cba12-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="cba12-108">[in] Dokument, dla którego żądana jest przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="cba12-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="cba12-109">[in] Wiersz dokumentu odpowiadający zakresów.</span><span class="sxs-lookup"><span data-stu-id="cba12-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="cba12-110">[in] Kolumna dokumentu, odpowiadający zakresów.</span><span class="sxs-lookup"><span data-stu-id="cba12-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="cba12-111">[in] Rozmiar `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cba12-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="cba12-112">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zakresy.</span><span class="sxs-lookup"><span data-stu-id="cba12-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="cba12-113">[out] Wskaźnik do buforu, który otrzymuje zakresów.</span><span class="sxs-lookup"><span data-stu-id="cba12-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cba12-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cba12-114">Return Value</span></span>  
 <span data-ttu-id="cba12-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="cba12-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cba12-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cba12-116">Requirements</span></span>  
 <span data-ttu-id="cba12-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cba12-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba12-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cba12-118">See also</span></span>
- [<span data-ttu-id="cba12-119">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="cba12-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
