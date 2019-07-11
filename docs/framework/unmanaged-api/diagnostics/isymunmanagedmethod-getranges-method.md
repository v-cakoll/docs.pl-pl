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
ms.openlocfilehash: ef5a98d510eee8942a2cad0525b6902e3e4eaa52
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769390"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="33a31-102">ISymUnmanagedMethod::GetRanges — Metoda</span><span class="sxs-lookup"><span data-stu-id="33a31-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="33a31-103">Danou pozici w dokumencie zwraca tablicę rozpoczęcia i zakończenia pary przesunięcia, które odnoszą się do zakresów języka Microsoft intermediate language (MSIL) uwzględniającą pozycja w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="33a31-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="33a31-104">Tablica jest tablicy liczb całkowitych i ma format [rozpoczęcia, zakończenia, uruchamianie i kończenie].</span><span class="sxs-lookup"><span data-stu-id="33a31-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="33a31-105">Liczba par zakres jest długość tablicy podzielonej przez 2.</span><span class="sxs-lookup"><span data-stu-id="33a31-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a31-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="33a31-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33a31-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="33a31-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="33a31-108">[in] Dokument, dla którego żądana jest przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="33a31-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="33a31-109">[in] Wiersz dokumentu odpowiadający zakresów.</span><span class="sxs-lookup"><span data-stu-id="33a31-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="33a31-110">[in] Kolumna dokumentu, odpowiadający zakresów.</span><span class="sxs-lookup"><span data-stu-id="33a31-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="33a31-111">[in] Rozmiar `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="33a31-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="33a31-112">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zakresy.</span><span class="sxs-lookup"><span data-stu-id="33a31-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="33a31-113">[out] Wskaźnik do buforu, który otrzymuje zakresów.</span><span class="sxs-lookup"><span data-stu-id="33a31-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33a31-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33a31-114">Return Value</span></span>  
 <span data-ttu-id="33a31-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="33a31-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a31-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33a31-116">Requirements</span></span>  
 <span data-ttu-id="33a31-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33a31-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a31-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33a31-118">See also</span></span>

- [<span data-ttu-id="33a31-119">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="33a31-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
