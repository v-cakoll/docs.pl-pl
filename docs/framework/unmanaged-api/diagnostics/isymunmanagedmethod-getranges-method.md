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
ms.openlocfilehash: 1f1bd9c33f24847eae4ff7d26c5b996cd34afb72
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448929"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="a429a-102">ISymUnmanagedMethod::GetRanges — Metoda</span><span class="sxs-lookup"><span data-stu-id="a429a-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="a429a-103">Nadana pozycja w dokumencie zwraca tablicę par przesunięć początkowych i końcowych odpowiadających zakresom języka pośredniego firmy Microsoft (MSIL), który znajduje się w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="a429a-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="a429a-104">Tablica jest tablicą liczb całkowitych i ma format [początkowy, końcowy, początkowy, końcowy].</span><span class="sxs-lookup"><span data-stu-id="a429a-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="a429a-105">Liczba par zakresów jest długością tablicy podzieloną przez 2.</span><span class="sxs-lookup"><span data-stu-id="a429a-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a429a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a429a-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a429a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a429a-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a429a-108">podczas Dokument, dla którego zażądano przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="a429a-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="a429a-109">podczas Wiersz dokumentu odpowiadający zakresom.</span><span class="sxs-lookup"><span data-stu-id="a429a-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="a429a-110">podczas Kolumna dokumentu odpowiadająca zakresom.</span><span class="sxs-lookup"><span data-stu-id="a429a-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="a429a-111">podczas Rozmiar tablicy `ranges`.</span><span class="sxs-lookup"><span data-stu-id="a429a-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="a429a-112">określoną Wskaźnik do `ULONG32`, który odbiera rozmiar buforu wymaganego do zawierania zakresów.</span><span class="sxs-lookup"><span data-stu-id="a429a-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="a429a-113">określoną Wskaźnik do buforu, który odbiera zakresy.</span><span class="sxs-lookup"><span data-stu-id="a429a-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a429a-114">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="a429a-114">Return Value</span></span>  
 <span data-ttu-id="a429a-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a429a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a429a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a429a-116">Requirements</span></span>  
 <span data-ttu-id="a429a-117">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a429a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a429a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a429a-118">See also</span></span>

- [<span data-ttu-id="a429a-119">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="a429a-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
